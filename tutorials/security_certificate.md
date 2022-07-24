############################

############################
# SECURITY CERTIFICATE
############################

############################

# SSL sertifikaları ile web sayfaları ilişkisi

- ## sertifika (or certificate)
public key + ilgili kurum bilgileri

- ## SSL (secure socket layer)
soket üzerinden sertifika ile şifreleyerek data alışverişi yapan sanal katmandır.

tarayıcı üzerinden bir internet sitesine gittiğimiz zaman, public key'i site bize gönderir. artık yaptığımız her işlem (Ajax işlemi) bu public key ile şifrelenerek gönderilir. artık bu bilgileri sadece private anahtara sahip internet sitesi açabilecektir.

- ## CA (or Certification Authority or sertifika otoritesi)
Sertifika vermeye yetkisi olan kurum. bu kurumun kendi sertifikasına "root" (kök) sertifikası denir. Pazarı yüksek olan bazı firmalar: IdenTrust, Sectigo, DigiCert, GoDaddy, Globalsign, Verisign. 

internet siteleri SSL sertifikalarını aracı kurumlara onaylatırlar. süreç bu şekildedir:
- web sunucu kendi public key (__SITE_PUB__) + private key'ini (__SITE_PRV__) lokalde oluşturur.
- public key'i CA'ya yollar.
- CA kendi private key'i (__CA_PRV__) ile __SITE_PUB__'nin hash'ini şifreleyip yeni anahtar oluşturur (__X__).
- CA, __X__'i web sunucusu yetkililerine yollar.

Kullanıcı bir web sitesini ziyaret ettiğinde;
- web tarayıcısında CA'in public key'leri (__CA_PUB__) zaten yüklü olmalıdır.
- browser web sunucusundan ziyaret ettiği sitenin public key'ini (__X__) indirir.
- browser __CA_PUB__ ile __X__'i açar. __X__ kendi içinde domain ve IP bilgisi tutmaktadır. bu sebeple tarayıcı gittiği sitenin doğru olup olmadığını anlar.
- browser o anda simetrik şifreleme için bir anahtar yaratır (__S__). __S__ i tarayıcı sunucuya public key (__SITE_PUB__) ile şifreleyip yollar.
- Artık browser sunucuya bir istek yolladığında sadece __S__ şifrelenecektir. yani artık public/private key'lere ihtiyaç yoktur. 

Web tarayıcıları __S__ değerini son kullanıcıya dahi vermiyor. Handhsake sırasında yaratılan ve simetrik haberleşmede kullanılacak olan __S__ public key (__SITE_PUB__) ile şifrelendiğinden ve sadece sunucu tarafından açıldığı için, bir hacker tüm akışı baştan sona takip edebilse bile, hiçbir şey yapamayacaktır.

__S__, değeri olmadan public key üzerinden de haberleşebilir. fakat bu şekilde "kusursuz ileri güvenlik" sağlanmış oluyor (bu konu başka başlıkta anlatılıyor).

TLS 1.2 için yukarıdaki adımları daha detaylı inceleyecek olursak:

  - client "__client hello__" (tam olarak bu string kullanılıyor) tipindeki mesajı ile handshake isteği yollar. bu mesajda:
    - client'ın kabul ettiği cipher'lerin listesi de mevcuttur.
    - session ID: önceden varsa bu değer doludur. eğer bu değeri sunucuda onaylarsa tekrar handshake yapılmasına gerek kalmaz.
    - tls version
    - random bytes
    - extensions: extra değerler burada yollanır. örneğin opsiyonel kullanılan "session ticket" özelliği bilgileri burada yollanır.

  - server ise response olarak "__server hello__" tipinde mesaj döner.

  - buradan sonra server sertifikasını yollar ve client sunucu sertifikasını kendi içinde valide eder.

  - daha sonra "__Key Exchange__" adımına gelinir. burada kullanılabilecek bazı yöntemler şunlardır:
    - TLS_RSA
    - Diffie-Hellman (TLS_DH)
    - ephemeral Diffie-Hellman (TLS_DHE) (Ephemeral kelime anlamı: fani, kısa ömürlü)
    - Elliptic Curve Diffie-Hellman (TLS_ECDH)
    - ephemeral Elliptic Curve Diffie-Hellman (TLS_ECDHE)
    - anonymous Diffie-Hellman (TLS_DH_anon)

    Not: Diffie-Hellman algoritması başka başlıkta anlatılmaktadır.

    Bu adımda __S__ anahtarı oluşturulur. Nasıl oluşturulacağı burada belirtilen algoritmaya bağlıdır.

    Bu akışta kullanılan bazı terimler:

    - ## pre master key
        web tarayıcısının kendi içinde oluşturduğu random key (__BS__)

    - ## master secret
        Web tarayıcısı handshake sırasında bir random bilgi, sunucuda dönüşünde bir random key yollar. bu 2 data ve __BS__ kullanılarak "master secret" (__S__) oluşturulur.

  - daha sonra "Server Hello Done" mesajı sunucudan client'a iletilir.

HTTPS ile haberleşildiğinde tüm HTTP mesajı şifrelenir. header yada farklı bir bilgi açık bırakılmaz. URL path'leri ve query variable'ları dahi şifrelenir. fakat neredeyse tüm web servisleri şifrelenmesi gereken bilgiler olduğunda hiçbir zaman GET isteği ile query parametrelerinde o bilgiler yollanmaz. onun yerine POST payload'ında yollanır. aslında ikiside aynı kapıya çıkar. fakat GET isteği ile atılan istekler, hem web tarayıcısının history'sinde, hemde server tarafının access log'larında görülür. bu sebeple post tercih edilir.

web sitenin anlaştığı sertifika firmasının web tarayıcılarla anlaşmış olması gerekmektedir. aksi durumda sertifika kırmızı uyarı verir. kırmızı uyarı sertifika var, fakat CA'lara tanıtılmamış anlamına gelir.

Bazı çakışmalar/uyuşmazlıklar:
- farklı web tarayıcıları farklı sertifika sağlayıcılarla anlaşabilir.
- aynı web tarayıcısı mobil versiyonu ile masaüstü versiyonunda aynı sertifika firmalarının bilgilerini bulundurmayabilir.
- aynı tarayıcı farklı versiyonlarında farklı sertifika sağlayıcılarının bilgilerini bulundurabilir. 
- aynı tarayıcı farklı versiyonlarda aynı CA'leri bulundurur fakat farklı sertifikalarını  (farklı sürümlerini) bulundurabilir

bu tarz durumlar yaşamamak için her zaman globalsign, Verisign gibi gibi çok tercih edilen firmalardan sertifika almakta fayda vardır.

sertifika çeşitlerine göre; web tarayıcısında logo, firma ismi vs gösterilme durumları vardır.

- ## Session ID
web sunucuna ilk istek atılacağı zaman client varsa eski Session ID'lerden devam edebilir. eğer önceden açılmış bir Session ID yoksa bu bilgi null gönderilir. session ID var oldukça handshake'e gerek kalmaz.

- ## SessionTicket
session ID'den farklı bir özelliktir. TLS extension olarak kullanılır. yani ekstra bir özelliktir. RFC buradadır: (source-id: 447)

- ## self sign key

public ve private key herhangi bir tool ile anında oluşturulabilir. bu anahtarlarda siteye gömülüp kullanılabilir. fakat web tarayıcısı kırmızı uyarı verecektir.

self sign aracılığı ile yapılan bağlantıların dışarıdan çözümlenme gibi bir durum söz konusu olamaz. aynı durum CA'e onaylatılan sertifikalar içinde geçerlidir.

self sign imza kullanırken şifre anahtarlarının boyutu arttırılarak güvenlik seviyesi çok rahat şekilde arttırılabilir. fakat dosya paylaşımı gibi uzun data işlemi gerektiren işlemlerde, anahtar boyutu sebebi ile şifreleme ve açma işlemleri CPU'ya yük bindirebilir.

- ## Intermediate CA
CA'lere 3üncü parti kuruluşlarda aracılık yapabilir. bu sebeple web tarayıcılarımızın "certificates" sekmelerinde içiçe sertifikalar görürüz.

- ## End Entity Certificate
son kullanıcıya ziyaret ettiği site aracılığı ile yollanan public key'dir.

- ## Certificate Signing Request (or CSR)
CA'ya müşterisinin (yani web sunucusunun sahibinin) yaptığı sertifika imzalatma isteğidir.

- ## Subject Alternative Name
Firefox sayfa ayarlarında web sitenin sertifika özelliklerini incelendiğimizde bu alanı görürüz. bazı sertifikalar birden fazla domain için kullanılabiliyor. bu gibi durumlarda izin verilen domain listesi bu değerin içerisinde yazmaktadır.

- ## "servers" tab on Firefox certificate manager
self-sign imzalı bir web sitesine Firefox üzerinden gittiğimizde Firefox exception fırlatır. eğer son kullanıcı add exception'a tıklarsa o sertifika bu listeye eklenir. 

- ## wildcard certificate
wildcard Türkçe kelime anlamı: joker

her subdomain (a.Google.com, b.Google.com gibi) için ayrı sertifika alınması gerekir. fakat wildcard sertifikalar tüm subdomain'leri desteklemektedir.
