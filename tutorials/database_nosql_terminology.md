############################

############################
# DATABASE NOSQL TERMINOLOGY
############################

############################

# NoSQL (or Not Only SQL or non-relational or non-SQL) vs Relational Database Management System (or RDBMS or İlişkisel veri tabanı yönetim sistemi)
ilişki olmamasından yola çıkılarak optimize edilmiş veritabanlarıdır. fakat bazı database'ler ilişki destekler. örnek: MongoDB'deki "DBRef" özelliği. dolayısı ile aslında olayın çıkış noktası ilişki olmaması olsa da, ilişki kurup daha fazlı özelliklerden feragat ederek optimize edilen veritabanları da NoSQL grubunun içindedir.

NoSQL veritabanları kendi içlerinde çok farklı mantıklarda çalışabilmektedirler. bazılarında bir özellik yok iken, diğerinde mevcut olabilir. işleyiş, data tutma biçimleri çok çok farklı olabiliyor.

piyasada NoSQL'lerin scallable olduğu söylenir. Oysa RDBMS'lerde scallable'dır. Fakat RDBMS'in scallable olmasını zorlaştıran etkenler çok daha fazladır. en önemli sebeplerden biri, distributed transaction lock ve foreign key özellikleridir. Çünkü bu özellikler tüm cluster'daki tüm node'lara aynı anda bilgi iletimi gerektirir. Dolayısı ile scallable sistemde yeni node ekleme çıkarma gibi işlemlerde, runtime sırasında binlerce farklı satırda lock olduğunu düşünürsek işimizi zorlaştığını göreceğiz. Aslında:
- RDBMS'lerde "Horizontal Scaling (or Yatay Ölçeklendirme)" NoSQL'e göre zordur (imkansız değil). - "Vertical Scaling (or Diken Ölçeklendirme)" ise hem RDBMS hemde NoSQL'lerde aynı komplekslikle olduğunu söyleyebiliriz. Çünkü sadece tüm sutunları okumak gerektiğinde hem NoSQL hemde RDBMS bu 2 node'a erişmek durumundadır. Eğer sadece 1 node'daki tüm sutunlar okunacak ise yine 2 DB'de sadece 1 node'a ihtiyaç duyacaktır.

# NoSQL database tipleri

- # Document-Oriented store
Her nesneyi (ID'si olan bir nesneyi) ayrı birer (tek) fiziksel döküman olarak saklar. kaynak: (source-id: 458) title: "Document data stores", 2th paragraph.

örnek sistemler: MongoDB.

- # Key-Value store
Bilgiler bir anahtar ve karşılığında bir değer şeklinde saklanıyor. genelde çok fazla işlem ama ufak verileri saklamak için kullanılan sistemlerde kullanılıyor (örneğin; caching).

En kritik noktalardan biri sadece key ile value çekilebilmesidir. Bu sebeple SQL'deki WHERE koşulu imkanı sunulmaz. Sunulsada çok yavaş arama yapacaktır. kaynak: (source-id: 458) title: "Key/value data stores", 5th paragraph.

örnek sistemler: Redis.

- # Graph store
Kayıtlar, graph(structure çeşidi) ile ilişkilendirilmiş şekilde tutulmaktadır. 

İlişkiler RDBMS'teki gibi çift yönlü olmak zorunda diildir. Tek yönlü de olabilir. (source-id: 458) title: "Graph data stores", 1th paragraph.

Bu tarz sistemlerde ilişkileri çok fazla olduğu query'ler yapılmaktadır: "Find all employees who report directly or indirectly to Sarah" or "Who works in the same department as John?". (source-id: 458) title: "Graph data stores", 3th paragraph.

örnek sistemler: Neo4J, Giraph

- # others which includes "column" word
bu gruba giren örnek sistemler: HBase, Cassandra.

burada terminoloji karmaşası söz konusudur. Bu kaynakta yorumları da dahil olmak üzere çok verimli bilgiler mevcut: (source-id: 407)

"column" terimi içeren NoSQL terimleri aşağıda açıklanmıştır. Bu terimler piyasada sıkça birbirleri yerine kullanılmaktadır. Fakat genel olarak "column" terimi içeren DB sistemleri her sutuna (veya sutun grubuna) ayrı ayrı (tüm diğer sutunları okumadan) erişebilmemizi sağlar.

  - # column-oriented
    bu terim RDBMS dünyasında farklı amaçla kullanılan bir terimdir. Fakat çoğu makalede bu terim NoSQL'ler için de kulanıldığında karışıklığa sebep olmaktadır.

  - # column-store
    column-store bir sütun'a ait (belli range'lerdeki veya tüm) bilgilerin fiziksel olarak ardarda kayıtlı olduğu sistemlerdir. daha doğrusu; her hücrenin hangi satıra ait olduğu bilgisinin direk olarak store'a yazılmayan sistemlerdir. bu tarz sistemlerde bir hücrenin hangi satır'a ait olduğunu farklı hesaplamalarla bulabiliriz. column-store fiziksel olarak data'yı bu şekilde kaydeder:

    ```
    (ID) 1, 2, 3, 4, 5, 6
    (First Name) Joe, Jack, Jill, James, Jamie, Justin
    (Last Name) Smith, Williams, Davis, Miller, Wilson, Taylor
    (Phone) 555-1234, 555-5668, 555-5432, NULL, 555-6527, 555-8247
    (Email) jsmith@gmail.com, jwilliams@gmail.com, NULL, jmiller@yahoo.com, NULL, jtaylor@aol.com
    ```

    column-store'lar her sutunu ve içindeki bilgileri farklı dosyalarda saklar. Dolayısı ile sadece tek fromatta (String, int...) veri tuttuğu için compression gibi birçok optimizasyon sunar.

    Yukarıdaki şekli bir tablo gibi düşünürsek, artık ID'ler bizim için sutun, "first name" ve "last name" bizim için satır gibi olmuş oluyor. Bu sebeple "column-store" DB denir. Çünkü RDBMS sistemler "row-store" olarak ifade edilebilir.

    Örneğin Cassandra column-store değildir. zaten resmi Github sayfasında "partitioned row-store" olduğu yazar. çünkü eğer bir hücreye erişmek istiyorsak; Cassandra, önce row-key'i buluyor, sonra o satırdan istediğimiz column-name'i olup, ilgili sütunun değerini buluyor. Zaten Cassandra her sutunu ayrı dosyda tutmuyor, 1 tabloyu tümüyle aynı dosyada tutuyor (bu durum "column family" başlığında anlatılıyor).

  - # column family (or columnar data store)
    columnar türkçe kelime anlamı: sutunsal, sutun biçiminde, sutunlu...

    "ar" suffix'i, "tabular" kelimesindeki gibi kullanılıyor. "tablular", "table" kelime kökünden geliyor ve "tablosal (tablo biçiminde)" anlamına geliyor.

    column family database'de, RDBMS'teki tablo, column-family'ye denk gelmektedir. column family yapısında developer'ın sorgudan döndürmek istediği her sütun için farklı tablo yapması gerekir/beklenir. (not: "one-table-per-query pattern" buradan gelir). bu sebeple "tablo" yerine "column-family" terimi kullanılır. yani 1 tablo, bir column grubuna denk gelir. "family" suffix'i buradan gelir. family suffix'i; bir nevi "column-group" terimine denk gelir.

    Bu kısmı farklı bir dille açıklamak gerekirse: user_by_name ve user_by_id tablomuz olsun. RDBMS'te bunları tek 1 tabloda tutardık. Column-family yapısında ayrı ayrı tutuyoruz. İşte bu sebeple sütunları family'lere ayrılmış varsayıyoruz. terim buradan geliyor.

    Column family yapısında fiziksel olarak, her column-family data tek bir dosyada tutulur. Tabi bu dosyada tüm satırlar diil, belli aralıktaki satırlar tutulur. Yani birçok dosya birbirini tamamlar. Fakat bunun avantajı şudur: Bir data açekmeye çalıştığınızda, sadece ilgili sutunların olduğu dosyayı okumak yeterli olmaktadır. Yani sadece column-family'deki sutun'ları okumaktayız. kaynak: (source-id: 458) title: "Columnar data stores", 5th paragraph.

    dosyanın logical yapısı bu şekildedir:

    ```
                  column-A      column-B
    row-key-1     value-1       value-2


                  column-A      column-C
    row-key-2     value-3       value-4
    ```
    
    "table" ile "column-family" karşılaştırıldığında, fiziksel olarak data tutuş biçiminin fark etmemesini bekleriz. fakat ikisi arasında şu farklar söz konusu:
    - kavramsal/logical farklılık (birinde denormalized ve dublicated data olabilirken diğerinde bu olmamalı)
    - veriye erişimde, genelde farklı öncelikler tercih edildiği için, data'nın tutuş biçimi structural olarak farklı optimize ediliyor. örneğin column-family mantığında (genelde) data fiziksel olarak sorted oluyor. tablo ile karşılaştırıldığında, sorted olması gibi optimizasyonlar/farklılıklar söz konusu olabiliyor. RDBMS'te de 1 sutuna göre index'leme yapabiliyoruz fakat RDBMS'te data fiziksel sorted olmuyor.

    Cassandra dünyasında eskiden column-family terimi kullanılırdı. fakat daha CQL'e geçiş ile "tablo" terimi kullanılmaya başlandı. fakat Cassandra hala column-family bir database'dir.

  - # wide-column store (or extensible record store)
    column family'nin türevidir diyebiliriz.

    __wide-column__ sistem; her cell (hücre)'nin value'su için farklı sürüm değerleri saklar. __time-series pattern__'i de buradan gelir. Bu sebeple; __wide-column__ store'lar "__three-dimensional structure__ (bazen "__multi-dimensional__" denir)" olarak, document-based store'lar ise "two-dimensional structure" olarak nitelendirilirler. çünkü document-store'da her column'un farklı sürümlerini saklayamayız (JSON formatını düşünürsek bunu hayal edebiliriz).

    ```
                  column-A   column-B@01-01-2020       column-Y
    row-key-1     value-1    value-2                   value-3


                  column-A   column-B@02-02-2022       column-X
    row-key-2     value-4    value-5                   value-6
    ```

    __Time series data store__, wide-column store'un bir alt kümesidir. Sutunların versiyonları zamana göre ayrılır. Bunun için özel geliştirilen DB'lerdir.

# Kullanım tercihi
Yukarıdaki NoSQL tiplerine bakıldığında, aslında, herhangi bir database ile kaydettiğimiz ve çektiğimiz bilgiyi diğeri ile de yapabiliriz. örneğin; Document tabanlı sistemdeki kaydı, Key-Value ile de tutabiliriz. fakat seçimimizi bilgilerimizi nasıl çekeceğimize (nerelere sorgu atıp çekmek isteyeceğimize), nasıl kaydedeceğimize göre karar vermeliyiz.

örneğin; ilişkisel veritabanı gibi data kaydedecek isek, fakat ilişkiye ihtiyacımız yok ise, Document tabanlı database bu iş için uygun. çünkü ilerideki zamanlarda her data sütununa göre sorgu atmak isteyebiliriz. oysa bu data'yı Key-Value database'de saklıyor olsaydık, sorgularımızda büyük problem yaşardık. çünkü Key-Value database value'da ne olduğu ile pek ilgilenmez. Key-Value genelde value'su tek bir değer olan bilgiler için uygundur. bu şekilde daha hızlı okuma ve yazma yapabiliriz. Hatta bu sebepten genelde RAM üzerinde çalışırlar.
