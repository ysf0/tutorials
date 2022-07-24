############################

############################
# WEB WEBSOCKET
############################

############################

# STOMP (or Simple Text Orientated Messaging Protocol or Streaming Text Orientated Messaging Protocol)
Alt seviyesindeki protokollerden bağımsız, text tabanlı, üst seveyeli bir protokoldür. Örneğin HTTP ile kullanıyorsak, kendisini sadece body kısmına ekler.

STOMP'un farklı sürümleri mevcut.

Örneğin aşağıdaki mesaj, SockJS (websocket senaryosu, fallback diil) üzerinden STOMP ile sunucuya yollanmış bir mesajın body kısmıdır:

```
["CONNECT\nuserName:jack\naccept-version:1.0,1.1,1.2\nheart-beat:4000,4000\n\n\u0000"]
```

Bunu human-readable yapıp göstermeye çalışalım:

```json
{
    "command": "Connect",
    "headers": {
        "heart-beat": "4000.4000",
        "accept-version": "1.0,1.1,1.2",
        "userName": "jack"
    },
    "body": ""
}
```

- STOMP temelde 3 bilgiden oluşur. Body'nin içeriğine hiç karışmazken, bazı header'lar standarttır.
- Body kısmı her zaman String'dir.
- STOMP'un kendisinde CONNECT, SUBSCRIBE, DISCONNECT gibi birçok komut vardır. Bunlar standart olduğu için kütüphaneler de bunlara resmi destek verir. Örnek bir JS kodu:

```js
var socket = new WebSocket('ws://localhost:8080/greeting');
ws = Stomp.over(socket);

ws.connect({}, function(frame) {
    ws.subscribe("/user/queue/errors", function(message) {
        console.log("Error " + message.body);
        message.ack(); // optionally can be sent ACK to server.
    });

    ws.subscribe("/user/queue/reply", function(message) {
        console.log(message.body);
    });
}, function(error) {
    console.log("error " + error);
});
```

# Transaction
STOMP her message için ACK yolladığı zaman her mesajda bulunan ID'yi kullanır. Buna ek olarak istenirse transaction ID de yaratılıp, tüm transaction'ın abort edilmesi veya kabul edilmesi gibi süreçleride yönetilmesi için protokolde bazı standartlara yer verilmiştir.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# WebSocket
- TCP socket'lere bağlanamazlar. Karşı tarafında WebSocket kullanması şart. TCP üzerine kurulu HTTP alternatifidir.
- browser to browser haberleşme mümkün değil, çünkü browser'da server-web-socket açılamaz. 
- server taraf istediği port'ta ve path'te web socket'i sunucu modunda açabilir.
- protocol: URL'lerde 'ws' prefix'i kullanılıyor. 'wss' ise secure (SSL) kullanan versiyonudur.
- ISS, Nginx, Apache HTTP Server gibi pazarı yüksek sunucuların resmi olarak WebSocket destekleri vardır. 
- WebSocket tam iki taraflı iletişimi sağlar. bir request'e karşılık response olmak zorunda değildir. iki tarafta istediği kadar ve istediği zaman mesaj atabilir. bu tarz iletişimlere full duplex iletişim protokolü denir. 

# Standartlar
WebSocket rfc6455 ile birlikte 2011'de resmi stabil standartlarına kavuştu. O zamana kadar bazı tarayıcılar WebSocket RFC'sinin draft'ları ile (hybi ve hixie prefix'li RFC'ler) haberleşme imkanları sundular.

# Handshake
WebSocket bağlantısı kurulduğunda client sunucuya önce bir HTTP isteği gönderir (80 portu değil. direk WebSocket'in bağlanacağı port'a yollar bu isteği):

örnek:

```
GET ws://websocket.example.com/ HTTP/1.1

Origin: http://example.com

Connection: Upgrade

Host: websocket.example.com

Upgrade: websocket
```

Burada WebSocket'e geçiş yapmalarını söyler. sunucuda bunu kabul eder:

```
HTTP/1.1 101 WebSocket Protocol Handshake

Date: Wed, 16 Oct 2013 10:07:34 GMT

Connection: Upgrade

Upgrade: WebSocket
```

Bu istekten sonra artık aynı TCP bağlantı üzerinden sürekli stream'in yapılır.

# Message vs fragment
fragment Türkçe kelime anlamı: parça

API'lerin sunduğu onMessage event'lerimiz her message geldiğinde tetiklenir. her message arkaplanda en az bir adet "frame" denilen parçalardan oluşur. frame'ler şu akışta daha basit anlaşılabilir:

```
Client: FIN=1, opcode=0x1, payload="hi"

Server: bir mesaj geldi: Hi

Client: FIN=0, opcode=0x1, payload="ben"

Server: mesaj dinlenmeye devam ediyor...

Client: FIN=0, opcode=0x0, payload="ahmet"

Server: mesaj dinlenmeye devam ediyor...

Client: FIN=1, opcode=0x0, payload="Doganoglu'yum."

Server: bir mesaj geldi: ben Ahmet Doganoglu'yum.
```

- FIN=1 ve FUN=0 mesajın devam edip etmeyeceği bilgisini yolluyor.

# opcode'lar
- opcode=0x1 text mesajı atıldığını
- opcode=0x2 binary mesaj atıldığını
- opcode=0x0 ise bu frame'in önceki frame'in devam ettiğini belirtiyor.
- opcode=0x3-7 are reserved for future
- opcode=0x8 denotes a connection close
- opcode=0x9 denotes a ping (for heart-beat)
- opcode=0x10 denotes a pong
- other opcodes reserved for future

# Heartbeat
WebSocket heartbeat için yapılan özel opcode var. Fakat bu mesaj, WebSocket altyapısı tarafından otomatik atılmıyor. Developer'ın kendisi bunu düzenli olarak tetiklemeledir ve kullanımı opsiyoneldir.

STOMP Sürüm 1.1 ile heart-beating özelliği geldi. SockJS'te de heart-beat özelliği olmasına rağmen, STOMP'ta heart-beat özelliği sunar. Çünkü STOMP onu taşıyan protokollerden bağımsızdır.

STOMP ve SockJS'te de heartbeat opsiyoneldir. fakat heartbeat mesajı, kütüphanenin kendisi tarafından otomatik düzenli olarak karşı tarafa atılır.

# frame tipleri
Data yollanması amaçlı yollanan frame'ler __data frame (or non-control frame)__, diğer amaca hizmet eden frame'ler __control frame__ olarak gruplandırılır.

bir frame'in, control frame'i olup olmadığını opcode'dan anlarız.

# Subprotocol
- WebSocket'in rfc'sinde Subprotocol tanımı açıklanmıştır.
- Subprotocol payload'da gönderilecek data'nın formatıdır. XML şeması yapısına çok benzetilebilir.
- Subprotocol bilgisi "Sec-WebSocket-Protocol" header'ında yollanmaktadır.
- Kayıtlı subprotokoller buradan görülebilir: https://www.iana.org/assignments/websocket/websocket.xml. Bu listeden bazı örnekler:
  - soap
  - wamp
  - v10.stomp
  - v11.stomp
  - mqtt
  - MBLWS.huawei.com

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# SockJS
WebSocket'i wrap eden bir kütüphane. Sunucu tarafta da SockJS-server kullanmak şart. Eğer WebSocket desteklemeyen bir tarayıcıdaysak, SockJS otomatik olarak aşağıdaki gibi yöntemlere gider:

- HTTP (without streaming) (long polling or short polling - explaining in another topic) 
- HTTP streaming
- JSONP
- hixie (old draft version of WebSocket. It was used by some web-browser.)
- hybi (old draft version of WebSocket. It was used by some web-browser.)
- IFrame solutions (The server side serves HTML page. The details are here: https://sockjs.github.io/sockjs-protocol/sockjs-protocol-0.3.3.html title: "IFrame page: /iframe*.html".)

SockJS kütüphanesinin API'si, WebSocket API'sini simüle eder. Fakat SockJS, iletişim yöntemi WebSocket kullanılamadığında değiştiği için kendisi de bir "protokol" olarak düşünülmelidir. Github'da farklı bir repository'de bu protokolün resmi dökümantasonu geliştirilmektedir ve bununda farklı sürümleri vardır: https://github.com/sockjs/sockjs-protocol. Bu repository'nin dökümantasyonu burada yayımlanmaktadır: https://sockjs.github.io/sockjs-protocol/sockjs-protocol-0.3.3.html. Protokolü incelediğimizde WebSocket dışında HTTP'ye geçiş olması durumuna karşı hangi path'lerden haberleşileceği bilgileri de mevcut.

SockJS resmi protokol dökümanında "Protocol and framing" başlığında şu cümleyi içerir:

"SockJS tries to stay API-compatible with WebSockets, but not on the network layer. For technical reasons SockJS must introduce custom framing and simple custom protocol."

Ve ardından kendi __frame__'lerini tanımlar. Buradaki '__frame__' tanımı, orjinal WebSocket RFC'sindeki dökümanınkinden tamamen ayrı bir kavramdır. SockJS kendi __frame__'lerini:
- eğer WebSocket kullanıyorsa payload kısmında yollar (fakat bir Subprotocol olarak kendini tanıtmaz)
- eğer HTTP kullanıyorsa, yine payload kısmında bunu yapar.

Firefox developer tool'daki network sekmesinden, WebSocket işlemlerini izlediğimizde, payload kısmını yansıtırken SockJS olup olmadığını Firefox otomatik algılıyor ve son kullanıcıya ilgili mesaj kısmı doğru formatta gösteriliyor.

Mesajların body kısımlarında "o", "h", "a" gibi prefix'leri görmemizin sebebi SockJS'tir.

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •
