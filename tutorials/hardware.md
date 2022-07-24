
############################

############################
# HARDWARE
############################

############################

# ARM (or old-name:Advanced RISC Machine or Acorn RISC Machine)
cep telefonları ve bazı oyun konsollarında kullanılan CPU tasarımıdır. CPU tasarımıdır; çünkü ARM firması, kendi başına işlemci üretmez, dizayn ve lisansı satar. CPU mimarisi özelleştirilebilir olduğundan her üretici farklı CPU performansları sergiler.

ARM'nin birçok sürümü vardır: ARMv1, ARMv2, ARMv2a...

Bu sürümler "aile" olarak gruplanmışlardır ve aile sürümü ile mimari sürüm numaraları farklı gider. örnek: ARM8 ailesinin içinde, ARMv4 vardır.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# sensor (or sensör or algılayıcı or detector)

# Accelerometer sensor (or ivmeölçer sensör) vs Jiroskop (or Gyroscope)
İvmeölçer yönden bağımsız cihazın ivmesini ölçer, jiroskop ise telefonun hangi yöne doğru yatırılmış olduğunun bilgisi verir. jiroskop 360 derecede telefonun hangi pozisyonda olduğunu belirler ve bu pozisyonda saniyede kaç derece yön değiştirdiğini belirler. bu iki sensör çoğu telefonda bulunmaktadır bu sebeple halk arasında bu ikisinin görevi birbiri ile çok karıştırılır. 

ivmeölçer m/s2 olarak dönüş yaparken, jiroskop rad/s (radian per second) olarak dönüş yapar. 

pi radyan = 180 derecedir.

# yakınlık sensörü (or proximity sensor)
ekrana bir cisim yaklaşıp yaklaşmadığı bilgisini döner. örneğin; telefonla konuşurken ekrana kulak değmesin diye ekranı otomatik kapatmak için kullanılır.

# tr:manyetometre (or tr:magnometre or eng:magnetometer)
Manyetik alanın yoğunluğunu ve yönünü ölçmeye yarayan sensördür.

ölçüm birimleri Gauss ve Tesla'dır.

Bu sensör, manyetik alanları ölçerek hangi yönün kuzey olduğunu söyleyebiliyor. harita servisleri için çok kullanılıyorlar. Pusula (or Compass) amacı ile kullanılıyor. Burada ufak bir ince nokta var: magnetometer ne kadar kusursuz donanımdan yapılmaya özen gösterilse bile, her zaman tam olarak geometrik olarak kutup yönünü göstermemektedir:

1- çünkü dünyanın manyetik kutup noktası ile dünyanın geometrik (dünya dönüşü üzerinden hesaplanan kutup noktası, diğer bir değiş ile; tepe noktası) tam olarak aynı noktayı göstermemektedir. ve bu değer zaman içinde değişiklik göstermektedir. çok ince hesaplamalarda bunu dikkate almak gerekir.

2- bu cihaz etraftaki her manyetik alan yaratan kimyasallardan etkilenir.

# ışık sensörü (or photodetector or tr:fotosel or photosensors)
ortamdaki olan ışık seviyesini belirler.

örnek kullanım:
- oto parlaklık ayarı seçilmişse, güneşin durumuna göre ekran parlaklığı oto arttırır/azaltır.
- kamera uygulaması flash ayarını otomatik ayarlar

# Barometer (or barometre)
ortamdaki/Atmosferdeki hava basıncını ölçen sensördür. dağcılar yüksekliği bulmak için ortam basıncını ölçmektedirler.

# Kalp Ritim Ölçer (or Heart Rate)
sadece parmak ucu ile temas ettirildiğinde kalp atış hızını hesaplayabilmektedir.

# gravity (or yerçekimi)
x, y, ve z için ayrı ayrı bu data sunulabilmektedir. örneği telefon dik tutulduğunda sadece Y yönünde bir çekim olduğu belirlenebilmektedir.

dönüş birimi: m/s2

# step counter
adım sayarlar genelde telefonun ayrı bir özel API'si ile sağlanmaktadır. çünkü adım saymak basit bir geliştirici için zordur. onun yerine işletim sistemi diğer sensörleri kullanarak basamak sayısını öngörmeye çalışır ve bunu ayrı bir API aracılığı ile sunar.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# Internet Protocol television (or IPTV)
streaming bazlı internet altyapısı ile kullanılan TV izleme teknolojilerinin genel ismidir. uydu, kablolu internet gibi farklı teknolojiler altyapıda olabilir.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# ROM
Bir kere bile program yazılmıyor içine. program hard-code çipin içindeki donanımda oluyor.

# Programmable rom (or PROM)
bir kere program yazılır daha sonra tekrar içi silinemediğinden pek kullanılması tercih edilmiyor.

# EPROM (or Erasable and Programmable Read Only Memory or Programlanabilir salt okunur bellek)
"salt" terimi birçok farklı anlama geliyor. "yalnız" anlamına da gelmektedir.

ultraviyole ışınlarla içi silinebilir.

# EEPROM (or E2PROM or Electrically Erasable and Programmable Read Only Memory)
Elektrik ile içi silinebilir. Ultraviyole ışık yerine elektrik kullanması çok büyük kolaylık sağlıyor.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# satellite (or tr:uydu)

## uplink (or U/L or UL) vs downlink
uplink uyduya client tarafından atılan sinyallerdir. downlink ise sunucudan client'a atılan sinyallerdir.

## Uydu interneti
- Dünya yörüngesinde birçok uydu var. bu uyduların bazıları birden fazla görev üstlenirken bazıları sadece 1 görev yapmaktadırlar.

- internet kullanımı için bazı uydular vardır. bu uydular ile internet servis sağlayıcılar tarafından yörüngeye yollanırlar.

- bazı uydular sadece bilgi dağıtırlar bazıları ise hem alıp hem cevap verebilirler.

- eğer tek yönlü çalışan bir uydu ile internet sağlanacak ise; süreç şu şekilde ilerlemektedir:

  - PC'ye bağlı bir modem ile kablo servis sağlayıcısına yönlendirilmiş olmalıdır.

  - PC indirmek istediği dosyanın isteğini kablo üzerinden servis sağlayıcısına yapar.

  - servis sağlayıcı cevabı uydu üzerinden tüm dünyaya yollar.

  - PC cevabı alırken başka insanlarda bu aldığı cevabı okuyabilecektir. tek yönlü uydu internetleri genelde büyük dosya indirirken avantaj sağlamaktadır. 

- çift yönlü uydularda servis sağlayıcısına kablo ile bağlanmak zorunda değiliz.

uydu yörüngesini tespit maliyetli olduğundan, uydu interneti de maliyetli. Bu sebeple araba gibi cihazları internete bağlarken, araba firmaları, mobil telefon hatları firmaları ile anlaşıp, arabaya mobil hat gömmektedir. Bu şekilde 3g/4g gibi teknolojilerle standart internet kullanılmaktadır. kaynak: (source-id: 363)

# amaçlarına göre uydular

- askeri güvenlik

- haritalama hizmetleri

  Uygular ortalama 30 santime'e kadar dünyadan görüntü alabilirler (2020 yılı). kaynak: (source-id: 364) video title: "Webinar-3 - Uydu Teknolojileri: Dün, Bugün ve Yarın...", "Bilişim Teknolojileri Derneği", at 35:00.

- Navigasyon hizmetleri (konumlama uygulamaları)

  Aynı amaç için hizmet eden birçok uygu sadece kendi alıcılarına uygun veri alıp verebilir. Bu sebeple birçok farklı sistem vardır:

  - GPS (or Global Positioning System) (ADB)
  - GLONASS (Rusya)
  - Beidou (Çin)
  - Galileo (Avrupa Birliği)

  kaynak: (source-id: 364) video title: "Webinar-3 - Uydu Teknolojileri: Dün, Bugün ve Yarın...", "Bilişim Teknolojileri Derneği", at 39:00.

  GPS sisteminde uydular sürekli olarak kendi konumunu içeren sinyalleri dünyaya yayarlar. Bu sinyalleri alan mobil client'lar kendi yerlerini kendi cihazlarında hesaplarlar. Ne kadar çok uydudan bilgi alınırsa o kadar net pozisyon elde edilir. 3 boyutlu pozisyon (yerden yükseklik, enlem, boylam bilgileri) için birden fazla uydudan bilgi almak şart.

- hava durumu tahmini

- bilimsel ar-ge (örnek: Uluslararası Uzay İstasyonu (or International Space Station or ISS))

- internet

- tv yayını

- telefon (uydu telefonları için büyük antenli cep telefonu ve uydu alıcısı olan bir telefon şarttır. ve cep telefonunun uyduyu görebilecek bir alanda olması şarttır.)

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# Retina Display
retina kelimesi kamera için gerekli algılayıcıya verilen isimdir. bu isim insan gözündeki biyolojik retinadan gelmektedir. "Retina Display" ise Apple'ın patentini aldığı özel bir isimdir. Retina Display yüksek piksel yoğunluğuna sahip ekranlar için kullanılan bir markadır.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# Harita hizmetlerinde trafik bilgisi kaynağı
Google Maps, Yandex Maps gibi hizmetlerin trafik bilgileri anlık olarak güncelleniyor. Bunlar anlaşmalı lojistik firmalarının araçları (örneğin kargo firması), akıllı telefon kullanan ve GPS istatistiği paylaşan kullanıcıların bilgilerinin ortalamaları alınarak trafik bilgisi edinilmektedir.

Trafik bilgisi hesaplamaları birçok karmaşık algoritmalar içeriyor. Örneğin; harita kaynaklarında caddenin akışı (yönü) bellidir. Bu yöne ters giden kullanıcıların konum bilgileri hesaplamadan çıkarılmaktadır. Tamamen duran (beklemede) olan kullanıcıların konum bilgileri devre dışı bırakılmaktadır gibi... Sadece tekil kullanıcı göz önünde bulundurulmayıp, aynı çevrede (örneğin 5 metrekarelik alanda) olan kullanıcıların tümü birlikte göz önünde bulundurulmaktadır. Örneğin; herkes hızlı hareket ediyor, sadece 1 araç yavaş ise o araç hesaplama dışı bırakılmaktadır.

Caddelerde geçen araçları algılayan sensörler ile trafik ölçümü yapılabilmektedir. Fakat bu sensörlerin maliyeti (bakımı gibi) çok yüksektir.

Benzer şekilde caddelerde bulunana kameralardan görüntü işleme ile trafiği ölçmekte çok maliyetlidir.

# GPS'in her zaman konumu tespit edememesi
GPS normalde uydulardan yararlanarak konumunu tespit etmektedir (başka başlıkta nasıl olduğu anlatılıyor). Fakat __A-GPS (or Assisted GPS or Augmented GPS or aGPS)__ teknolojisi ile baz istasyonlarından da konum tespit edilebilmektedir. Bu teknoloji mobil internet verisi (3g, 4g gibi) üzerinden bilgi alışverişi yapmaktadır. Bu sebeple A-GPS açıkken internet verisinin de açık olması gerekmektedir. A-GPS, GPS gibi uyduyu kendi bulabilir, fakat bazen GPS'in uydudan tam olarak konumunu tespit etmesi 5 dakikayı dahi geçebilir. Oysa A-GPS uydu bilgilerini direk olarak baz istasyonlarından almaktadır. Baz istasyonları bizim cep telefonlarımızdan güçlü olduğu için anında konum tespiti yapabiliyoruz.

# geolocation nasıl konum tespit ediyor

HTML 5 ile gelen bu özellik tarayıcılarda bir API sunuyor fakat tarayıcının nasıl konumu tespit edeceği standartlar arasında değildir.

Google sokak resimlerini çekmek için sokak sokak araçlarla dolaşıyor, bunun gibi bir çok işlem için sokak sokak dolaşan araçlar mevcut. bu araçlar etrafta algıladıkları WIFI-isimlerini kaydediyor. bu isimler database'de, konum ve WIFI sinyal gücü (o andaki WIFI uzaklık bilgisi) bazlı toplanıyor.

web tarayıcımızda konum tespiti yapmak istediğimiz anda, tarayıcı etraftaki WIFI isimlerini sinyal güçlerine göre topluyor (admin yetkisine gerek duymadan çoğu işletim sistemi bu bilgiyi sağlıyor). bu bilgiyi "Google Location Services" isimli web servisine gönderiyor ve eğer database'de kayıtlı ise konum bilgisini alıyor.

Google Location Services gibi birçok alternatif var (örnek: Mozilla Location Services), fakat en büyük veritabanı şimdilik (yıl 2018) Google'da.

mobil tarayıcılarda "Google Location Services" hizmetine ek olarak, tarayıcı, GPS üzerinden de konum tespiti yapmaya çalışıyor.

"Google Location Services" database'i sadece sokak sokak gezerek bilgi toplamıyor. bir kullanıcı, hem WIFI hem GPS üzerinden konumunu tespit etmişse; aynı WIFI'ye bağlı veya aynı çıkış IP'sine sahip olan her cihazı aynı lokasyonda olarak tanımlıyor. yani bir internet kafede yada şirket içerisinde bir kere lokasyon tanımlatmış biri, 1 hafta boyunca tüm herkese lokasyonun sağlanması için yeterli olabilir.

Yukarıda sayılan 2 madde gibi birçok algoritma daha mevcut: Google servislerine kaydolmuş ve Google uygulamalarını kullanan kişilerin cihazlarındaki uygulamalardan toplanan WIFI sinyalleri ve GPS ile belirlenen konum bilgilerinden de çok fazla bilgi toplanabiliyor.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# bazı Apple ürünleri

# iOS version history
| sürüm | çıktığı yıl |
|-------|-------------|
| 3     | 2010        |
| 4     | 2010        |
| 5     | 2012        |
| 6     | 2014        |
| 7     | 2014        |
| 9     | 2016        |
| 10    | 2017        |
| 12    | 2018        |

# MacOS version history

| number        | codename      | release date       | Most Recent Version and its release date |
|---------------|---------------|--------------------|------------------------------------------|
| Mac OS X 10.0 | Cheetah       | March 24, 2001     | 10.0.4 (June 22, 2001)                   |
| Mac OS X 10.1 | Puma          | September 25, 2001 | 10.1.5 (June 6, 2002)                    |
| Mac OS X 10.2 | Jaguar        | August 24, 2002    | 10.2.8 (October 3, 2003)                 |
| Mac OS X 10.3 | Panther       | October 24, 2003   | 10.3.9 (April 15, 2005)                  |
| Mac OS X 10.4 | Tiger         | April 29, 2005     | 10.4.11 (November 14, 2007)              |
| Mac OS X 10.5 | Leopard       | October 26, 2007   | 10.5.8 (August 5, 2009)                  |
| Mac OS X 10.6 | Snow Leopard  | August 28, 2009    | 10.6.8 v1.1 (July 25, 2011)              |
| Mac OS X 10.7 | Lion          | July 20, 2011      | 10.7.5 (September 19, 2012)              |
| OS X 10.8     | Mountain Lion | July 25, 2012      | 10.8.5 (12F45) (October 3, 2013)         |
| OS X 10.9     | Mavericks     | October 22, 2013   | 10.9.5 (13F1112) (September 18, 2014)    |
| OS X 10.10    | Yosemite      | October 16, 2014   | 10.10.5 (14F27) (August 13, 2015)        |
| OS X 10.11    | El Capitan    | September 30, 2015 | 10.11.6 (15G1510) (May 15, 2017)         |
| MacOS 10.12   | Sierra        | September 20, 2016 | 10.12.6 (16G1212) (July 19, 2017)        |
| MacOS 10.13   | High Sierra   | September 25, 2017 | 10.13.6 (17G65) (July 9, 2018)           |
| MacOS 10.14   | Mojave        | September 24, 2018 | 10.14.6 (18G87) (August 1, 2019)         |

# IPhone model farklılıkları
(source-id: 434) bu siteden karşılaştırma yapılabilir.

- "Plus" olan modeller (örnek "IPhone 8 PLUS" vs "IPhone 8"): sadece ekran boyutu, pil kapasitesi, kamera kapasitesi değişiyor.
- "S" olan modeller: S olan modellerde ekran boyutu değişmiyor fakat kamera ve pil ömrü değişebiliyor.

# iMac
masaüstü bilgisayar serisinin ismidir. kasa monitörün içindedir.

# Mac Mini
monitör olmadan satılan ufak kasadır.

# Mac
Apple'ın laptop ve masaüstü bilgisayarlar için olan OS ismi.

# MacBook
laptop serisi.

# Mac Pro
sunucu bilgisayarlar.

# iPod
portable media oynatıcı.

# iPad
tabletler.

# MacBook Air
özellikle ince olması için tasarlanmış laptoplar.

# PowerPC
AMD, ARM ve Intel CPU'larına alternatif CPU mimarisi. Apple, IBM ve Motorola tarafından geliştiriliyor.

# Macintosh
Apple'ın bilgisayar modellerinin serisinin ismidir. hem laptop hem bilgisayarları kapsar. yani MacOS çalıştırılan her cihazı kapsar.

# Hackintosh (or OSx86)
MacOS'un Intel CPU'lu mimarilerde çalışması için yapılan projedir. Eskiden Apple sadece PowerPC'li mimarilerde çalışıyordu. daha sonra Apple resmi olarak Intel mimarilerde çalışabilir hale geldi.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# HDMI (or High-Definition Multimedia Interface)
Girişi ince ve çubuk gibi olan yeni media aktarım kablosu.

```
##########################
#   ..................   #
#  ====================  #
 #  ..................  #
  ######################
```

# DVI (or Digital Visual Interface)
Girişi dikdörtgen (VGA'ya göre daha ince ama daha uzun) olan media aktarım kablosu.

```
__________________________
|      ................  |
|  __  ................  |
|      ................  |
|________________________|
```

# VGA (or Video Graphics Array)
Girişlerindeki köşeleri yuvarlar olan eski media aktarım kablosu.

```
 __________________________
(   ..................     )
 (   ..................   )
  (  ..................  )
   ――――――――――――――――――――――
```

# serial port (or seri port)
kablo ile iletişimde bilgilerin sıra ile iletildiği iletişim/kablo tipidir.

# COM (or communication port)
Bir cihazda bir den fazla giriş varsa COM1, COM2 şeklinde adlandırılır. Microsoft Windows bilgisayarlarındaki seri portlu girişler için bu terimi kullanmıştır.

# LinePrinTer (LPT or Paralel Port)
EN çok printer'larda kullanıldıklarından LinePrinTer olarak isimlendirilmişti. Her seferinde 8 bit (1 bayt) ile haberleşirler.

# Universal Serial Bus (or USB)
- Seri port çeşididir. fakat eski seri port'lara göre ekstradan güç kaynağı yolu da vardır. bu şekilde takılan cihaza elektrikte verir. üstelik eski seri portlara göre daha hızlı veri aktarımı yapabilmektedir.
- USB'nin bir çok sürümü vardır: 

# USB version history

| VERSION                          | MAX SPEED | COMPABILITY      |
|----------------------------------|-----------|------------------|
| 1.0                              | 1.5 MB/s  |                  |
| 1.1                              | ?         | ?                |
| 2.0                              | 60 MB/s   | ?                |
| 3.0                              | 625 MB/s  | with 1.1 and 2.0 |
| 3.1 Gen 1 (or SuperSpeed USB)    | 625 MB/s  | with 1.1 and 2.0 |
| 3.1 Gen 2 (or SuperSpeed+ USB)   | ?         | ?                |
| 3.2                              | ?         | ?                |

"3.0", "USB Implementers Forum (or USB-IF)" tarafından "3.1 Gen 1" olarak spesifikasyon ismi değiştirelerek piyasaya sunulmuştur. Kaynak: (source-id: 366)

USB kablosunun ucundaki cihaz, 2.0'ın desteklediği maximum güç'ten daha fazla elektrik ihtiyacı var ise, USB sürümleri geriye uyumlu olmasına rağmen çalışmayacaktır.

- USB'nin connector tipleri çok çeşittir. aşağıdaki connector'ler mevcuttur:

  - Type A
  - Type B
  - Type C
  - Mini A
  - Mini B
  - Mini AB
  - Micro A
  - Micro B
  - Micro AB

  Girişlerin görüntüleri buradan görülebilir: 
  - (source-id: 367)
  - (source-id: 368)

# plug and play (or PnP or tak çalıştır)
USB ve PCI'da kullanılabilen bir teknolojidir. USB'ye takılan cihaz belli standartlara uyduğu sürece (plug and play standartlarına) işletim sistemi takılan cihaz için kısmen/tamamen sürücü ihtiyacını algılayabilmektedir.

PnP desteği olan bir cihazı tanımama durumunun sebepleri:

- işletim sisteminin USB driver'ında sorun olması
- işletim sisteminde sorun olma durumu
- aygıtın sürücüleri sorunsuz tanınmıştır. fakat cihaz kendi sürücüsünün bir kısmını dışarıya verecek şekilde tasarlanmıştır. cihazın yönetimi için gerekli tüm sürücü tanınacak diye bir kaide yoktur. son kullanıcı olarak bizde hatalı tanındığını düşünürüz.
- iletişimde olan GUI uygulaması bizim işletim sistemimizde düzgün çalışmıyordur.

# Diğer kablo iletişim tipleri
- PCI (or Peripheral Component Interconnect)
- PCI-X: PCI'dan daha gelişmiş
- PCI express (or PCI-e): PCI'dan daha gelişmiş

PCI girişleri genelde buna benzer:

```
 _________________________________________
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  ―――――――――――――――――――――――――――――――――――――――|
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
 ‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾
```

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# Üç boyutlu ses (or environmental audio or surround sound)
ses yaratan kaynakların yönlerinin kulağa doğru şekilde gelmesini sağlayan ses sisteminin genel ismidir. sanal ve gerçek olarak iki şekilde bu ses yaratılabilir. gerçek için; hoparlörlerin konumu önemlidir (sol alt, sol üst, sağ alt, arka gibi). çalınan ses dosyası da her ses objesini hangi kanaldan yayılması gerektiği bilgisini içermelidir. oysa sanal surround ses için ses sistemine ihtiyaç yoktur. sadece çalınan ses dosyası her hoparlörün nasıl çalışması gerektiği bilgisini içerir. basit tekniklerle sanal; bazı hoparlörlerin sesinin kısılması, tizin yada basın arttırılması gibi taktiklerle sanal surround ses çıkarılmaya çalışılır. örneğin 2 hoparlör var ise; önümüzden geçen bir helikopter için önce sağ hoparlörden daha fazla ses çıkarılır sonrada sol hoparlörlerden daha fazla ses çıkarılır. böylece helikopter sağdan sola geçiyormuş havası yaratılmış olunur.

# mono vs stereo
mono bir sesi tüm hoparlörden aynı şekilde yansıtan ses sistemidir. oysa stereo'da her hoparlör farklı davranışlar sergileyebilirler.

# Dolby Digital (or old-name:Dolby Stereo Digital)
Dolby firmasının geliştirdiği ses teknolojisinin özel ismidir. içerisinde birçok alt teknoloji barındırmaktadır. 

# Woofer vs speaker (or hoparlör)
Woofer bas için özel geliştirilmiş bir speaker çeşididir.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# Personal computer (or PC)
Genel bir terimdir. özel bilgisayar serisi ismi değildir. MacOS'lerde PC grubuna girer.

# Phablet (or Phonelet or Tabphone or Fablet)
akıllı cep telefonları ile tabletlerin arasında büyüklükte olan cep telefonlarına verilen genel isimdir. en bilindik örnek Samsung note serisidir.

# Commodore 64 (or C64)
Eskiden piyasaya sunulan ve satışlarda rekor kıran bir ev bilgisayar modeli.

# mainframe
server olarak kullanılan bu cihazlar normal bilgisayarlardan farksızdır. donanım firmaları mainframe kategorisi altında sattıkları bu bilgisayarlarlar çok güçlü ve tek OS destekli oluyor (sanallaştırma ile farklı os'lar desteklenebiliyor). Tek OS destekli olduklarından sistem stabil ve hazır paket şeklinde satırlıyor. Bu sebeple özellikle enterprise firmalar sunucu niyetine, mainframe alıp kullanmayı tercih ediyorlar.

örneğin IBM mainframe satar ve birçok modeli vardır. İçlerinde de z/OS isimli işletim sistemi gelir.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# Otomat (or automata or automaton)
- otomatik olarak ardışık veya döngüsel işlemleri gerçekleştirebilen mekanik veya elektro-mekanik düzenektir. 
- canlı bir varlığın yapacağı kimi işleri yapabilen mekanik ya da elektrikli araç ya da aygıt.

# otomat teorisi (or özdevinim kuramı or Automata theory)
soyut 'matematiksel' makineleri veya sistemleri ve bu makineleri kullanarak hesaplama problemlerinin çözülebilmesini araştıran daldır.

# finite state machine (or finite state automaton or sonlu durum makinası or sonlu durum otomatı)
Sadece "__state machine (or durum makinası)__" denildiği de olmaktadır. Fakat başlıktaki terimleri kullanmak daha net olacaktır. Çünkü "infinite-state machine" kavramı da mevcuttur. Fakat piyasadaki kaynaklarda %99 sonlu durum makinesi konusu olduğundan, herkes direk "state mahine" terimini kullanmaktadır.

__finite automaton (or sonlu otomasyon)__ denildiği olmaktadır.

eylemler sonucu belli statelere düşen makinalardır. sonsuz durum söz konusu değildir. belli eylemler sonucu belli state'lere düşer.

# Muntazam Diller (or Biçimsel Diller or Formal Languages)
Tüm kuralları belli olan (syntax, words... gibi) yazılı dillere verilen bir isimdir. Örneğin; bilgisayara programlama dillerinin tümü biçimseldir.

# Turing makinesi
Turing (başka başlıkta detay var) makinesinin tarihte büyük önemi vardır. bilgisayarlar için programlama mantığının en temel işlevini yerine getirmektedir. Basitçe; 
- bir teyp (bant) üzerinden veri okur
- bir önceki veriyi okur yada bir sonrakini okur
- koşula(duruma) göre bir yere bir veri yazar(kaydeder). 
- tekrar ilk adıma gider

O zamanlar geliştirilen turing makinesi, onun özel ismi olsa da, günümüzde bu temel üzerine kurulu makinelere hala turing makinesi diyenler olmaktadır. Turing makinesi otomatlar içinde temel bir örnektir.

# Turing Complete
hesaplamalar/işlemler yapıp sonucu bulabilmemizi sağlayacak tüm makinelre turing-complete denir. örneğin Java turing complete'dir. her şeyi yapabilir ve sonuca gidebiliriz. fakat hesap makinesi yada SQL dili turing complete değildir. sadece bir yere kadar işlerimizi görebilir. programlama dilleri sanal olsalarda turing-complete olabilirler. turing complete bir donanım da olabilir.

(not: SQL ile de arkada native bir işlemi tetiklersem herşeyi yapabiliriz. fakat yularıdaki cümlede bu tarz durumların yapılamadığını varsaydık. SQL'i sadece tablo çeken ve tablolara yazan komutlar olduğunu varsaydık.)

# Turing testi (or Turing test)
Alan Turing tarafından yazılan bir makalede bahsedilen testtir. Makalede bu teste "imitation game" (imitation kelime anlamı: taklit) adı verilmiştir. Oysa piyasada herkes bu testi "Turing test" olarak isimlendiriyor.

Test temel olarak şunu yapıyor: Birbiri arasında sadece text ile mesajlaşabilen 2 taraf var. Soru soran taraf testi yapan taraftır. Soru soran; karşı trafın bilgisyar mı yoksa gerçek bir insan mı olduğunu anlamaya çalışır.

# polynomial vs non-deterministic polynomial
- bir programın inputa göre ne zaman sonlanacağı (çözülebileceği) çokterimli (polinomsal) bir ifade ile belirtilebiliyorsa o program polynomial'dir.
- polynomial sadece "P" ile de gösterilir. Tersi durum içinde "NP" kısaltması kullanılmaktadır.
- NP durumları n değerinin azaltıldığı ve bazı koşullarda kodun içinde kendini azalttığı programlarda söz konusu olmaktadır.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# quick format vs normal format
sadece Microsoft Windows'un sunduğu bir format atma şeklidir. tek farkı normal formatın, quick formata ek olarak, diski komple bad sectorlere karşı denetlemesidir.

# bad sector noktaları nereye kaydediliyor
bad sector tespit edildiği zaman MBR'ye kaydediliyor. bu sebeple; MBR yeniden yazıldığında bu bad sectorlerin listesi yokoluyor. zaten MBR boyutu çok ufak olduğundan sadece bir kısım bad sector burada tutulabiliyor.

# Self Monitoring Analysis Reporting Technology (or S.M.A.R.T.)
sabit disklerde bulunan bir teknolojidir. HDD'de bulunan bad sectorleri, anormal sıcaklık durumları gibi bir çok parametreyi algılayıp son kullanıcıya iletilmesi için sürücüleri aracılığı ile işletim sistemine bildirir. SMART bilgileri işletim sistemine bildirir fakat kendi içinde bir kayıt olmalıdır. bu kayıtlar HDD parçasının özel bir kısmında (işletim sisteminin göremeyeceği bir kısımda) bulunmaktadır.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# instruction set architecture (or ISA)
Intel developed the "x86" architecture which was a 16-bit architecture (with device "Intel 8086 microprocessor").

Intel developed a 32-bit instruction set for x86 and called it "i386" for the Intel 386-series of CPUs, its first 32-bit "x86-compatible" CPU.

AMD developed AMD64 for 64-bit instruction set for x86. But Intel did not want the term AMD and it refers as "x86-64 (or x86_64)". AMD64 was "x86" compatible.

"x64" is a term which is using to refer AMD64.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# CPU cache
CPU kendi içinde memory tutmaktadır. Bu şekilde RAM'den daha hızlı çekmesi gerektiği bilgileri burada tutar. ama pahalı olduğundan RAM'e göre daha ufaktır.

CPU içerisindeki bu bellek bölgeleri L1, L2, L3 gibi adlandırılırlar. L'nin yanındaki sayı ne kadar küçükse o bellek bölümü o kadar hızlıdır. kaynak: (source-id: 369) "What is caching?" 2inci paragraf.

eskiden bu bellekler anakart üzerindeydi fakat daha sonra anakarta erişim süresi ile zaman kaybetmemek için CPU'lara entegre edildi.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# iot (or internet of things or nesnelerin interneti) vs ioe (or internet of everything)
bu iki kavramın farkı net olarak belirgin değildir. ikiside aynı kapıya çıkmakta. IoE, Cisco firmasının kendi iot ürünlerine verdiği isimdir. fakat genel olarak ioe; tüm internet'e girebilen kavramları kapsar (internet of social media, Internet of Information(blogs and websites) gibi), oysa iot sadece internete girebilen cihazları kapsamaktadır. iot, ioe'den türemiştir diyebiliriz. ioe o kadar geniş bir kümeyi içine alırki; internete bağlanmış insanlar (son kullanıcı) bile bu kümenin içindedir.

# m2m (machine to machine)
iot'den çok farklı bir kavram değil. makineler arası iletişim kuran cihazlara denir. m2m'lerde, iot lerden farklı olarak; insana sunulan arayüzün olmamasıdır (or aşırı kısıtlı olmasıdır). bunun dışında; m2m'de makineler birbiri arasında iletişim kurarken, iot kavramında; daha komplike bir yapıyı ele alır (iot için geliştirilmiş özel yazılımlar ve algoritmalar ve protokoller). m2m, iot kümesinin içindeki bir elemandır.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# Mobil iletişim terimleri

## GSM (or Global System for Mobile Communications)
Baz istasyonlarından yararlanılarak kullanılan mobil iletişim protokolleridir.

# GSM standartlarındaki protokollerin sürümleri (nesilleri - generations):

- 0G (or pre-cellular) analog veri akışı kullanılırdı.

- 1G analog veri akışı kullanılırdı.

- 2G - İlk sayısal veri akışı kullanan GSM teknolojisidir.

- 2.5G - kullandığı teknoloji: GPRS (or G (GPRS'in ilk karakteri) or General Packet Radio Service)

- 2.75G - kullandığı teknoloji: Enchanced GPRS (or EDGE or E (EDGE'nin ilk karakteri))

- 3G - kullandığı teknolojiler:

   - UMTS (or Universal Mobile Telecommunications Service)

   - FOMA

   - W-CDMA

   - WCDMA (or Wideband Code Division Multiple Access)

   - WCDMA2000

   - HSPA (or H or High Speed Packet Access)

     HSPA = HSDPA (or High Speed Downlink Packet Access) + HSUPA (or High Speed Uplink Packet Access)

- 3.5G (or 3G+ or Turbo 3G or H+ or HSPA+ or Envolved HSPA)

- 4G (or LTE or Long-Term Evolution)

- 4.5G (or 4.25G or LTE-A or LTE-Advanced)

Not: 

- LG G3 (Canada), LG G3 (Korea) gibi aynı cihazın birçok farklı ülke ismi ile türevi görülecektir. Yukarıdaki tabloda görüldüğü üzere özellikle 3G'nin birden fazla teknolojisi var. Bir ülke birden fazla teknolojiyi destekleyebilir. İşte bu sebeple teknolojilere uygun aynı telefonun modelleri çıkarılmaktadır.

- Bazı telefonların aynı modeli Wi-Fi yada LTE gibi farklı prefix'ler almaktadır. 4G'li olan cihazlar hem Wi-Fi hem 4g'yi desteklemektedir. Oysa Wi-Fi olan sadece Wi-Fi'yi destekliyor. Wi-Fi olan modeller %99 tablettir yada phaplettir. SIM kart hiç takılamıyordur. Bu tarz özellik karşılaştırmaları bu tarz sitelerden yapılabilir: https://www.gsmarena.com/compare.php3?&idPhone1=8505&idPhone2=5253

1 saniyede teorik max download/upload hızları (bu hızlara pratikte ulaşamıyorlar):

| Sürüm | max download/upload speed |
|-------|---------------------------|
| 0G    | internet yok              |
| 1G    | internet yok              |
| 2G    | 10KB      / 10KB          |
| 2.5G  | 50KB      / 25KB          |
| 2.75  | 200KB     / 100KB         |
| 3G    | 370KB     / 120KB         |
| 3.5G  | 14-84MB   / 5-23MB*       |
| 4G    | 100MB     / 50BM          |
| 4.5G  | 1GB       / 500MB**       |

- 3.5G'nin birçok  sürümü çıktı. en eski ve en yeni sürümünü hızları yazılmıştır.

- 3.5 ve üzerinde hız çok yüksek olduğundan kota tüketimi hızlı olmaktadır. bu sebeple güncel mobil uygulamalar bundan korunacak şekilde tasarlanmaktadır. örneğin; video player'lar hiçbir koşulda videonun tamamını indirmiyor. sadece kullanıcının bulunduğunu noktanın ve birkaç saniye ilerisi yükleniyor.

# GPS (or Global Positioning System)
sadece konum bilgisini elde etmek için gerekli protokol. BUnun için fırlatılmış uydulardan bilgi alır. Bu bir GSM protokolü değildir.

# Roaming (Dolaşım)
- Aynı hat ile yurtdışında GSM protokolünün kullanımına verilen isimdir.

- network dünyasında ise bu terim farklı amaçla kullanılıyor: bir cihaz, bir baz istasyonu/modem'e bağlıdır. eğer cihaz yer değiştirirse farklı bir cihaza bağlanabilir. bu bağlantı sırasında yapığı işlem kesilmeyebilir. işte böyle bir durumda bu cihaz dolaşım yapıyor anlamına gelir.

# Cellular network (hücresel ağ)
WIFI için modemler, GSM için baz istasyonları birer hücredir. Hücrelerden yararlanan bu tip ağların tümüne hücresel ağ denir. Fakat piyasada genelde mobil ağları temsilen kullanılır.

# SIM (or Subscriber Identity Module or Abone Kimlik Modülü) kart boyutları

Full-size (1FF) telefon kartları ile birlikte dağıtılan SIM'lerdir. gerçek bir kredi kartı büyüklüğündedir. genelde telefon kulübelerine takmak için kullanılır.

Mini-SIM (2FF) - 3ff'e göre biraz daha büyük bir çerçeve kaplar. 

Micro-SIM (3FF) - çip'in etrafını çok çok ufak bir çerçeve kaplar

Nano-SIM (4FF)  - sadece çip'in kendisi vardır.

# SMS (or short message service)
sadece text yollanması sağlanıyor.

# MMS (or Multimedia Messaging Service)
media dosyaları da yollanabiliyor.

# Unstructured Supplementary Service Data (USSD)
- yazılımcılar arasında "Quick Codes" veya "Feature codes" olarak adlandırılırlar.

- SIM kartın servis sağlayıcısına istek atıp cevap almayı sağlayan kodlardır. örnek: \*123# bize kalan kullanım miktarımızı döndürmektedir.

- bazı kodlar USSD değildir. örnek IMEI döndüren \*#06# kod telefon üreticisinin bir kodudur ve servis sağlayıcısına erişim gerektirmeden cevap döndürür.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# IMEI (or International Mobile Equipment Identity)
Cihazın donanımında yüklenen bu tekil 15 haneli değer, yazılım tarafında dışarı iletilirken değiştirilebilmektedir. Bu sebeple servise sağlayıcılar birden fazla IMEI'li cihazın kullanımına izin vermektedir. Fakat Türkiye gibi ülkelerde cep telefonu numarası ile IMEI isteğe bağlı eşleştirilmektedir. Zira Türkiye'de aynı anda birden fazla cihaz aynı IMEI kullanamamaktadır. Böyle bir durumda telefon kullanılabilir, fakat o cihazda hat kullanılamaz duruma gelmektedir. Hat takılamayan cihazlarda IMEI bulunmaz.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# Near Field Communication (or NFC) vs Bluetooth vs Wireless vs WIFI (or Wireless Fidelity)
Wireless tüm kablosuz iletişimlere verilen genel isimdir. Telsizler, WI-FI, NFC, Bluetooth gibi tekneolojiler wireless kategorisindedir. Wi-fi halk arasında en çok kullanılan teknoloji olduğunda çoğu zaman sadece wireless olarak adlandırılır.

| name      | max distance (about) | Bandwidth |
|-----------|----------------------|-----------|
| NFC       | 5 cm                 | 2 kbps    |
| Bluetooth | 30 metre             | 800 kbps  |
| WIFI      | 90 metre             | 11 Mbps   |

# Bluetooth version history

| version |
|---------|
| 1.0b    |
| 1.1     |
| 1.2     |
| 2.0     |
| 2.1     |
| 3.0     |
| 3.1     |
| 4.0     |
| 4.1     |
| 4.2     |
| 5       |
| 5.1     |

her versiyon tüm versiyonlar ile geriye uyumlu çalışıyor.

Bluetooth 4.0, "Bluetooth Smart" ismi ile pazarlandı. Bluetooth 4.0, aynı zamanda "Bluetooth Smart" özelliği içeriyor. Bu özellik opsiyonel kullanılabiliyor. "Bluetooth Smart" özelliği geriye uyumlu değil. hatta "Bluetooth Smart" kullanan bir cihaz, 4.0 öncesi Bluetooth cihazları ile birbirlerini pair olarak göremezler. kaynak: (source-id: 370)

"Bluetooth Smart Ready", Bluetooth 4.0 olan "host" olan cihazların logosunun altında yazmaktadır. "Ready" ek bir özellik değildir.

Bazı sürümler sadece yazılımsal update gerektirirken, bazı sürümler hem yazılımsal hemde donanımsal güncellemeyi şart kılar.

her versiyon ekstra bir özellik içeriyor:

| version of Bluetooth | Basic rate (BR) | Enhanced Data Rate (EDR) | High Speed (HS) | Low Energy (LE) | Slot Availability Masking (SAM)  |
|----------------------|-----------------|--------------------------|-----------------|-----------------|----------------------------------|
| 1.x                  | Yes             | No                       | No              | No              | No                               |
| 2.x                  | Yes             | Yes                      | No              | No              | No                               |
| 3.x                  | Yes             | Yes                      | Yes             | No              | No                               |
| 4.x                  | Yes             | Yes                      | Yes             | Yes             | No                               |
| 5.x                  | Yes             | Yes                      | Yes             | Yes             | Yes                              |

Bluetooth standartlarına ek olarak bazı standartlar geliştiriliyor.  bu şekilde; örneğin; sadece "stereo kulaklıklar" için standart geliştirilmiş oluyor. bu standartlara Bluetooth dünyasında "profil" deniliyor. birçok profil burada açıklanıyor: (source-id: 371)

Bluetooth profilleri sadece belli Bluetooth versiyonlarını desteklemektedir.

Bluetooth cihazlarınında MAC adresleri vardır.

Android üzerinden örnek kod ile akışı anlatalım:

```java
BluetoothHeadset bluetoothHeadset;

// Get the default adapter(device)
BluetoothAdapter bluetoothAdapter = BluetoothAdapter.getDefaultAdapter();

private BluetoothProfile.ServiceListener profileListener = new BluetoothProfile.ServiceListener() {

    public void onServiceConnected(int profile, BluetoothProfile proxy) {
        if (profile == BluetoothProfile.HEADSET) {
            bluetoothHeadset = (BluetoothHeadset) proxy;
        }
    }
    public void onServiceDisconnected(int profile) {
        if (profile == BluetoothProfile.HEADSET) {
            bluetoothHeadset = null;
        }
    }
};

// Establish connection to the proxy.
bluetoothAdapter.getProfileProxy(context, profileListener, BluetoothProfile.HEADSET);

// ... call functions on bluetoothHeadset

// Close proxy connection after use.
bluetoothAdapter.closeProfileProxy(bluetoothHeadset);
```

Pair olan iki cihaz arasındaki iletişim client-server mimarisi ile aynıdır. Android'de BluetoothServerSocket ve BluetoothSocket kullanılarak bilgi alışverişi olur. 

# Radyo Frekansı ile Tanımlama (or RFID or Radio-frequency identification or High-Frequency RFID or HF RFID)
radyo: Elektrik dalgalarının özelliğinden yararlanarak seslerin iletilmesi sistemidir.

RFID; radyo frekanları ile veri transferi teknolojisidir. "Tanımlama" kelimesini almasının sebebi, ortamdaki birçok farklı frekans/data arasından doğruyu istenileni algılayabilmesidir.

RFID üç temel nesneden meydana gelir: Okuyucu, Anten ve etiket. Etiket ve anten aynı cihazda olmalıdır. Etiket olan cihazda bir çip olması da gerekmektedir.

NFC, RFID'nin bir uzantısıdır. NFC çift yönlü iletişimi sağlarken, RFID tek yönlüdür. Bunun sebebi aslında; NFC'nin hem "NFC okuyucu" hemde "NFC etiketi" olma özelliğidir.

RFID etiketleri 3 çeşit olabilir:
- aktif olanlar kendi içlerinde bir güç kaynağı barındırırlar ve uzak mesafeden ID'nin okunabilmesini sağlarlar.
- pasifler ise gücü okuyucudan alırlar bu sebeple yakın mesafeden okunmaları gerekir.
- yarı pasifler ise; kendi içleride pil barındırırlar fakat sadece okunduklarında devreye girerler ve okuyucudan güç harcamazlar. sadece tetiklenirler. Bu çeşit piller günlük kullanılan kartların içine sığmakta ve çok uygun fiyattadırlar.

# Smart kart vs manyetik kart vs chip'li kart

## manyetik kart
kartın arkasında bulunan bir şerit üzerindedir. çabuk bozulur ve kopyalanabilirler. bu şerit içindeki veri değiştirilememektedir.

## çipli kartlar
çip elektronik devre anlamına gelir. chip'li kartlar bir elektronik devreye sahiptirler. process işlemi yapabilirler. içinde bellek vardır. içindeki değerler process işlemi sırasında değiştirilebilirler. chip gibi gelişmiş tüm kart teknolojilerine genel olarak "smart cart" adı verilir. bu kart tipleri sadece kredi kartlarında değil, birçok kartlarda tercih edilmektedirler.

Manyetkikler sadece bilgi barındırırken, çipliler bilgiye ulaşmadan önce ve sonra process yapacak elektronik devrelere sahiptirler. Bu sebeple; çipin içindeki bilgi klonlanamaz. Çünkü kart-reader tarafındaki private key ile ancak çip(kart) doğru dönüşü yapmaktadır. Zaten yaptığı dönüşte yine bir key ile şifrelenmiş ve ancak kart-reader içine gömülmüş olan key ile açılabilmektedir.

# temaslı kartlar
çipli ve manyetikli kartlar fiziksel olarak okuyucuya temas ettirilmelidir.

# temazsız kartlar (or Proximity card or Proximity card)
Proximity kelime anlamı: yakınlık

temaslı akıllı kartlar direk olarak, güç kaynağına temas ettirildiği için elektrik akımını alabilirler. temassız kartlarda ise ekstradan bir anten vardır. kart okuyucu sürekli elekromanyetik dalga üretir. karttaki anten elektromanyetik sinyalleri elektrik akımına çevirir. bu şekilde kart içerisinde güç kaynağı elde edilmiş olur. data okunma işlemi yapıldıktan sonra kart tarafında da elektromanyetik dalga üretilir ve data okuyucuya yollanır.

Wireless şarjlarda aynı teknoloji ile çalışır. Wireless şarj aleti elekromanyetik dalga yaratır. Bu dalgaları alan cep telefonu şarj olmaya başlar.

temazsız kartlarda da akıllı olan (process yapan) veya sabit bilgiyi döndüren kartlar olabilmektedir.

pasif olan standart temazsız kartlar 2-5 santim arasından okuma işlemini yapmaktadırlar.

aktif olan standart temazsız kart teknolojileri 150 metreye kadar algılama yapabiliyor.

# MIFARE
özel şirkete ait temazsız kartlar için geliştirilmiş çip ailesidir. birçok sürümü vardır.

# beacon
Türkçe'de el feneri; işaret ışığı (örnek: arabalarda olan) anlamına gelen cihazların tümüne verilen isimdir.

# Bluetooth beacons
Düşük enerjili Bluetooth teknolojisi ile çalışan cihazlara verilen genel isimdir. Bu cihazlar yakında olan diğer Bluetooth alıcılara bildirim yollamak ve eğer alıcıda kabul etmiş ise; bildirim almak için kullanılmaktadır.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# nano teknoloji
günümümüzdeki tüm teknolojik cihazlar (elektronik aletler...) sadece birçok molekülün bir araya getirilerek, karıştırılarak, veya kimyasal filtreleme işlemlerinden geçirilerek, ufak parçalara bölünerek yapılmaktadır. fakat nano teknoloji ile; atomlar (or atomların yanyana gelerek yarattıkları moleküller) tamamiyle insanın tasarladığı gibi oturtulabilecekler. yani; atom seviyesinde montaj yapılabilmektedir. durum böyle olunca şu andakinden binlerce kat daha ufak cihazlar tasarlanabilecek.

nanometre uzunluğu bir atomun ortalama çapına denk gelmektedir.

# kuantum bilgisayarlar (or Quantum computers)
Quantum bilgisayar aslında processing'i hızlı yapan kısmı içeirir. yani CPU ve gpu'ya alternatiftir. fakat ona adapte olan cihazlarında uyumlu olması gerekir. fakat quantum alanındaki gelişmeler sadece processor kısmı içindir ve diğer bilgisayar elemenlarının şu ana dek sunulan klasik cihazlara göre bir artıları yoktur. sadece quantum işlemcileri ile uyumludurlar.

quantum processorler CPU'da olduğu gibi qubit'lerde bilgi sakalayabilirler (buna __quantum state__ denir).

quantum bilgisayarlar yapısı gereği her algoritmayı çözemiyor. ve maliyetli cihazlar olduklarından sadece ihtiyaç duyduğumuz kod bloklarını orda çalıştırıyoruz. quantum cihazda çalışan programlama dillerinin buna göre tasarlanmış olması gerekiyor. Binary cihazlarda simulatorler aracılığı ile gerçek cihazda olmadan test çalışmaları/kod denemeleri yapılabiliyor.

bir __qubit (or qbit or quantum bit)__ 0 veya 1 olabiliryada bunun arasıda olabilir. bu ara pozisyonlara __kuantum süperpozisyonu (or quantum superposition)__ denir. örneğin 1 adet qubit şu superpozisyonda olabilir:

- 0.3 --> 0 olma olasılığı (probability)
- 0.7 --> 1 olma olasılığında (probability)

Qubit'in bulunduğu bu değerlere "qubit state" denir.

bu qubit'i tek sütunlu bir matris olarak gösterebiliyoruz. ve bunu vektör olarak kullanabiliyoruz:

1'e denk gelen qubit şu vektör ile ifade edilir:

```
(0)  = |1>
(1)
```

0'a denk gelen qubit şöyle ifade edilir:

```
(1)  = |0>
(0)
```

qubit'in state'ini sitediğimiz gibi setleyebiliriz, fakat okuyamayız. okduğumuzda ya 1 yada 0 okuruz. quantum-un state'i okuduğu anda yok olur. bu state'in yok olma durumuna bu durumda "lost of Quantum coherence" denir.

qubit'i okuduğumuzda 0 mı 1 mi okuyacağımız ihtimallere kalmış. işte burada "probability" devreye giriyor. probability'nin 0 a veya 1 e mi daha yakın olduğu önemli.

görüldüğü üzere quantum processor'lerle her algoritmayı çözmek verimli olmayabilir. fakat performance olarak bakıldığında, 1 birimde, 1 yada 0 tutmak yerine, superpozisyon bilgisi saklayabiliyoruz.

quantum programlama dillerinde, byte int gibi aynı zamanda "qubit" primitive nesneleri olur.

__kuantum mekaniği (or nicem mekaniği or dalga mekaniği or Quantum mechanics)__ atom ve atom altı teknolojilerle ilgileniyor. kuantum mekaniği alanındaki çalışmalar ile nano teknoloji alanındaki çalışmalar çok fazla ortak yönleri olduğundan insanlar arasında bu iki teknoloji karıştırılmaktadır. oysa nano teknoloji ile quantum mekaniği farklı konulardır.

# çevresel gürültü
kuantum bilgisayarlar etraftaki gürültüden etkilenirler ve yanlış hesaplama yapmalarına sebep olur. bu sebeple olabilecek en soğuk ortamda çalıştırırlar.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# integrated circuit (or monolithic integrated circuit or IC or chip or microchip or çip or mikroçip or tümdevreor yonga or kırmık or tümleşik devre or entegre devre)
elektronik devre anlamına gelir. birden fazla devre elemanının birleştirilmiş parçadır.

# Mikroişlemci (microprocessor)
içinde ALU bulunana mantıksal işlemleri yapmak için giriş çıkış birimleri olan elektronik çip'tir. genel amaçla tasarlanır. dışarı tarafta neye hizmet edeceklerin bir önemi yoktur.

# mikrodenetleyici (microcontroller)
dışarıda neye hizmet edeceklerine göre özel tasarlanırlar. bacaklarından aldığı komutları işlerler. bu komutlar dışında parametreleri yoktur. microprocessor, microdenetleyici'den daha pahalıdır. çünkü microprocessor içindeki ALU genel amaçlı olduğu için birçok ALU işlemi barındırır. oysa mikrodenetleyici içindeki ALU sadece mikrodenetleyici API'si içindeki komutları çlıştıracak şekilde optimize edilmiştir.

# central processing unit (CPU)
CPU bir Mikroişlemci'dir. sadece bu özel ismi; tüm sistemde (bilgisayar, telefon, buzdoladı...) asıl microişlemci görevinin hangi parçaya ait olduğunu göstermek için verilmektedir. Bir bilgisayarın tüm birimlerinde birer ufakta olsa microişlemci olabilir. Bu durumda tüm sistemde birden fazla microişlemci olmuş oluyor. Fakat tüm sistem için asıl CPU'lar bellidir.

# CPU ve GPU (graphic process unit)
arasındaki farkı anlamanın basit bir yolu, görevleri nasıl işlediklerini karşılaştırmaktır. CPU ardışık seri işlem için optimize edilen birkaç çekirdekten oluşurken, GPU birden fazla işi eşzamanlı olarak yürütmek için tasarlanan binlerce daha küçük, daha verimli çekirdekten oluşan büyük ölçüde paralel bir mimariye sahiptir. GPU'lar paralel iş yüklerini verimli bir şekilde işlemek için binlerce çekirdeğe sahiptir.

# PIC
are microcontrollers made by Microchip Technology. PIC'ler içerisindeki bulundurduları bellek sayesinde programlanabilirlerdir.

# programmable logic controller (or PLC or programmable controller)
microcontroller'dır. içindeki hafızası sayesinde programlanabilirdir. özellikle endüstride fabrikalarda makinelerin işleyişini yönetmek için kullanılır. kolay ve hızlı programlanabilmesi için genelde IDE gibi destekleri ve hazır kütüphaneleri vardır.

PLC dünya pazarında sırası ile (çoktan aza doğru) bu markalar (brands) hakim: Siemens, Rockwell Automation, Mitsubishi, Schneider.

# Arduino
açık kaynak donanım prensiplerine dayalı microcontroller'dır. işletim sistemi yada firmware barındırmaz. direk olarak üzerine yazılan kod çalıştırılır. çok basit bir yapıdadır.

# rasperry pi
işletim sistemi barındırır. bir mini-bilgisayar gibi düşünülebilir. donanım açık kaynak değildir.

# single-board computer (or SBC)
sadece kasa taraı olan mini bilgisayarlara verilen isim. örneğin: rasperry pi.  Arduino tam olarak bütün bir bilgisayar kasası işlevini yerine getiren modüllerden oluşmadığından (video kart girişi, enthernet girişi gibi) single-board computer grubuna giremez.

# PDA (or Personal Digital Assistant or personal data assistant or handheld PC)
Cebe sığacak boyutta olan tüm bilgisayarlardır. Günümüzün cep telefonları PDA kategorisindedir.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# temel devre elemanları

# pozitif/negatif yük
bir maddede proton'dan fazla elektron var ise; o madde eksi yüklüdür. tersi olunca o madde + yüklü olur. bu sebeple; bir devrede elektronlar gerçekte -'dan +'ye doğru akar. fakat hesaplamalarda tam tersi uygulanır.

# voltaj
iki kutupun arasındaki potansiyel farktır. birimi volt. potansiyel farkın yarattığı hız.

# direnç (or resistor)
Birimi Ohm (birimin simgesi (omega işareti) Ω'dur).

# akım (or current)
birimi amper'dir. potansiyel faRkın dirençe karşı uyguladığı kuvvete amper denir.

# OHM Kanunu formülü
V = I # R

# pil
güç kaynağıdır (or power supply). pilin üstünde voltaj ve amper yazması gerekir.

# Elektriğin gücü
Birimi WATT. V*I formulünden bulunur. WATT bir güç birimidir.

# DC (or direct current)
- den artıya gidiş sürekli düzenli. bir elektron hiç kablo üzerinden gidiş geliş yapmıyor.

tomas edison'un çalışmaları ağırlı olraka bu yöndeydi. 

# General Electric
tomas editosun'un kurduğu 2017'de hala faaliyette olan şirket.

# AC (or alternatif current)
tesla'nın çalışmaları ağırlı olarak bu yöndeydi. ac'de akış halinde olan elektronlar kısa vadeli gitgeller yapabiliyor.

# bobin
elektrik yükü biriktiren component.

# röle
içinde bir mıknatıs barındırıyor. anahtarlama yerine kullanılıyor. anahtarlama uçlarına güç verilerek açılıp kapatılıyor.

# priz
Prizler guc kaynagidir. Bir tarafi arti bir tarafi eksidir. prizler takilan devrenin direncine gore amper yayar. Bu sebeple sabit enerji harcanmaz. TakiLan alete gore elektrik harcanir.

artı ve eksi yönü prizlere ters takılırsa devre yine calışır. Fakat bu durum normal piller/kaynaklar için gecerli değildir. Prizlerin içi buna göre tasarlanmıstır. Bu durum ileri seviyede elektrik bilgisi gerektiren bir fizik konusuna dayanır.

# akım ve volt değişimi
seri bağşanmış akışlarda direnç ile karşılaştıkça amper azalır voltaj da azalır.
oysa paralel bağlanmış akımlar var ise; amper aynı kalır fakat voltaj 2'ye bölünür.

# transistör
anahtarlama yerine kullanıyor. anahtarlama uçlarına güç verilerek enable/disable ediliyor. transistör benzer şekilde farklı amçlar içinde kullanılıyor. örneğin; voltaj yükseltici.

# diode (or diot)
ac'yi dc'ye çeviren component. ve sadece tek yönde geçişe izin veriyor. + dan eksiye gidiş varken , pil yön değiştirdiğinde akımın geçmemesini sağlar.

# alternatör
mekanik enerjiyi elektrige ceviren sistemdir. Barajlar buna örnektir. Barajlar basınç ile elektrik üretir. 

# çip'lerin bacakları
çiplerin birçok bacağı vardır. bir çipi kullanmak istediğimizde bu bacaklarına komut gönderiririz. bir komutu tanımlamak için en az 8 bit'e ihtiyacımız vardır. 8 sayısı standart olarak belirlenmiştir. zaten 8'in altı çipin dışardaki API'sini çok kısıtlı olmasına sebep olacaktır.
Bir çip eğer 8-bit desteği var ise (örneğin bir bilgisayardaki işlemci 32-bit 64-bit desteği olması gibi), o çipe sadece 1 komut sadece 8 bacağından birden (aynı anda) verilmelidir. Ancak işlem bittiğinde farklı bir komut daha verilebilir. Fakat 16-bit bir çip'e aynı anda 2 farklı komut verilebilir. Çip bu aldığı 2 komutu paralel şekilde yürütecektir.

# component'lerde uzun bacak vs kısa bacak
uzun bacak her zaman + yönünde, kısa bacak - yönünde bağlanmalıdır. kırmızı renk genelde + yönünde bağlanacak kısmı temsil eder. siyah ise - yönünü temsil eder.

# potansiyometre (or reosto)
ayarlı (arttırıp azaltılabilen) dirençtir.

# osiloskop
elektriğin dalgalarını (direct or alternatif current) grafikte gösteren cihazdır.

# kısa devre
akım her zaman direnci az olan yoldan geçer. Örneğin aşağıdaki gibi bir durumda akım boş olan yoldan geçecekti. boş olan yol aslında çok çok az da olsa direnç barındırır. bu sebeple V=IR formülünde R küçüldükçe I artacağı için I çok büyür ve kablo buna dayanamaz erir yada güç kaynağında patlama meydana gelebilir. bu duruma kısa devre adı verilir.

```
- +V- ----------R----------
-         -         -     -
-         -         -     -
-         -----------     -
-                         - 
-                         -
---------------------------
```

# Topraklama
- istege bagli yapilir.
- Ucuncu bir kablo (hat) yeryuzune cekilir. bu kabloda cok ufak bir direnc vardir. Eger akim yuksek gelirse akim az direnc olan yerden gitmek isteyeceginden akim topraga gider.
- Toprak notr dur. Uzerine gelen elektrik yeryuzune dagilir. Sonsuz buyuklukte direnc olarak dusunulemez. Gelen elektrik dagilir.

# flip flop
en az bir bitlik veri tutabilen devredir. dolayısı ile önceki girişlerinde çıkışa etkisi vardır. bir çıkışın devrenin içinden farklı bir elemana bağlanması sonucunda böyle bir mantık devresi ortaya koyulabilmektedir. bu şekilde çıkış (yanibir önceki durum), yeni girişlere etki edecektir.

En basit flip flop'lardan biri SR Flip flop'tur. Girişleri S ve R olarak adlandırılır. S girişi set input'umuz, R girişimiz ise reset input'umuzdur. set girişimiz bir önceki durumu değiştirmek için değil, durumu 1'e set etmek için kullanılır. yani çıkışımızı1 yapmak istiyorsak set'i 1 yapmalıyız. ama çıkışımızı sıfırlamak istiyorsak; ancak reset ile sıfırlayabiliriz. eğer reset ve set 1 olursa flip flop patlıyor çünkü mantıksız bir durum. 

JK Flip Flop ise SR flip flopun R=S=1 durumuda patlamaması için yapılmıştır. bu devre S=R=1 durumunda bir önceki çıkışın (durumun) tersini vermektedir.

D flip flop tek girişlidir. D harfi data'nın ilk harfinden gelmektedir. Girişin tersinin JK flip flopa bağlanması ile oluşuturulan bir flip floptur. giriş ne ise çıkış odur. sadece clk değiştiğinde çıkış değişeceği için veriyi saklamış olur.

# clock pulse
kısaltması: clk. bu da devrenin bir girişine bağlı bir inputtur. belirli aralıklarda 1 ve 0 değerini verirler. bu şekilde sadece belli durumlarda devre tetiklenir. örneğin; Eğer flip-flop pozitif kenar tetiklemeli (rising edge triggered) ise, çıkışlar sadece girişlerin pozitif kenardaki değerlerine göre değişir. yani tam olarak; clk sıfırdan 1'e geçerken flip flop yeniden inputlar ile çıkışı hesaplayacaktır.

# elektrik alanı vs manyetik alan vs elektromanyetik alan
elektrik yükü sadece hareket halindeyken kendi etrafında hem "elektrik alanı" (doğal bir enerji çeşidi) yayar hemde "manyetik alan" oluşturur. bu iki alana birlikte "elektromnyetik alan" denir. elektromanyetik alan elektroniların hareket halinde olduğu alandır. elektronların frekansı ve dalga boyuna göre insanlar bunları gruplandırmıştır. örneğin; gama ışınları, X-ışını, morötesi, görünür ışık, kızılötesi, mikrodalga, radyo ve tv dalgaları gibi. Bunun dışında NFC, WI-FI, RFID, temassız akıllı kartlar gibi tüm teknolojiler manyetik alanın farklı dalga boylarındaki protokollerini temsil eder.
Örneğin; çipli kartlarda elektronik devre vardır. Uzaktan elektromanyetik alan yaratılarak elektroniların o devreyi çalıştırması ve sonucun geri alınması sağlanır. BÖylece uzaktan elektrik kaynağı olmayan kart çalıştırılmış olunur.

# elektrik hızı
Elektrik ışık hızına cok yakindir.  Tasindigi ortama gore de hızı degisir. Bu sebeple radyo ve internet gibi kanallar da çok hızlı çalışır. internetin yavaş olmasının sebebleri;
- paralel işlemlerin yazılımlar tarafından sırada bekletilmesi
- elektriği taşındığı kabloda kayba uğraması ve buna bağlı olarak bazı data paketlerinin tekrar sırada beklemesi
- elektronik devreye varan elektriğin farklı formlarda çevrilmesi için geçen süreler
- Bir elektronik chip'e kablodan gelen elektrik ilk transistöre aktarilir. Transistor cok daha duzenli bir bicimde 1 ve 0 lari clock pulse frekansinda devrenin icine yollar. clock pulse için geçen sürelerde kayıptır. Çünkü her pulse belli bir zaman dilimi içinde tanımlanır. Örneğin saniyenin binde biri boyunca gelecek volt değeri 1 yada 0 olarak kabul edilmesi... Clock pulse'lar sadece kabloların cihaza takıldığı girişlerde yoktur. Cihazın kendi içinde her modülün arasında da birimler arası haberleşmede clock pulse'lar kullanılır. hatta her elektronik parçanın kendi içindeki birimlerde clock pulse'lar ile haberleşir.

# Elektromanyetik tayf (or elektromanyetik spektrum)
spektrum çeşitlilik anlamına gelir. elektromanyetik spektrum elektromanyetik daglaların ve frekansın değişmesi ile yaratılan elektromanyetik alan çeşitlerini temsil eder.

# elektrik vs elektronik
elektrik; yüklerin hareketini fiziksel olarak inceleyen bir bilim dalıdır. çalıştığı bazı konular: statik elektrik, elektrik akımı, elektrik alan, manyetik alan...

elektronik ise; maddenin elektriksel özelliklerini kullanarak digital ortamlarda sinyal işleme üzerine çalışır.

# electricity (or elektrik) vs Electric
Electric'in tam olarak Türkçe karşılığı olmadığı için elektrik olarak kullanılmaktadır. 

electricity, elektriği ifade eder.

electric; ise "electric kettle" gibi onu kullanan sistemlerin önüne koyulan özel bir terimdir. 

__'Electrical'__ ise; 'elektriksel' olarak Türkçeye çevrilir ve elektrikle ilgili olan anlamında kullanılır: elektriksel arıza (or electrical faults)...

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# uninterruptible power supply (or uninterruptible power source or UPS)
asıl güç kaynağı kesilince devreye giren yedek güç kaynağı.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# Firmware
- kelime kökü: firm (firma) + ware (mal, eşya)
- Donanım parçası içerisinde bulunan salt okunabilir yazılım. Teorikte sadece salt okunur olması beklenmektedir. fakat pratikte güncelleme yapılabilmesi için yazılabilir olarak tasarlanabilirler.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# PATA (or Parallel ATA or IDE)
Anakart ile diskler (HDD, dvd/cd gibi) arasındaki veri yolu bağlantı tipidir.

# SATA (or Serial ATA)
PATA'nın üzerine kurulu daha yeni ve hızlı teknolojidir.

# AHCI (or Advantec Host Control Interface)
SATA desteği olan anakartlar ile sadece HDD arası veri yolu bağlantı tipidir.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# Original Equipment Manufacturer (or OEM or orijinal ürün üreticisi)
Başka bir firmanın satacağı ürün için ekipman/parça imalat eden firmaya OEM denir. örneğin;
- Microsoft Windows, HP laptoplarında yüklü gelir. Burada OEM Microsoft oluyor.
- Ford marka bir araba aldığımızda içindeki cd player sony'nin oluyor. sony burada OEM oluyor. 

Bazı bilgisayar satan firmalar (örnek X-firması) OEM ürünlerini sadece birleştirerek satar. Bunu yaparken sattıkları ürünün her parçası OEM firmalarına ait oluyor. X-firması bu parçaları toplu satın alırken kutusuz satın alıyor çünkü kutular lojistik/kargo/depo maliyetini yükseltiyor. X-firması, toplu alınan bilgisayar parçaların bir kısmını bazen tek tek de satabiliyor. Bunları sattığı zaman kutusuz satmak durumunda kalıyor.

OEM'li bir ürün, yada kutulu bir ürün farklı servis/destek/ek-parçalar ile birlikte satılabiliyor. Örneğin; daha uzun yada daha kısa garanti süreli, destek hizmeti olmadan, ekipman parçaları olmadan gibi. Fakat asıl ürününü kendisi tamamiyle orijinal'dir.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# OLED (or organic light-emitting diode)
OLED cihaz ekranlarında kullanılan bir teknolojidir. Bu teknolojide her pixel bağımsızca parlatılır. Bu sebeple tamamen siyah olan pixeller aydınlatılmaya ihityacı olmaz. Bu OLED ekranlı bir cihazda, sebeple siyah temalı görüntülerde cihazın pil ömründen kazandırır. Tabi bu tek parametre değil. Örneğin hem beyaz hem siyah kullanmak ve bunlar arasında sık geçiş yapmanın daha çok pil tükettiğini de idda edenler var.

AMOLED (active-matrix organic light-emitting diode), OLED'in bir türevidir.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# plc
2 input'u ve 2 output'u olan bir device örneği:

```
  =====I0=====I1======

  ====================

  ===  SIEMENS PLC ===

  ====================

  =====Q0=====Q1======
```

- PLC'nin içine programımızı attığımızda gelen inputlara göre çıktılara 1 ve 0 ları yönlendirecektir. Girişlerdeki clock pulse'a göre her daim yazdığımız kodlar tekrar tekrar işletilecektir.

- Girişimiz birçok input'u olabilir. özellikle bayt girişlerine çok ihtiyaç olduğundan kare olarak dikdörtgen şeklinde girişlerimiz olabilir. örnek: 50x8 lik bir dikdörtgenimiz olabilir. 50 bayt anlamına geliyor. her giriş bir bit'i temsil eder.

- Cihazın girişleri ve çıkışları 24 volt oluyor (çoğunlukla). Bu sebeple direk olarak çıkışımızı güç isteyen bir kaynağa (örnek motora) bağlayamayız.

- PLC'ler özellikle otomasyon sistemlerinde kullanıldığından titreşimlere, darbelere, ve sıcak soğuk gibi hava koşullarına dayanıklı üretilmektedirler. En azından aurdinio gibi cihazlara göre çok daha dayanıklı.

## programlama dilleri

birçok  yötem ile programlama yapılabilir:

- Ladder (or Merdiven) Diyagramı
Elektrik devreleri bilgisi olanlar tercih eder.

örnek:
```
  -----| I0 |------------| Q1 |----
                |
                |
                |
  -----| I1 |----
```

Yukarıda input0 veya input1'imiz 1 olursa ancak quit1'imiz 1 olacaktır.

Bu gibi birçok programı tanımlayıp, plc'nin içine atabiliyoruz. PLC çalıştığında bunların tümünü sırası ile tekrar tekrar işletecektir.

## Statement List Editor (or STL)
Programlama dili bilenler tercih eder.

örnek:

```
LD I0
AND
LD I1
```

## Function Block Diagram (or FBD)
Elektronik (logic kapılar) bilgisi olanlar tercih eder.

örnek:

```
   IO ------------

         |  OR   |-----------Q1

         |       |

   IO ------------
```

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# sleep vs Hibernate vs others

- sleep (or Stand By or Suspend or Suspend to RAM or uyku) ile işletim sistemi tüm uygulamalrı pause eder ve sistemin az enerji harcamasını sağlar. sistem kapanmaz. bu sebeple saniyeler içerisinde devam edebilir.

- Hibernate (or Suspend to Disk or hazırda beklet), sleep ile aynı mantıktadır. fakat sistemi tamamiyle kapatabilmek için RAM'deki bilgileri harddiskte saklar. açılması zaman almaktadır.

- Hybrid Sleep (or Suspend to both) modunda kullanıcı logout edilir. sadece işletim sistemi ve servisleri Hibernate edilir. Microsoft Windows, 8 ve sonrası sürümlerde "shut down" işlemi ile "Hybrid Sleep" uygulamaktadır. gerçek bir sistem kapanması için "restart" işlemi yapılmalıdır. Microsoft Windows ayalarında "fast startup" (or Fast Boot) isimli bu özellik devre dışı bırakılabilir.

  Bazı işletim sistemlerinde "hybrit Sleep" aynı işlevi yapmamaktadır. Bazı sistemlerde şu yapılıyor: Sistemdeki tüm uygulamalar pause ediliyor (sleep'te olduğu gibi). RAMdeki veriler Hibernate'deki gibi HDD'ye saklanıyor. RAM'deki veriler silinmiyor. aynen bırakılıyor. Yani sleep moduna ekstradan RAM'deki veriler HDD'de de saklanmış oluyor. Bu şekilde; makina aksi bir durumda kapanır ise en kötüsü Hibernate tarzı bir açılış yapıyor. Eğer sistem kapatılmamış ise, sleep gibi hılı açılıyor.

- Connected Standby (or InstantGo) mobile cihazlarda görülen bir yöntemdir. masaüstlerine çok sonradan gelmiştir. sleep ile aynı mantıktadır. tek farkı, ek olarak; isteyen uygulamalar internet ağını kullanacak kod bloklarını sürekli arkaplanda çalıştırabilmeleridir.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# özet boot süreci

- BIOS (eski süreç)

> BIOS ----(HDD)----> MBR ----> bootloader ----> os

- uefi sonrası yeni süreç:

> UEFI ----(HDD)----> bootloader ----> os

- uefi sonrası, BIOS uyumlu kurulmuş bir disk üzerinde işletim sistemini başlatma:

> UEFI ----(HDD)----> MBR ----> bootloader ----> os

# Uyku ve diğer kapanma metotları sonrası boot süreçleri nasıl değişiyor

Uyku'ya alınan cihazın açılması firmware'den itibaren olmuyor. Sistem hiç kapanmamış olduğu için direk olarak işletim sistemi devam ediyor.

Hibernate işleminde işletim sistemi normal kapanma metotunu uyguuyor. Açılıştada normal açılma süreci işleniyor. İşletim sistemleri otomatik olarak son durumunu algılayıp, Hibernate edilmiş ise dosyadan RAM'e aktarım yapıp devam ediyor. Eğer hibernat edilmemiş ise; normal olarak açılıyor. Boot sürecinde bir değişiklik söz konusu değil.

# MacOS boot işlemi
Apple, EFI'yi ilk kullanan şirketlerden biri. 2005 yılında, Apple Intel işlemcilere geçiş yaptığında klasik BIOS yerine EFI kullanmayı tercih etmişti. Yıllar sonra, UEFI spesifikasyonu sayesinde tüm PC'lerde UEFI kullanılmaya başlandı ve bu bir standart haline geldi. Mac'lerde şu an Apple'ın kendine göre uyarladığı bir EFI bulunmakta. Mac'lerdeki firmware tıpkı normal PC'lerde olduğu gibi UEFI ve Legacy modda işletim sistemi boot edebilir. Ancak Apple'ın yaptığı düzenlemeler olmadan MacOS önyüklenemez.

# CSM (or Compatibility Support Module)
UEFI'nin 'BIOS compatibility mode'una verilen özel isim. UEFI devre dışı bırakılamaz. UEFI MBR-tarzı bölümlü HDD'lerden işletim sistemi açabilir. Bu da UEFI'nin geriye uyumlu çalıştığı anlamına gelir. Fakat CSM, her UEFIde olmak zorunda değildir.

# BIOS (or Basic Input Output System)
- Bir firmware'dir.
- BIOS anakartın üstündedir.
- Makina baslatildiginda hangi aygıttan (cd, dvd, HDD, USB gibi) boot edileceğini belirler.
- HDD ile baslatilirsa; HDD'nin ilk sektörünü okur. Burada okuduğu kismi execute eder. Execute edilen bu bölge MBR (Master boot record) olarak adlandirilir.

# MBR (or master boot record)
iki kisimdan olusur:
- Master Boot Code --> execute edilebilir olan kisim.
- Master Partition Table --> HDD için bölümlerin haritasi. en çok 4 bölüm tutabilir. bu sebeple 4 bölümden (birincil bölüm veya primary partition) fazlaya ayirmak gerekirse, hardiskki "genisletilmis bölüm (extensable partition)" özelliğinden yararlanılır. genisletilmis bölüm en fazla 1 adet olabilir. fakat altinda sinirsiz bölüm barindirabilir. altinda olan her bölüme "mantiksal bölüm (logical partition)" denir.

# bootloader
- MBR tarafindan execute edilebilen bir sistemdir. bu sistem ile isletim sistemleri baslatilir.

- her isletim sisteminin bootloader dosyalarını bir yerde saklaması gereklidirki MBR o dizini okusun ve execute etsin.

- bu dizin Ubuntuda varsayılan olarak /boot/grub'tur. bu dizinin Ubuntu'da, baslatilacak islemim sistemi ile ayni bölümde olma sarti yoktur. örnegin /boot/grub, /dev/sda9'da iken, Ubuntunun tüm dosyalari /dev/sda5'te olabilir. eger bölümleri ayirirsak, Ubuntu'yu sildigimizde Grub sistemi de silinmeyecegi için HDD'de kurulu diğer işletim sistemleri hala başlatılabilir olacaktir. fakat Grub, Ubuntu ile ayni partition'da olursa, Ubuntu partition'u silindiginde (or formatlandığında), Grub başlamayacagı için HDD'de kurulu diğer işletim sistemleri de baslamayacaktir.

- Microsoft Windows'un bootloader'ı "Microsoft Windows Boot Manager (BOOTMGR)" olarak isimlendirilmektedir. Dosyaları; "System Reserved" isimli partition'da durmaktadır.

- herhangi bir işletim sistemi HDD'ye kuruldugunda, MBR dizini üzerinde degisiklik yapar. bu degisiklikler:

  - MBR içine hangi bölümün master boot (active) oldugu yazilir. yani; hangi bölümdeki bootloader'in baslatilacaginin adresidir. (her partition altinda bootloader olabilir, ama sadece 1 tanesi baslayacaktir). işletim sistemi kurulumunda yeni bir bootloader kurulmayacak ise bu işlemin yapılmasına gerek yoktur.

  - Grub normal koşullarda MBR alanına kurulur. fakat MBR alanı çok küçük olduğundan, Grub kendini 2 parçaya böler. bir kısmı MBR içinde, 2inci kısmı farklı bir (boot flag'inin olduğu) partition'a saklanır. 2-stage bootloader kavramı burada ortaya çıkmıştır. normal koşullarda MBR'nin içindeki executor, ext4 dizinini okuyamaz. Ubuntuda Grub dosyaları ext bölümünde dururur. MBR'nin Grub'u çalıştırması için ext dosys sistemini tanıması lazım. işte bu ext-tanıma kısmı modülü 1inci stage bootloader kısmı ile çözülmüş oluyor.

- Microsoft Windows, her kurulumdan sonra sürekli MBR'yi kendi bootloader'ına yönlendirir. Microsoft Windows'un bootloader'ı diğer işletim sistemlerini zaten tanımaz. bu sebeple her Microsoft Windows kurulumu sonrası, liux ve diğer işletim sistemler ile Grub'u tekrar kurmak gerekmektedir.

# fixmbr
Microsoft Windows'un komut satırı uygulaması. bu komut ile MBR tamamen sıfırdan değiştirilmektedir. fixmbr komutu sonrası Microsoft Windows kendi bootloader'ına yönlendirme yapacak şekilde MBR'yi yeniden yazmaktadır.

# ntldr
Microsoft Windows NT için bootloader'dır. günümüzde tamamen yeniden tasarlandığı için artık kullanılmamaktadır. Yeni tasarım Microsoft Windows Boot Manager (BOOTMGR) üzerinedir. BOOTMGR başladığında eski bir Microsoft Windows sürümü seçilirse, BOOTMGR, ntldr'yi başlatmaktadır.

# GRUB (or GRand Unified Bootloader) vs GRUB2
Grub yazılımı 2inci sürümünde neredeyse sıfırdan tasarlandı. Bu yüzden çoğu yerde farklı yazılımmış gibi algılanmaktadır. Oysa Grub2, Grub'un güncel sürümüdür. Grub'un eski sürümüne "GRUB Legacy" adı da verilir. "Grub legacy" sadece BIOS-uyumlu bölümlendirmeleri destekler.

# SYSLINUX
NTFS veya FAT32 dosya sistemlerine kurulu Linux başlatmak için gerekli bir bootloader çeşididir.

# LILO (or LInux LOader)
Bir BIOS uyumlu bootloader çeşididir. Daha sonra UEFI'ler için ELILO isminde bir türevi çıkarılmıştır.

# OS-Loader
bootloader, ismi gereği, genel bir terimdir. MBR'nin içindeki sistemde, MBR'nin başlattığı sistemede aslında bootloader denilebilir. çünkü sistemi boot/load ediyorlar. bu sebeple bazı insanlar, günümüzdeki sistemelere "2 stage bootloader" olarak varsayıyor. 1'inci stage: MBR bootloader'ının execution'u. 2'inci stage ise: GRUB, BOOTMGR gibi yazılımların execution'udur. dolayısı ile bir makalede; MBR'ye bootloader yazınca, 2inci aşamaya OS-Loader diyen kaynaklar olabiliyor.

# UEFI (or Unified Extensible Firmware Interface or old-name:EFI)
Yeni gelen bir sistemdir. BIOS'a alternatif bir firmwaredir. UEFI her konuda çok daha gelişmiştir diyebiliriz. Sadece süreç olarak bakıldığında; MBR gereksinimi ortadan kalkmıştır. Bakınız: "özet boot süreci".

Bazı UEFI Arayüzlerinde "BIOS" kelimesi görülebilmektedir. Bunun sebebi BIOS tabanlı sistemler üzerinde ekstra modül olarak UEFI kullanılmasıdır.

# UEFI boot manager
Bağlı olan tüm diskler içindeki tüm başlatılabilir sistemlerin (işletim sistemi, bootloader, MBR) listesini tutar ve bunlara ekleme/çıkarma/değişiklik yapılmasını sağlar. kısmen Grub'un görevini görmektedir diyebiliriz. listenin veritabanı anakartın içindedir. Bu listedeki öncelik sırasına göre, anakartı üzerinde olan UEFI ilgili sistemi başlatacaktır.

Bu liste dışardan düzenlenebilmektedir. Örneğin Linux'ta "efibootmgr" uygulaması bunu yapıyor. Her işletim sistemi, kurulumunda bu listeye ekler yada siler yada düzenler. Aynı şekilde anakarttaki UEFI yazılımı GUI'si ile son kullanıcı manuel de ekleme/silme/değiştirme yapabilir.

Listenin içinde BIOS-uyumlu bölümlerde olabilir. Çünkü UEFI, geriye uyumlu; yani; BIOS uyumludur.

örnek bir "efibootmgr" komut satırı çıktısı (her satırın açıklaması aşağıdasında yazıyor):

> BootCurrent: 0002 

şu anda OS'u başlatmak için kullanılmış olan boot

> Timeout: 3 seconds

aşağıdaki liste PC açıldığında görüntülenir. 

> BootOrder: 0003,0002,0000,0004

boot deneme sırasını temsil eder. biri açılmazsa diğerini açmaya çalışır.

> Boot0000# CD/DVD Drive  BIOS(3,0,00)

BIOS kelimesi, eski BIOS uyumlu açılışı temsil eder.

\# (yıldız karakteri) bu kaydın aktif olduğunu belirtiyor

> Boot0001# Hard Drive    HD(2,0,00)

HDD'yi aç anlamına geliyor. özellikle partition belirtmemiş. bu durumda UEFI native mod'da HDD yi açar. GPT bölümlü olan bu HDD içerisinde, UEFI partition'unu bulur. "Fallback path mode (or fallback mode)" denir buna. yani; native uefi mode (BIOS değil) fakat HDD karar veriyor hangi partition'un açılacağına. detaylar için ESP ile ilgili başlıklarına bakınız.

> Boot0002# Fedora        HD(1,800,61800,cb3e-4727-8fed-5ce0c040365d)File(\EFI\fedora\grubx64.efi)

uefi native mode partition belirtilmiş. ".efi" uzantısı UEFI firmware'nin execute edilebilir bootloader dosyası uzantısıdır.

> Boot0003# opensuse      HD(1,800,61800,cb3e-4727-8fed-5ce0c040365d)File(\EFI\opensuse\grubx64.efi)

>  Boot0004# Hard Drive    BIOS(2,0,00)P0: ST1500DM003-9YN16G

HDD yi aç der. özellikle partition belirtmemiş. fakat BIOS uyumlu olsun demiş. bu durumda HDD içerisinden MBR yi okur eskisi gibi. Yukarıdaki Boot0001'da, UEFI geri uyumlu modda olmadığı için GPT'yi okumuştu. Burada ise MBR okunacak.

Bazı bilgisayarlarda efibootmgr ile yapılan işlemlerde hata almasakta, yapılan işlemin etki etmediğini görebiliriz. bunun sebebi boot option'larının cihaz tarafından hardcode tanımlanmış olmasıdır. böyle durumlarda; bootorder'ı takip edip, /EFI altında istenmeyen dizinlerin önüne saçma prefixler verilebilir. yukarıdaki örnekten gidelim: bootorder 0003 opensuse'yi açacak. eğer opensuse'yi istemiyorsak ve efibootmgr yazılımı etki etmiyor ise; /EFI/opensuse dizinini silebiliriz yada /EFI/\_opensuse olarak rename ederiz. bu şekilde yedeğini almış oluruz.

# Secure boot
- UEFI ile gelen bir özellik. manuel olarak devre disi birakilabilmektedir. açılacak olan işletim sisteminin bootloader'ının anahtarının, UEFI içerisindeki anahtarlarla uyuşması gerekiyor.

- Bu sistemle rastgele bir kullanıcının USB'den istediği gibi işletim sistemini çalıştırması engellenmiş oluyor.

- Makine ile kurulu gelen işletim sistemlerinin anahtarı UEFI içerisine kaydedilmiş oluyor.

- Microsoft, Microsoft Windows'un anahtarını bazı farklı işletim sistemleri firmalarına da veriyor (örneğin Fedora). Bu şekilde o makinada, güncel Fedora ISO'su ile direk işletim sistemi başlatılabiliyor oluyor.

# UEFI based botloaders
UEFI firmware, direk olarak bootloader'ı çalıştırır. BIOS tabanlı sistemlerde ise, MBR bootloader'ı çalıştırırdı. UEFI çok daha gelişmiş oluğundan execute ettiği bootloaderda daha gelişmiştir. Farklı executable dosyası çalıştırırlar. Bu sebeple bootloader'larda kendilerini güncellemişlerdir. Eğer HDD içerisinde sadece UEFI'nin execute edebileceği bootloader var ise; aynı HDD BIOS'lu anakartlarda işletilemeyecektir.

# Volume Boot Record (or VBR or volume boot sector or partition boot record or partition boot sector)

MBR çok ufak oldugundan, tüm detaylari üzerinde tutmak mümkün değildir. bu sebeple her mantiksal ve birincil bölümün başında VBR olur. VBR'ler de MBR'ler gibidir. bölüm bilgilerini daha detayli şekilde tutarlar.

# GUID Partition Table (or GPT)

- UEFI'nin tanıdığı, MBR'ye göre çok daha gelismis bir bölüm tutma semasidir.

- eski BIOS-MBR uyumlu bölümlendirmelere "msdos partition table" adı verilir.

- GPT bilgileri diskin en başındadır. GPT olan bir HDD'de MBR'de vardır. MBR bölümü her zaman bırakılır. Bu şekilde geriye uyumluluk sağlanmış olur.

- GPT olarak tasarlanmış bir diski makineye taktığınızda BIOS anakartlar ile buradaki işletim sistemlerini başlatamazsınız. Fakat burada yanlış anlaşılma olmasın: Sadece işletim sistemi boot edemezsiniz. Onun dışında, bir işletim sistemi yürütülür durumdayken, GPT bölünlenmiş HDD'yi mount edip, hem Microsoft Windows hemde diğer tüm işletim sistemleri ile okuyup yazabilirsiniz (default olarak işletim sistemi okuyamasa bile üçüncü parti uygulamalarla yapılabilir). Çünkü HDD'yi okuyan bir yazılımdır. BIOS değil. Yani işletim sistemi boot etmekle, HDD'yi sadece data olarak kullanmak tamamen ayrı kavramlardır.

# Microsoft Windows recovery partition
- Bu bölüm Microsoft Windows yüklemesi sırasında otomatik oluşturuluyor.

- Bölüm winRE dosyalarını içeriyor. WinRE Microsoft Windows kurtarma işlemlerini yapan bir yazılım.

# ESP (or EFI System Partition or EFISYS)
-Diskte varolan işletim sistemlerinin EFI dosyaları (bootloader'ları) + Bootloader için gerekli sistem sürücüleri (driver) dosyaları bu bölümdedir.

- FAT32 olmak zorundadır. FAT16 olması UEFI implemementasonunda yazmaktadır. Fakat Microsoft Windows işletim sistemi fat16 olması durumunda sorun çıkardığı için, artık her yerde FAT32 kullanılmaktadır.

- boyutu değişkendir. Örnek boyut: Ortalama 40 MB sadece Microsoft Windows-10 ve Ubuntu yüklü bir makine için yeterlidir. Fakat İlerde yapılabilecek ek işletim sistemi kurulumlarının EFI dosyaları için bu bölümün boyutunu yüksek tutmakta yarar var.

- \EFI dizini altında her işletim sisteminin kendi bootloader'ı ayrı dizinlerde mevcuttur. \EFI\BOOT dizini HDD "fallback mode" ile yürütüldüğünde devreye girer. Yani; UEFI, hiçbir partition belirtmeden HDD'yi boot ettiğinde, UEFI, ESP bölümünü bulur. Daha sonra içerisinde \EFI\BOOT\BOOTx64.EFI (or standrat önceden belirlenmiş farklı bootloader path'leri) dosyasını execute eder. Yani işletim sistemlerinin bootloader'ları dışında genel bir UEFI arayüzü (bootloader'ı) mevcuttur. Bu bootloader "default bootloader" olarak da adlandırılmaktadır. Bazı UEFI firmware'leri bu bootloader'ı bulamadığı zaman Microsoft Windows'un default bootloader'ını da açmayı denemektedir: EFI/Microsoft/BOOT/bootmgfw.efi.

- \EFI dizini altında sürücüler ve işletim sistemi çekirdekleri de mevcuttur. EFI dosyası executable'ı olarak Linux çekirdeği çalıştırılabiliyor. Linux güncel sürümleri bunu desteklemektedir. Bu özellik; EFI Boot Stub (or EFI Stub) olarak isimlendiriliyor.

- \EFI altında aynı zamanda sürücü (driver) dosyaları bulunmaktadır. Sürücüler: dosya dizinlerine erişim sürücüleri (EXT, NTFS gibi), network cardlar'ın daha geniş özelliklerle kullanılabilmesini, bootloader sırasında takılan exernal USB cihazların tanınması gibi işler için gerekli olabilmektedirler.

# MSR (or Microsoft System Reserved Partition or Sistem ayrıldı bölümü)
- sadece GPT disklerde oluşan bir bölümdür.

- ESP'den sonra ve Microsoft Windows kurulu bölümden önce olmak zorundadır.

- Microsoft Windows sürümüne göre dosya sistemi formatı NTFS yada FAT32 olabilir.

- Boyutu Microsoft Windows sürümü ve disk boyutuna göre değişebilir.

- Bootmgr bu bölümde yüklüdür.

# Redundant Array of Inexpensive Disks (or Redundant Array of Independent Disks or RAID)
- Birden fazla diski tek bir disk gibi gösterme özelliğidir.

- RAID kendi içeirisinde birçok özelliği vardır: RAID0, RAID1 gibi... Bunlardan sadece bir tanesi sçeilmek zorundadır.

  - RAID0: 2 diskimiz var. 2 disk tek bir disk gibi gösteriliyor. 2 tarafta da farklı bilgiler tutuluyor. performans artışı sağlıyor. çünkü bazı durumlarda iki diskten ayrı ayrı dosyaları aynı anda okuyabiliyor. tek diskte olsaydık aynı anda bir dosya okuyabilecektir.

  - RAID1: 2 diskimiz var. 2 disk tek bir disk gibi gösteriliyor. 2 tarafta da aynı bilgiler tutuluyor. Bu eşkilde birine bir zarar geldiğinde diğerinden devam edilebiliyor. Performans açısından kötü.

- Sadece Donnanımsal yada sadece yazılımsal çözümlerle sağlanmaktadırlar.

# Flag (Bayrak)

GPT ve MBR her partitition için bir bayrak bulundururlar. Bayrakların birer anlamı vardır.

- boot: tüm HDD de sadece bir bölümde bu set edilebilir. ilk o bölümün boot edileceği anlamına gelir. MBR sistemlerde çalıştırılacak bootloader'ın olduğu bölüm iken, GPT istemlerde EFI kurulu bölüme atanmalıdır.

- Diag: o bölümün diagnostics/recovery amaçlı kullanıldığını belirtir.

- Hidden: Microsoft otomatik mount edilmesini istenmediği bölümlere bu bayrağı atıyor.

- RAID: raid teknoloji için kullanılan bir bölüm olduğunu gösterir

- Msftres: sadece GPT'de disklerin içindeki bölümlerde mevcuttur. bölümün "Microsoft Reserved partition" olduğunu gösterir.

- msftdata: Microsoft kendi oluşturuduğu dizinlere bunu atıyor. bazı Linux sistemleri de kendi dizinlerine bu flag'i attığı görülüyor.

- Swap: HDD üzerinde kurulu tüm Linux sistemler bu bölümü swap alanı olarak kullanabileceklerini belirtir.

- BIOS_GRUB: GPT Kurulu bir HDD'de, sadece "Grub legacy"'nin kurulu olduğu bir bölüm var ise, o bölüme bu bayrak atanır.

- legacy_boot:  GPT yapılı disklerde, SYSLINUX botloader'ın bulunduğu bölüme atanmaktadır.

# Partititon name vs partition label
- name, GPT alanında olan bir etikettir.

- label ise partition'un içinde olan bir etikettir.

# Gparted
- Linux üzerinde çalışan, GUI içeren bir disk yönetim aracıdır. gparted komut satırı "(GNU) parted" uygulamasının önyüzüdür.

# fdisk
"Parted" uygulaması ile aynı görevi gören komut satırı uygulaması.

# Gparted anahtar icon'u
- her partition'un yanında bu icon olabilir. bu icon o partition'un mount edilmiş olduğu ve bu sebeple üzerinde işlem yapılmasına izin vermeyeceği anlamına gelir.

- anahtar işaretli bir bölüm üzerinde işlem yapmak için o bölüm önce unmount edilmelidir. eğer ilgili bölüm, çalıştırılan işletim sistemi dosyalarını içerior ise unmount edilemez. böyle bir durumda ilgili bölüm ancak canlı cd üzerinden, yada aynı HDD üzerinde farklı bir bölümdeki işletim sistemi çalıştırılarak yapılabilir.

# bootable USB creators

| name                                         | runs on              | allowed ISO types | note                                                                |
|----------------------------------------------|----------------------|-------------------|---------------------------------------------------------------------|
| Unetbootin                                   | cross-paltform       | Linux-based       | open source                                                         |
| Rufus                                        | Microsoft Windows              | any               | open source                                                         |
| WinToUSB                                     | Microsoft Windows              | Microsoft Windows           | closed source                                                       |
| WinUSB                                       | ?                    | Microsoft Windows           | fork fake app                                                       |
| WoeUSB                                       | Linux                | Microsoft Windows           | open source                                                         |
| MkUSB                                        | Linux (command line) | Linux             | ?                                                                   |
| Etcher                                       | any                  | any               | (read below)                                                        |
| LinuxLive USB Creator                        | Microsoft Windows              | Linux             | writes open source but code is not available                        |
| YUMI (or Your Universal Multiboot Installer) | Microsoft Windows              | any               | multi ISO on one USB feature. source code is available on Zip file. |
| UUI (or Universal USB Installer)             | Microsoft Windows              | any               | source code is available on Zip file.                               |
| USB-creator (or Startup Disk Creator)        | Ubuntu,Microsoft Windows       | Ubuntu            | Ubuntu pre-installed app                                            |
| Microsoft Windows USB/DVD Download Tool                | Microsoft Windows              | Microsoft Windows           | ms official app                                                     |
| MultibootUSB                                 | Microsoft Windows, Linux       | any               | open source                                                         |
| Ventoy                                       | ?                    | ?                 | open source (read note)                                             |

note: Ventoy diğerlerinden farklı olarak USB'yi bootable hale getiriyor. boot edildiğinde çalışan uygulama USB dis içerisinde özel bir dizini tümüyle tarıyor. Bulduğu ISO'ları direk boot edebilmemizi sağlıyor. Yani ISO'yu tüm diske baskmıyoruz. ISO yu elle kopyalıyoruz. birden fazla ISO da atabiliriz.

# Etcher vs balena-etcher
Etcher isim değişikliği ile Balena-etcher (or BalenaEtcher) olmuştur.

Etcher, Electron üzerine kurulu, ISO dosyasını tümüyle byte byte USB medyaya basmaktadır ve distro-spesifik configürasyonlara izin vermemektedir. bu sebeple Microsoft Windows gibi ISO'larda başarı sağlayamamaktadır.

# Microsoft Windows To Go
Microsoft Windows 8 ile gelen bir özellik. sadece enterprise edition'larda mevcut. artık Microsoft Windows USB'ye de kurulabiliyor. bazı USB cihazları bunu destekleyebiliyor.

# Remastersys
desteği biten bir yazılım. çalışmakta olan Linux sistemini, o haliyle ISO haline getirmeye yarıyor.

# mount point
bir partition işletim sisteminde bir dizinden erişilmek zorundadır. örneğin Microsoft Windows'ta her partition en tepedeki dizinden ayrılır. oysa POSIX'lerin tümünde istenilen dizinden istenilen partitiona erişim sağlanır. bu bağlama işlemine "mounting" adı verilir ve bağlanan dizin adresine de "mounting point" adı verilir.

# logical drive (or volume) 
bilişimde kullanılan "volume" kelimesinin Türkçesi yok.

volume şu anlama gelmektedir: hacim, yoğunluk, yığın. bunlardan bağımsız olarak "ses kuvveti" anlamına da gelmektedir.

bilişimde volume birden fazla partition'u barındırabilen özel bir bellek alanını temsil etmektedir.

# drive (or sürücü)
fiziksel bellek alanını temsil eder. örnek: HDD, USB, floppy, cd.

# partition (or bölüm)
her partition sanaldır.

# Linux boot parameters
grup ekranında Linux çekirdeği başlamadan önce ona parametre geçebiliriz. örnek parametreler:

- acpi=off : ACPI yönetimini devre dışı bırak

- noapic  : APIC desteğini devre dışı bırak

- nolapic  : Yerel APIC desteğini devre dışı bırak

- edd=on  : EDD desteğini etkin kıl

- nodmraid : Yazılımsal RAID özelliğini devre dışı bırak

- quiet: Linux'un output'a log'lamamasını sağlar. quiet disable bırkılırsa, Linux output'a log'ları basar.

- splash: Linux boot olurken ekranda logo görünmesini sağlar. eğer splash açık ise quiet'ın önemi olmayacktır. quiet vs splash birlikte kapatılmalıdır ki log'lar ekranda gözüksün.

- nomodeset: ekran kartları ile ilgili sorunlar yaşandığında kullanılan bir seçenektir. sistem başlayana kadar (X (pencere yöneticisi) başlayana kadar), video sürücülerinin devre dışı bırakıp kernel'deki video modunun kullanılmasını sağlar. nomodeset; __kernel mode setting (or KMS)__yi disable eder.

Bu seçeneklerden birini uygulamak için:

- grup ekranında Linuxu başlatmak için seçeceğimiz satır'da enter tuşuna basmadan önce "e" tuşuna basarız. o satırı düzenlemeyi açar. 

> Linux	/boot/vmlinuz-4.15.0-45-generic root=UUID=86e0d3db ro  quiet splash $vt_handoff

yukarıdaki satırın sonuna istediğimiz parametreyi ekleyebiliriz ve F10 ile başlarız. bu düzenleme sadece o oturuma mahsus olacaktır. bu işlemi kalıcı hale getirmek için:

- /boot/grub/grupcfg dosyamızı düzenlememiz gerekmektedir. fakat grupcfg dosyası her Linux update'i sonrası, yeniden oluşturuluyor. bu sebeple bu dosya kalıcı bir çözüm değil.
- /etc/default/grub dosyasının düzenlenmesi gerekli. her Linux kernel update'i sonrası, bu dosyadaki config'ler okunarak, grupcfg dosyası oluşturuluyor.

# update-grub vs "grub-mkconfig -o /boot/grub/grub.cfg"
ikiside tamamen aynı görevi görüyor. update-grub sadece bir wrapper.

Grub menü dosyasını default configurasyonlara göre re-generate ediyor. 

# update-grub vs grub-install
update-grub sadece menü dosyasını tekrar oluştururken, grub-install tüm Grub sistemini sisteme yüklüyor.

# update-grub vs update-grub2
bu 2 komut birbirine link ediyor. Grub2 çıkınca update-grub2 komutu çıktı, fakat update-grub her 2 grub sürümünü de update edebiliyor.

# Nouveau
name of open source Nvidia driver
