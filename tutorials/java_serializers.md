############################

############################
# JAVA SERIALIZERS
############################

############################

# GSON
Java için Java objelerini JSON'a çevirip tekrar Java objesine çevirme kütüphanesidir.

# JAXB (Java Architecture for XML Binding)
- Java içinde gelen XML kütüphanesidir.
- javax.xml.bind.* paketleri kümesini kapsar.
- Java 9 ile deprecated olarak işaretlendi, 10 ile tamamen kaldırıldı.
- marshalling ve unmarshalling yapar ve verilen XML şemasına göre Java objeleri oluşturur.
- marshalling işlemi sonrası bir XML oluşur. bu XML hem kolay okunabilirliği de sağlar, aynı zamanda üzerinde un-marshalling yapmadan önce değişiklikler de yapılmasını kolaylaştırır. oysa serializable'da bir nesne dosyaya dönüştürülmüşse artık değişiklik mümkün değildir.

# Jackson
asıl öncelikleri JSON olan, fakat ekstradan XML gibi birçok formatı ayrıştıran, üreten, işleyen bir Java Kütüphanesidir.

2.x'ten eski sürümler org.codehaus.# paketi altında dağıtılıyordu, 2.x sürümü ise com.fasterxml.* altında dağıtılıyor.

```java
@JsonPropertyOrder({"age", "id", "name"})
public class Person {
  
    @JsonProperty("_id")
    private String id;

    private String name;

    private int age;

    @JsonIgnore
    private String note;
}
```

Jackson 3 farklı alt projeden oluşuyor:

- Streaming (jackson-core)

  Burada xml/JSON derleme gibi işlemleri yapan core kodlar mevcut. alttaki tüm altprojeler bu projeye depend eder.

- Annotations (jackson-annotations) 

  sadece annotation'lar ayrı olarak bu projede barındırılıyor. annotation kullanmak istemeyenler bu projeyi classpath'te bulundurmak zorunda değil.

- Databind (jackson-databind)

  ObjectMapper/XmlMapper gibi sınıfların bulunduğu paket.

Yukarıdaki tüm dependency'leri tek bir Maven paketinden bulabiliriz:

```xml
<dependency>
    <groupId>com.fasterxml.jackson.dataformat</groupId>
    <artifactId>jackson-dataformat-xml</artifactId>
    <version>2.10.0</version> 
</dependency>
```

Yukarıdaki Maven dependency'si sadece XML formatı için Objectmapper türevini içerir. "jackson-dataformat-xml" yerine buradaki formatlardan birini tercih edebiliriz: (source-id: 316)

## ObjectMapper vs XmlMapper
ObjectMapper, JSON işleme metotlarının bulunduğu API. XmlMapper ise projeye sonradan eklendi. XmlMapper, ObjectMapper'dan türemiş bir sınıf. tüm metotları override edilmiş ve sadece XML işleme için kullanılmak için tasarlanmıştır.

## Modules
Jackson 3üncü parti module altyapısını destekler. modüller araya girerek birçok ek özellik katabilir. modülleri Jackson'a register etmemiz gereklidir:

```java
ModuleX moduleX = new ModuleX();
objectMapper.registerModule(moduleX);
```

Eğer manuel registration yapmaz isek bu metot ile classpath'te bulunan tüm metotları oto register yapabiliriz:

```java
ObjectMapper.findAndRegisterModules();
```

Jackson wiki'lerinde "Core modules" kısmında, yukarıda belirttiğimiz 3 proje gösteriliyor: Streaming, Annotations, Databind. fakat bunlar birer modül gibi register etmek gerekmiyor.

Bazı modüller aşağıdaki repo'larda geliştiriliyor. her repo'nun içinde birden fazla modüle mevcut.
- (source-id: 317)
- (source-id: 318)

Bazı modüller:

- ## Jackson Module JAXB Annotations
  JAXB, Jackson'a alternatiftir. önceden JAXB kullanıyorsak, JAXB'nin annotation'larını bazı Java Bean'lerimize atmış olabiliriz. bunları Jackson'ın da algılamasını istiyorsan bu projeden yararlanmamız gerekir.

  ```xml
  <dependency>
    <groupId>com.fasterxml.jackson.module</groupId>
    <artifactId>jackson-module-jaxb-annotations</artifactId>
    <version>2.4.0</version>
  </dependency>
  ```

- ## jackson-datatype-jdk8
  JDK 8 ile gelen optional değerler için support sağlıyor. örnek: serialize edeceğimiz sınıfımızda bu değere destek verebiliriz:

  ```java
  class Person {
      private final String name;
      private final Optional<String> email;
  ```

- ## jackson-datatype-jsr310
  Java 8 ile gelen java.time.* kütüphanesinin serileştirmesine yardımcı olur.

  ```xml
  <dependency>
      <groupId>com.fasterxml.jackson.datatype</groupId>
      <artifactId>jackson-datatype-jsr310</artifactId>
  </dependency>
  ```
