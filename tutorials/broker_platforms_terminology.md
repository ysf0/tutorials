############################

############################
# BROKER PLATFORMS TERMINOLOGY
############################

############################

# Messaging system
__JMS (or Java Messaging Service)__ is an implementation of "messaging system".

In traditional messaging systems, events are deleted after consumption.

Messaging system'a aracılık eden tool'a __messaging broker (or message broker)__ denir.

# message queuing vs publish-subscribe (or P/S) & topic vs queue
Kafka ve alternatifi sistemler 2 tipte mesaj yollama işlemini yapabiliyor. __publish-subscribe__'da tüm consumer'lara mesaj giderken, __queuing (or Point-to-Point Messaging Model or P2P Model)__ modunda sadece 1 adet consumer mesajı okuyabiliyor. kaynak: (source-id: 388) "Kafka as a Messaging System" başlığı ilk paragraf.

JMS dünyasında terimler yukarıdaki gibidir ve JMS dünyasında P/S __topic__'ler aracılığı ile yapılırken, P2P, queue aracılığı ile yapılır.

Kafka yukarıda yazan "message queuing" ve "publish-subscribe" özelliklerini sadece "topic" üzerinden destekliyor. Bu bazen makalelerde terimlerin yanlış anlaşılmasına sebep olabiliyor. Kafka yukarıda yazan özelliklere ek olarak şu özelliği sunuyor: streaming. Yani offset'i bilen client'lar eski bilgileri istediği okuyabiliyor, yani stream edebiliyor.

# Kafka vs RabbitMQ
Kafka streaming platform olarak geçer, RabbitMQ ise messaging broker'dır. temelde fark şuradadır: Kafka-server kuyruğu silmez. Kafka-client kuyrukta nerede olduğunu (index'i) kendi tutmak zorundadır. bu onu "consumer-centric" yapar. bu sebeple streaming platform olarak kullanılır. çünkü her client istediği gibi geçmişe ileriye gidebilir, yani stream edebilir. RabbitMQ da ise push vardır. RabbitMQ mesajları karşıya push'lar. eski mesajları client göremez. RabbitMQ'daki bu çalışma modeline "__smart-broker/dumb-consumer (or smart broker/dumb consumer)__" denir. Oysa Kafka'nın çalışma modeline tersi olarak; "__smart-consumer/dumb-broker (or smart consumer/dumb broker)__" denir.

not: Kafka-consumer(client) başarılı şekilde işlemin bittiğini ("acknowledgment") Kafka'ya bildirir. böylece Kafka bir cursor tutar. Dolayısı ile yeni ayağa kalkan bir client index'i bilmek zorunda değildir. Cursor'un olduğu yerden, pull etmeye başlayabilir. Fakat istenirse, index üzerinden de hareket edebilir. Eğer kesinlikle index üzerinden tekrar event okumayacak ise, Kafka kullanmamayı düşünmek gerekebilir.

RabbitMQ mesajları persist edebilir fakat bunların çekilmiş client'lar tarafından tekrar çekilebilmesini sağlayamaz.

RabbitMQ mesajların consumer'lara ulaşıp ulaşmadığını garanti edebilir (retry yapabilir).

# message queue vs message broker
message broker yazılımı, message queue'ların management'ini sağlar. kaynak: (source-id: 389) title: "What is a message broker?", 4th paragraph.

- enqueue
  
  fiildir. sıraya almak.

- dequeue

  fiildir. kuyruktan çıkarmak.

# event bus için yazılımlar (broker'lar)
  - Apache Kafka

  - JMS (or Java Messaging Service)

    JMS API, JavaEE'nin bir API spesifikasyonu. Runtime'da bir implementasyon kullanmak zorundayız. Bu implementasyonlara __JMS provider__ (broker) deniyor. JMS client'lar, JMS provider'a bağlanarak çalışır. JMS client destekleyen provider'lardan bazıları (bu liste normal JMS olmayan client'lar tarafından da message-queue olarak kullanılabilir):

    - Apache ActiveMQ

      "Artemis" kod adı ile ActiveMQ projesi paralelden geliştiriliyor. Artemis stabil olduğunda eski proje (Artemis'in başlaması ile artık "Classic" olarak adlandırılıyor) sonlandırılacak.

      __Advanced Message Queue Protocol (or AMQP)__ protokolü ile çalışır. Fakat MQTT, OpenWire, Stomp protokolleri ile de çalışabilir.

      - __OpenWire__: __AMQP__'ye çok benzer bir protokoldür.
      - __OpenWire__ vs __STOMP__: STOMP text based haberleşme sağlar ve OpenWire'a göre yavaştır. OpenWire ise binary haberleşme sağlar ve STOMP'a göre hızlıdır.

    - __Open Message Queue (or OpenMQ or Open MQ)__

      Oracle tarafından geliştirilen, GlassFish içerisinde default olarak geliyor. İstenirse standalone da kullanılabiliyor.

    - __OpenJMS__

    - __Oracle Advanced Queuing (or AQ)__

    - __IBM MQ (or old-name:MQSeries or old-name:WebSphere MQ)__

    - __Rabbit mq__
    
      Pivotal Software tarafından geliştiriliyor. __AMQP__ protokolü ile çalışır.

# BROKER FEATURES
Broker olan sistemlerde şu özelliklerden bahsedebiliriz:

- ## CONSUMPTION MODE
Push vs Pull.

push: broker'ın push ettiği model.

pull: consumer'ın pull aldığı model.

Client'ın pull alması, client'ın kendine fazladan yük bindirmemesi konusunda avantaj sağlamaktadır. Çünkü broker sürekli push yaparsa sıkıntı olabilir.

- ## MESSAGE QUEUING MODEL
point-to-point (or P2P) vs __publish-subscribe (or pub/sub)

point-to-point, 1 mesaj en fazla 1 consumer tarafından okunabilir. "queue" vardır. queue'ya 1 den fazla consumer listen edebili fakat yine de 1 mesajı sadece 1 consumer okuyabilir.

P2P, Fire-and-forget (async) veya request/reply (synchronized) messaging olabilir. 

pub/sub modelinde ise 'topic'ler vardır. 

- ## DELIVERY GUARANTEE
birçok çeşit olabilir. bazı örnekler:
- at-most-once
- at-least-once
- exactly-once

- ## ORDERING GUARANTEE
- no-ordering:

  bazı broker'lar mesajların sırasını garanti edemeyebilir. performans açısından büyük avantaj sağlar.

- partition or queue ordering

  bazı brokerlar mesaj sırası garanti edebilir ancak sadece belli kısımları için edebilir. örneğin Kafka sadece partition bazında garanti verebiliyor.

- global ordering

  performans açısından önemli derecede yavaşlığa sebep olabilir. bu seviyede tüm partition'lar arası sürekli senkronizasyon gerekmektedir.