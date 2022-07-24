############################

############################
# SECURITY UUID
############################

############################

# UUID (or Universally unique identifier)

- (source-id: 302)'da belirtilen standartlardır. her versiyon hakkında bilgi yine bu standart altında belirtilmiştir. bu standartta 5 adet version belirtilmiştir. versiyonlama, olgunluk olarak belirlenmemiştir, sadece 5 çeşit UUID vardır. bunlar aşağıdaki gibidir:

  - version 1 (Time Based)

    cihazdaki MAC adresi ve data-time (en ufak birimi nanosecond olacak şekilde) bilgisi ile UUID üretir. aynı bilgilerle aynı UUID tekrar üretilebileceğinden bazı durumlarda takip edilebilirliği sağlamak amaçlı bu kullanılmaktadır.

    mac adresi olmayan durumlarda (cihazlarda/platformlarda) rastgele sayı kullanılabileceği RFC standartlarında belirtilmiştir.

  - version 2 (DCE Security)

  - version 3 (Name Based)

    UUID oluşturmak için namespace(URL gibi) ve name'in MD5'i kullanılır. örnek kod:

    ```java
    String source = namespace + name;
    byte[] bytes = source.getBytes("UTF-8");
    UUID uuid = UUID.nameUUIDFromBytes(bytes);// bizim için MD5 hash alıyor
    ```

  - version 4 (Random)

    sistem random number generate ederken, önceden belirli data'lardan yararlanmaz. bu sebeple genelde bu tercih edilir.

  - version 5 (Name Based)

    Version 3 ile aynı. tek fark: MD5 değil, SHA-1 istiyor.

- version

  most significant 4 bits of "time" block.

- variant

  UUID'nin ilk 2 bitidir.

  UUID'nin layout'udur. hangi bitlerde, hangi bilginin yer aldığı standartıdır.
  
  RFC4122'de sadece bir varyant anlatılıyor.

  ("x" önemi olmayan bit anlamına geliyor)

  | bit-0 | bit-1 | bit-2 | explanation                                            |
  |-------|-------|-------|--------------------------------------------------------|
  | 0     | x     | x     | Reserved, NCS backward compatibility                   |
  | 1     | 0     | x     | RFC4122'de anlatılan formattır                         |
  | 1     | 1     | 0     | Reserved, Microsoft Corporation backward compatibility |
  | 1     | 1     | 1     | Reserved for future definition.                        |

  Leach-Salz (RFC4122 yazarlarının soyadları) UUID'nin 2'inci varyantının (digit olarak bakıldığında varyant değeri "1") takma adı olarak her tarafta kullanılmaktadır.

- Java code of version vs variant

  ```java
  UUID uuid = UUID.randomUUID();
  int variant = uuid.variant();
  int version = uuid.version();
  ```
  
- Tekil bir stringdir. 128 bittir.

- sayı çok büyük olduğundan aynı sayının aynı uygulama içinde üretilmesi matematiksel olarak çok azdır. bu sebeple standart olarak kullanılır.

- örnek kullanım alanlar:
  - MAC adresler
  - dosya sistemlerinde partition ID'leri
  - database'lerde ID'ler

- 36 karakterdir ve arada tire koyularak (tireler sadece notasyondur, 128 bite dahil değildir) 5 grup olarak gösterilir:
  > 123e4567-e89b-12d3-a456-426655440000
    
  her grup bir data'yı temsil eder:

  - time
  - version
  - clock_seq_hi
  - clock_seq_lo
  - node

- sadece küçük harf karakterler geçerlidir.

- Uniform Resource Name (or URN) gösterimi bu şekildedir:

  > urn:uuid:123e4567-e89b-12d3-a456-426655440000

- Nil UUID

  tümü sıfır olan UUID'dir.

# Globally unique identifier (or GUID)

Microsoft'un UUID implementasyonudur. UUID'den hiçbir farkı yoktur. sadece variant değeri farklıdır.
