
############################

############################
# PATTERN DOMAIN DRIVEN DESIGN
############################

############################

# Kitap
DDD ilk olarak Eric Evans tarafından "Domain-Driven Design: Tackling Complexity in the Heart of Software" kitabında, 2003 yılında ortaya atılmıştır. Daha sonra, 2014'te Eric, tanımların referanslarını kısaca yazdığı "Domain-Driven Design Reference: Definitions and Pattern Summaries" isimli kitapta özetlemiştir ve çok ufak eklemeler yapmıştır.

DDD kitabında birçok öneri/pattern'den bahsedilmektedir. Bunun yanında; 
- continuous integration
- Refactoring
- Clean&Readable Code
- Factory sınıfları
- takım çalışmasının önemi
- side effect free functions

gibi konuların önemlerine bir kez daha bu kitapta özellikle değiniliyor. zaten çoğu bilgi kitap ilk yazıldığında piyasada bilinmiyordu. Bu konular DDD çalışması içinde temel oluşturduğu için bu konularda kitapta yer almıştır. 

# ne zaman kullanılmalı
Büyük çapta ve business logic'in kapsamlı ve kompleks olduğu uygulamalarda kullanılması tercih edilen bir yaklaşımdır.

# ubiquitous language
Domain expert'leri ve yazılımcılar ortak isimlendirme kullanmalıdır. isimlendirmeler teknik değil; domain uzmanlarının verdiği isimler olmalıdır. Bu sebeple bu isimlendirmeye "ubiquitous language" (ubiquitous kelime anlamı: yaygın) adı verilmiştir.

# Domain-driven design (or DDD) vs data-centric design (or database-centric design or data-driven design)
DDD'yi anlamak için __data-centric design__ ile karşılaştırmak verimli olacaktır. Çünkü DDD, __domain-centric design (or domain-driven design)__ mantığı ile iş geliştirmeyi yapmamızı savunur.

Program yazarken önceliği hangi katmana vereceğimiz önemlidir. DDD, merkezde domain'i barındırırken, data-centric yapıda ise merkezde data vardır. DDD, önce domain modellerini çıkarılıp, daha sonra kalıcı veri yapısı (data) kısmı tasarlanmasını tavsiye eder. Domain ve persistence DB'deki tablolarımız farklı olabilir. Domain tarafında bu DB'den hiç habersiz (__persistence ignorance__) geliştirme yapılmalıdır. Domain business'i geliştirilirken, domain modelleri üzerinden konuşulmalıdır. Oysa data-centric yapıda; data'lar business ile içiçe karışmış olmasa bile (yani; iyi bir dizayn yapılmış olsa bile), uzun zaman sonra data'ya göre business akışı uyarlanabiliyor. Örneğin; 

- 1- Geliştirdiğimiz yazılımda, "Product" tablosunun 3 farklı feature sütunu olsun: F1, F2, F3. Bunun yerine "feature" tablosu yapıp, her product'ın özelliklerini burada tutabiliriz. Her product'ın özelliksini de, feature-tipi (F1, F2, F3 değeri alabilir) ve feature değeri şeklinde tutabiliriz.

- 2- data-centric bir yapıda NoSQL veritabanı kullanmış ve denormalizasyonları yaptığımızı varsayalım.

Yukarıdaki 2 madde DB tarafında verimli bir çözüm olsa da, bu kısmın domain tarafında hiç bilinmemesi gerekiyor. İşte DDD bu yönelimin olmaması için mimarisel öneriler sunuyor. Çünkü yazılımın temel ihtiyacı domain'e hizmet vermektir. DDD'de konular çok keskin bir şekilde ayrılmış değil. Yani şu, şu şekilde yapılacak, yoksa DDD olmaz diye öneriler mevcut değil. DDD sadece bir dizayn yaklaşımıdır.

Yukarıdaki maddeleri şuradan çıkarabiliriz: book: "Patterns, Principles, And Practices Of Domain-Driven Design", authors: "Scott Millett" and "Nick Tune", title: "Domain Model Implementation Patterns", subtitle: "domain model", 63 page, 1st paragraph.

Bazı domainlerde (örneğin; metric/istatistik, yapay zeka sistemlerinde) DDD yerine data-centric mimariler kullanmak daha verimli olabiliyor.

# business katmanı VS repository implementasyonu (persistence katmanı)
DDD kitabında repository'lerin sadece aggregate root'ları üzerinde işlem yapması gerektiğinden bahsedilmiş. Bazen bazı kod bloklarının repository implementasyonlarımızda mı, yoksa business logic'lerin olduğu servislerde mi olacağı karışmaktadır. Örneğin bir data'yı silmeye kalktığımızda, önce onunla bağlantılı data'ları silmemiz gerekmektedir. İşte bu kod bloğu repository tarafında olmalıdır. Burada şöyle düşünmek lazım: Eğer ki; database tarafında çok farklı bir yapı kullanıyor olsaydık, bu kod bloğu değişecekmiydi? Database değiştiğinde, domain'in bundan haberi olmaması gerektiği için, bu kod bloğunu repository tarafına çekmeliyiz. Gerçek bir örnekten gidersek; RDMBS kullandığımızı varsayalım. Fakat bunun yerine ileride 1 entity'ye ait tüm ilişkileri Cassandra DB'de tek 1 tablo içerisinde tutabiliriz. Bu durumda domain'in değişmemesi lazım. Bu sebeple, bahsedilen kod bloğu repository altında olmalıdır. Tabi burada ince bir nokta daha var: Domain servisleri, repository metodlarını çağırırken, ilişkili data'ları ayrı ayrı silineceğini bildirmez, sadece aggregate root'un son halini yollar ve bunun silineceğini belirtir:

```java
// pseudo code örneği

// compatible with DDD:
repository.save( orderInstanceDomainObject );

// "Repository" implementations may have inside anyting like JPA-Entities.
```

# 4 Layers of DDD
DDD'de bir sistem 4 temel katman bulunmalıdır (kaynak: "Eric Evans", "DDD", "Layered Architecture" başlığı.):

- __User Interface (or Presentation Layer)__: web servislerinin bulunduğu, önyüzlerin bulunduğu kodlar.

- __Application__: bu kısım 'use case'leri içerir. bu kısımda business logic yoktur. Controller'larımızın gittikleri ilk servisler burasıdır diyebiliriz.

  Görevlerine bazı örnekler;
  - farklı client'lar için yapılan transformation ve validasyon işlemleri yapılabilir.
  - UnitOfWork, transactional gibi yönetimlerin tümünü bu katman yapar.
  - Dış dünyaya data döneceği zaman, domain-objelerini dönmez. Bunları DTO'ya çevirir. Dışarıya DTO döner.

- __Domain__: bu kısım business logic'lerin olduğu kısımdır.

- __Infrastructure__: diğer hizmetlerin (mail, database...) bulunduğu servisler/kodlar. Bu kısma aynı zamanda ORM mapperlar'da dahildir.

Yukarıdaki her maddenin ayrımı için kaynak: "Eric Evans", "DDD", şekil: "Figure 4.1. Objects carry out responsibilities consistent with their layer and are more coupled to other objects in their layer.".

# Domain types
- __subdomain__

  Domain: ecommerce, sub-domain: checkout, order.

  bir domain'de birden fazla subdomain olabilir. bir sub-domain'de birden fazla bounded context olabilir.

  best-practice'lere göre 1 bounded-comntext, 1 sub-domain'e denk gelmelidir. Fakat bunu yapmak çok zordur.

- __core domain__

  bir doktor için yazılım düşünelim. Temelde 2 ihtiyaç var: 1-randevu sistemi, 2-hastaların bilgileri

  Burada core domain 2inci oluyor. Çünkü; hastaların bilgilerini tutma, tahlil sonuçlarını göstermek temel amaç. Bu sebeple "randevu" domain'i, __supporting domain__'dir.

- __generic domain__

  user-management, file-archive gibi domain'ler generic domain olarak adlandırılıyor.

# bounded context
Bir model herkes için farklı görünebilir. örnek; USB ile satılan bir Java yazılımı; aynı şirkette;
- satış departmanı için satılacak "ürün"
- lojistik departmanında "kargo"
- yazılımcı içinse bir "jar dosyası"dır

"Bounded context" bir model'in (yada modellerin) belli sınırlar içindeki anlamını ifade etmek için kullanılan bir terimdir. Yani "context içerisindeki sınırlandırılmış model" olarak Türkçe'de düşünebiliriz. Her bounded context'te (satış, lojistik, yazılım...), farklı modeller ile bu "jar" dosyasını temsil edebiliriz. tabi bu durumlarda context'ler arası haberleşmede mapping yapmak ((context mapping) durumunda kalabiliriz.

# defining the bounded contexts
bounded context'lere ayırma işinin resmi bir standardı yoktur. bu iş biraz da sezgisel (heuristic) yapılır. Bounded context'lere ayırma işlemi yapılırken bazı dikkat edilecek noktalar şunlardır:
- uygulama geliştirme süreci ilerledikçe aynı isimler farklı field veya model'lerde karşımıza çıkmaya başlar. Bu durumda acaba bunlar farklı bounded context'lerde mi olmalı diye düşünmeliyiz.
- Yapılacak işin altyapısına göre değil, iş mantığına göre belirlenmelidir.
- transaction süreci göz önünde bulundurulabilir.

# context map/mapping
bounded context'ler arası ilişkilerin nasıl yönetileceği için disiplinleri belirler. bunların bazıları:

- Partnership

  iki context'i geliştiren ekip birbiri ile haberleşerek uyumlu şekilde ortak modellerini günceller.

- Shared kernel
  
  farklı bounded context'ler ortak model paylaşabilir. bu jar/dll paylaşarak olabilir... örneğin sadece "customer" modeli 2 bounded context için ortak ise bu yol izlenebilir.

- Customer/Supplier Development Teams

  customer'ın, X ve Y bounded context'i için ortak olduğunu düşünelim. X customer ile ilgili tüm işlemleri Y'ye servis olarak sunar. Y customer'ı kullanmaz. En fazla ID tutabilir. Bu durum 1 servisi diğerine bağımlı yapar.

- Conformist

  iki servisteki ekipler birbiri ile ortak çalışamıyor ise, 1 ekip diğerinin yaptığı her değişikliği almak zorunda olduğu durumdur.

- Anticorruption Layer

  bir context diğer context'teki ile uyuşmazlıklar yaşıyabilir. bu durumda en iyi çözüm; herkesin tamamen kendi modelini oluşturması ve olabildiğince birbirinin field'larına bağımlı kalmayacak şekilde servis istekleri hazırlanmalıdır.

- Open Host Service
- Published Language
- Seperate Ways

# microservice vs bounded context
DDD mimarisinde microservis ile ilgili bir bilgi yoktur. DDD, "modüler monolith" bir yazılımda da kullanılabilir. Dolayısı ile şu durumlar olabilir:
- Bazı durumlarda 1 mikroservis tek başına bir bounded context'i temsil edebilirken, birden fazla mikroservis birlikte 1 bounded context'i temsil edebilir. kaynak: (source-id: 231) "Bir Bounded Context == Bir Mikroservis ?" başlığı. + (source-id: 232) 1inci paragrafın sonu.
- 1 domain birden fazla microservis'ten meydana gelebilir. Veya tam tersi de olabilir.

# servisler
objelerin doğasında olmayan yazılımsal süreçler servis olarak tasarlanmalıdır. servis isimleri yine ortak (Ubiquitous) olmalıdır.

# Aggregate vs Aggregate Root
birden fazla entity'nin transaction'larda birlikte uyumlu şekilde iş akışını tamamlamaları gerekir. birden fazla entity'nin birlikte kullanılması durumu "__aggregate__" olarak ifade edilmektedir. yani aggregate, entity'ler grubudur. aggregate; koda baktığımızda sadece bir sınıf ile temsil edilmez. aggregate; logical bir kavramdır.

"__aggregate root__" ise; direk örnek üzerinden gidersek: "sipariş" bir 'aggregate root'tur. ancak siparişe bağlı, 'ödeme bilgisi', 'kargo bilgisi' entity'ler aggregate root'a bağlı (normal) entity olarak nitelenirler.

Siparişe bağlı 'ödeme bilgileri', 'kargo bilgisi' bazı durumlarda (bazı domain'lerde) aynı aggregate root'a bağlı olmayabilir. Fakat "sipariş kalemi (yani bir siparişteki her item)", "sipariş" aggregate root'unun altında olması bu konuya daha net bir örnek olarak verilebilir.

aggregate root; repository tarafından yönetilir ve client bir data load ettiğinde ancak aggregate root'a erişebilir. kaynak: (source-id: 233) answer of Jeff Sternal at Dec 24 '09 at 15:33. Fakat pratik'te böyle kod yazılmaz. genelde client'a sadece ihtiyacı olan data kısmı yollanır. bu durum anti-pattern değildir. client için gerektikçe optimizasyon yapılabilir.

```java
public class Order { // this is the "aggregate root" which has all information about "aggregate".

  int orderId;
  int endUserNumber;
  boolean disabled;
  List<OrderItem> orderItemList; // this is "domain object".
  // all other domain objects (like orderItem) should be added here as an object, not ID!

  // Customer is another aggregate. Therefore customer should not be added as object. It should be ID.
  int customerId;
  
  // Customer is another aggregate. Therefore we should not use the below fields on this class:
  // String customerName; // Which is inside Customer.name
  // Customer customer;
  // Address cutomerAddress; // Which is inside Customer.address.

  // getter and setters should be here...
  // Some "setters" may not be implemented if business logic requires...
  
  boolean addItem(OrderItem orderItem){

      if(disabled == true){
        return false;
      }

      if(orderItemList == null){
        orderItemList = new ArrayList<>();
      }

      if(orderItemList.size() > 999){
         throw new OrderExcepiton("You can not add more then 999 items to basket!");
      }

      orderItemList.add(orderItem);

      // This is "domain event".
      // Kafka can be used or Spring-event (application itself). By this way, other aggregates may effected by this operation.
      // It is optional to publish an event for each business method.
      kafka.publishEvent( new OrderItemAddedEvent(orderItem) );
      
      return true;
  }

  // All other business logic specific to Order should be here...

  // All the data and method of this class should be "persistence agnostic".

  // Only "Order" can be sent to "repository" to save/update...
  // OrderItem should not sent to "repository". There should not be "OrderItemRepository" on the whole application code.

  // Order should be saved transactional (via repository). Therefore the events (like OrderItemAddedEvent) should never publish before the transaction will success. (To achive this gap, if we use microservices we can prefer outbox pattern.)
}
```

# Domain Events
domain expert'lerini de ilgilendiren olaylar kolay takip edilebilir olmalıdır. aynı zamanda her event'in ismi/tanımı ve ne yaptığı açıkça belirtilmeli ve herkes tarafından event sonrası ve öncesi nelerin gerçekleştiği herkes tarafından bilinmeli. isimlendirmeler yine ortak (Ubiquitous) olmalıdır.

Teknik anlamda konuşursak; domain event'leri aggregate'lerin birbirleri ile haberleşmesi (bir aggregate'teki değişiklik, farklı bir aggregate'te de değişiklik gerektirdiğinde) durumunda fırlatılan event'lerdir. (Bu konuya event-sourcing başlığında da değinildi).

# DDD kitabında geçen bazı terimler
Aşağıdaki bazı terimleri direk olarak kitap içerisinde açıklanmış.

- # domain
  domain is the field for which a system is built. Airport management, insurance sales, coffee shops...

- # model
  representation of a real world object. example: student class is not a real student object. student class includent only name, surname, age and some others representation on digital world.

  Model objemiz her zaman fiziksel bir nesneye tekabül etmek zorunda değil. Bazen "para transferi" gibi bir modelmizde olabilir.

- # domain model vs database object
  domain objeleri, database objelerine benzer fakat database objelerinden tamamiyle ayrı olabilir. ilk uygulama tasarlandığında, "modeller" tasarlanmalıdır. daha sonra database-admin bunları nasıl isterse o şekilde database'ye kaydeder. database'de hızlı arama olsun diye bazı şeyler denormalize edilebilir, sorgu bazlı tablolar yapılması için data'lar mükerrer edilebilir vs... fakat bu optimizasyonlar database objelerinde yapılmalıdır.

  dolayısı ile; bu ikisi arasında gerçek hayattaki nesneye/kavrama en benzer olan; domain objeleridir. çünkü database yöneticileri gerçek hayata uzak değişiklikler yapabilir.

  işte DDD kitabı bu 'ünün uygulamamızda birbirinden bağımsız kalmasını, bu şekilde veritabanı yapısının, domain modellerini veya iş akışını etkilememesi konusunda yönlendirmektedir.

- # domain model
  domain model (class) is the model which is using by a domain.
  
- # DTO (or Data Transfer Object)
  DTO is the class/structure which is using to store data. It can be using to send data from network protocols or passing arguments to functions. DTO can store model or models or any data...

  gerçek bir uygulamadan örnek verirsek; repository'den dönen entity class'ı, önce model'e çevrilir, sonrada DTO'ya çevrilir ve client'a dönülür.

  DTO'lar, modellerimiz'in içerikleri aynı olacakları anlamına gelmez. Farklı da olabilirler. Yada aynı olabilirler ama modelleri direk döndürmek yerine, mapping yaparak aynı field'lara sahip farklı objeler de kullanabiliriz. Çünkü DTO'lar sadece Data transfer objeleridir ve servisler arası haberleşme'de data transferi için kullanırlar. Remote servis çağrıları maliyetli olduğu için, tek bir istekte birçok data'yı birden taşımak isteriz. Bu sebeple DTO' pattern'i ortaya atılmıştır. kaynak: (source-id: 234) 1st paragraph.
  
  Sun/Java community DTO'lara sadece "transfer obje" demektedir. Bu pattern'in yazılım dünyasında genel adı "Data Transfer Object (or DTO)"tir. kaynak: (source-id: 234) son paragraf.

- # entity
  yazılım framework'lerinde "entity" terimi, veritabanındaki bir tablonun yazılım tarafındaki temsilidir (örnek JPA "entity bean"). fakat Eric'in DDD kitabında "entity" terimi farklı amaçla kullanılmaktadır. kaynak: "Eric Evans", "DDD", "Entities (a.k.a. Reference Objects)" başlığı, 13'üncü paragraf.

  Eric'in kitapta bahsettiği entity kavramı; eşleştirilmeye kalktığımızda (bir eşitlik sorgusunda) field'ları ile değil, sadece ID'si ile kontrol etmemiz gereken domain modellerimizdir. kaynak: "Eric Evans", "DDD", "Entities (a.k.a. Reference Objects)" başlığı, 12'üncü paragrafın ilk cümlesi.

  Bazı kaynaklarda DDD'den bahsedilsin veya bahsedilmesin, "entity" terimi direk olarak hem domain model, hemde database nesnesinin yerine  kullanılmaktadır. Bunun 3 temel sebebi vardır: 

  1- domain model, BD'ye farklı kaydedilse de, aslında ikisi birbirinin yansımasıdır. Farklı bir değiş ile; bir modelin veritabanına farklı bir biçimde kaydedilmiş olması (yansıtılmış olması) onun gerçek değerinin kaybolmasına sebep olmaz. Örneğin; aynı modelin, "materialized view" ile NoSQL ve RDBMS'e ayrı ayrı kaydediliğini düşünelim. İligli Model, veritabanı-1, veritabanı-2 arası mapper fonskiyonlarımız olsun. Aslında 3ü arasında git gel yapabiliyoruz. Bu durumda aslında 3 taraftaki data aslında aynı varlığa tekabül ediyor.

  2- JPA direk olarak kendi içinde bu terimi DDD'den bağımsız şekilde kullanmaktadır. Sadece DB tarafından bakıldığında her tablo birer 'varlık'tır.

  3- DDD uygulamadığımız sistemde, NoSQL tarzı sistemler kullanmıyorsak, direk "entity bean"'lerini model olarak düşünüp birebir şekilde kullanabiliriz.

- # value object
  - property'leri eşit olduğunda, birbirleri yerine kullanılabilen objeler'dir.
  - immutable olmalıdırlar.

  - Aşağıda bazı örnekler listelendi. Fakat bu objeler domainden domain'e (business logic'e göre) entity veya value obje olabilirlerler. Yani aşağıdakiler bu şekilde olacak diye bir kaide yoktur. Aşağıdakiler Sadece örnek amaçlı yazılmıştır.

  örnek-1:
  
  X ve Y veritabanı objelerimiz olsun. ikisinin tüm property'lerinin (isim, soyisim, yaş...) value'ları aynı olsun. buna rağmen bu objeler birbirlerine eşit değildir. çünkü ID'leri farklıdır. bu sebeple bu objeler "value object" değildir.

  örnek-2:

  Koordinat düzlemindeki noktayı tutan bir point1 ve point2'miz olsun. bu objelerin property'leri (x, y, z) eğer aynı ise bu 2 obje birbirlerine eşit demektedir. bu sebeple point objesi bir "value object"'tir.

  örnek-3:

  İki farklı kişi aynı adres'te oturuyor olabilir. Böyle bir durumda her iki Person objesinin hangi adrese işaret ettiğinini önemi yoktur. Bu sebeple "adres"'in value object olmasını bekleriz. Fakat bazı business'larda adres objelerinin birbirinin aynısı olup olmayacağını tanımlayan bir garanti olmayabiliyor. Çünkü adresler genelde manuel giriş yapılıyor. SOn kullanıcı tarafından otomatik tamamlamadan seçilerek tanımlanmıyor. Uzunca bir string oluyorlar. Bu durum genelde e-ticaret sitelerinde oluyor. Bu sebeple e-ticaret sitelerinde adres bir entity'dir.

  Oysa bir harita sisteminde (örnek: google maps) bir adresin neresi olduğu tüm field'ları ile ayrılşmış şekilde sistematik olarak tutulur. Bu sebeple google-maps için adres value objedir.

  Not: E-ticaret'lerdeki adres objesinin entity olmasının sebebi; son kullanıcı tarafından update edilebilmesi (yani immutable kuralı bozması) değildir. Çünkü e-ticaret sitelerinde update edilen adres olduğunda, yeni bir adres objesi yaratılır ve eskisi disable edilir/edilebilir.

  örnek-4:

  renkler birer value object'tir. kaynak: kaynak: "Eric Evans", "DDD", "Is "Address" a VALUE OBJECT? Who's Asking?" başlığının hemen sonrasındaki ilk cümle.

  örnek-5

  money, range, date birer value objedir.

# strategic design vs tactical design
DDD kitabı 2 temel kısımdan oluşuyor. İçerdiği bazı konular aşağıdaki gibidir:
- tactical design (bu terim kitapta geçmiyor. Bunu yorumlayanlar bu şekilde isimlendiriyor)
  - strategic dışında kalan birçok kavram burada.
- strategic design (name of the Part IV of the book)
  - Bounded Context
  - Context Map
  - domain types (core-domain, sub-domain...)