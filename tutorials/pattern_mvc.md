
############################

############################
# PATTERN MVC 
############################

############################

# MVC vs MVP vs MVVM vs Redux vs Flux vs Presentation Model (or Application Model)

Redux ve Flux pattern'leri detaylı şekilde farklı başlıkta anlatılıyor.

bu konuya girmeden önce birkaç terimi incelemek gerekli:

- # concern
    concern Türkçe kelime anlamı: ilgi, endişe, ait olmak

    yazılım projelerinde concern her bir fonksiyonalitenin yazılım tarafındaki katmanıdır. örneğin loggining layer'ı bir concern'dir.

- # Cross-Cutting Concern
    yazılımımızın bir katmanında diğer concern'lere ihtiyaç duyabiliyoruz. "loggining", "security" gibi concern'ler diğer tüm katmanlar tarafından ihtiyaç duyulmaktadır. başka katmanlardan çağrılan concern'lere "Cross-Cutting Concern" denir. bazı örnekler:

    - security
    - configuration management
    - logging
    - communication between services (protocols, DTO standarts...)
    - monitoring (healt check, metrics, distributed tracing)
    - persistence management
    - caching
    - data validation
    - business rules (common rules which are using by independed services)
    - exception handling
    - performance/memory management -> performans cross-cutting concern'dür. fakat her yere kod yazmayı gerektiren bir durum olmayabilir. yada bunun altına sub-category olarak caching'i ekleyebiliriz.

- # Separation Of Concern
    SoC concern'lerin birbirinden ayrılması için tasarlanmış pattern'lerdir/çözümlerdir.

    aşağıdakilerin her biri SoC çözümü için geliştirilmiş birer pattern'dir:

    - CQRS
    - MVC
    - MVP
    - MVVM
    - Presentation Model (or Application Model)

    MV ile başlayan pattern'ler ailesine __Model-View-\* (or MV\*)__ denir.

    Bu pattern'ler hem server hem client tarafta kullanılabilir.

    React, Angular, Android gibi framework'lerin sadece 1 tanesi ile yukarıdaki istediğimiz pattern ile yazabiliriz. Önemli olan yazım tarzımızdır. Fakat framework'ün best practice'leri bizi bir pattern'e yaklaştırabilir.

- # aspect oriented programming (or cephe yönelimli programlama or AOP)
    bu konu başka yerde de anlatılıyor.

    AOP, concern'leri birbirinden ayırmayı temel alan programlama felsefesidir.

# JSP model 1 Architecture vs JSP model 2 Architecture
model 1:

```
Client <--> JSP <--> Java-Bean(s) <--> Database
```

On above architecture, both JSP and Java-Bean(s) may have the responsibility of "Controller" (C of MVC). For that reason model 1 does not fit to MVC architecture.

model 2:

```
Client <--> Controller(Servlet) <--> JSP <--> Java-Bean(s) <--> Database
```

Model 2 fit in MVC architecture. On this model:
- Java-Bean(s) are representation of model (M of MVC)
- JSP is the View of MVC
- Controller(Servlet) is the C of MVC

In model-2 architecture, JSP's and Java Beans may contain business logic but it's not mostly recommended.

# MVC (or Model-View-Controller)
Flux vs MVC başka başlıkta anlatılıyor.

Smalltalk firması 1980'lerde MVC denilen yapıyı ortaya atmıştır.

MVC'de controller dolaylı yoldan view'a bağımlıdır. controller'ın bir metotunu çağırıken, view yoksa muhtemelen exception alırız. çünkü örneğin; muhasebe sayfamızda kullanıcının parası bittiyse "0 TL" kırmızı ile gösterilecektir. bu sebeple unit test controller'ların metotlarını çağırarak yapamıyoruz. (Bu sebeple MVP, MVC'den türetilmiştir.)

bir Android projesinde ilk düşünüldüğünde MVC şunlara karşılık gelebilir:
- M: herhangi bir sınıftaki data sınıfı yada objesi
- V: layout dizinindeki XML dosyamız
- C: activity sınıfımız

oysa bu bakış açısı her zaman doğru değildir. programı yazarken mimariyi biz tasarlamaktayız. örneğin; layout.xml oluşturmayıp, tüm GUI elementlerini activity'mizde (Java kodumuzda) dinamik oluşturabiliriz. araştırma yapılırsa MV* ailesinden birçok pattern'in de Android projelerinde kullandığı görülebilir.

MV* ailesindeki pattern'ler sadece önyüz için tasarlanmamıştır. Bir projenin bütünü iyice incelenirse birçok kısmında MV* ailesinden pattern'ler görebiliriz. Örneğin sunucu tarafta REST controller'ımızda da MVC görebiliriz.

Model sınıfı, sadece bilgilerin tutulduğu sınıf değildir. business logic'te burada olduğu unutulmamalıdır. Controller sadece view ve model arasında bir aracıdır.

Aşağıda MVC'nin temel şeması çizilmiştir. View, Model'dan data'ları gözlemlemek (observe) etmekle yükümlü. Controller ise Model'de update'ler gerçekleştiriyor.

Aşağıdaki şekilde yıldız (*) prefix'ine sahip olan text, ok işaretinin yaptığı örnek bir aksiyondur.

```
*show
 > > > >  User > > > > >*click
^                      v
^                      v
View               Controller
v                      v
v                      v 
> > > > > Model < < < <  *write
*observe
```

Şekil için kaynak: (source-id: 409) "A Pattern Language for MVC Derivatives", authors: Takashi Kobayashi and Sami Lappalainen.

Yukarıdaki şekilde "View" ile "model" arasındaki ok işaretinin yönünü diğer türlü çizenler de var. Bu biraz çizimin nasıl algılanacağı ile alakalı bir durum. Arkaplanda herkesin bahsetmek istediği şey aynı oysa.

Yukarıdaki şekilde tam gösterilmese de "view", controller'daki event'leri tetikliyor. Aslında user view'a tıklamış oluyor. (Şekilden farklı anlaşılabilir.)

Yine yukarıdaki şekilde controller ile view arasına şu görevi gören çizgi çizilebilir: User event'lerine göre Controller, farklı view'ı initialize edebilir.

MVC'yi basit bir pseudo-code üzerinde gösterirsek:

```java
class MyController {

    MyController(MyView view, MyModel model) {
        this.view = view;
        this.model = model;
    }

    void onEventX(int buttonNumber) {
        model.setPoints(buttonNumber);
        view.showAlertBox("Your points changed as " + buttonNumber);
        view.setAlertBoxVisiblity(true);
    }
}
```

# MVP (or Model-View-Presenter)

MVC'deki "controller" yerine "Presenter" gelir, ve MVC'deki "View" artık daha çok View değişikliklerinden de sorumludur. pseudo-code bir örnekle ilerleyelim:

```java
class MyPresenter {

    MyPresenter(MyView view, MyModel model) {
        this.view = view;
        this.model = model;
    }

    void onEventX(int buttonNumber) {
        model.setPoints(buttonNumber);
        view.showPoints(buttonNumber); //it does not cares what views does. view can show alertbox or can show small text inside screen.
    }
}
```

Burada MyView bir interface. MyView'ın View tarafında implemente edilmesi gerekiyor. Yani view, her olayda kendinde nelerin güncelleneceğini belirlemesi gerekiyor. Dolayısı ile view'ı mock'layıp, presenter'ın metotlarını çağıran Unit testler yazabiliriz.

Yani; MVC'de view'a daha spesifik ne yapması gerektiğini söylüyorduk. Oysa MVP'de View'ın abstract/arayüzini yönetiyoruz, yani daha genel/yüzeysel bir View-API'si kullanabiliyoruz.

Bu konu burada sade kod örnekleriyle açıklanmış: (source-id: 411) Linkteki projelerin gerçek kod örnekleri burada: (source-id: 412)

MVP ikiye ayrılıyor:

- # Passive View

  Presenter, modeli güncelledikten sonra view'a yeni model'i yollar. örnek:

  ```java
  view.showPoints(buttonNumber);
  ```

  view'ın model değişikliğinden haberdar olabilmesi için, Presenter'ın view'a bunu bildirmesi gerekir.

  Aşağıdaki şekilde yıldız (*) prefix'ine sahip olan text, ok işaretinin yaptığı örnek bir aksiyondur.

  ```
        User
        ^ v 
  *show ^ v *click
        ^ v
        ^ v
        ^ v
        ^ v   *onEventX
        View  > > > > >  Presenter
              < < < < <         v
              *showAlert        v
                                v
                                v
                                v
        Model  < < < < < < < < *write
  ```

  Şekil için kaynak: (source-id: 409) "A Pattern Language for MVC Derivatives", authors: Takashi Kobayashi and Sami Lappalainen.

- # Supervising Controller

  passive'dekinin tersine, modelde yapılan bir değişiklik otomatik olarak view tarafından bilinir. view kendini update eder. bunun için binding yapılması şarttır.

  ```java
  model.setPoints(buttonNumber);
  view.showPoints();
  ```

  Aşağıdaki şekilde yıldız (*) prefix'ine sahip olan text, ok işaretinin yaptığı örnek bir aksiyondur.

  ```
        User
        ^ v
  *show ^ v *click
        ^ v
        ^ v
        ^ v   *onEventX
        View  > > > > >  Presenter
        v     < < < < <          v
        v     *showAlert         v
        v                        v
        v                        v
        v *read                  v
        Model  < < < < < < < < < < *write
  ```

  Şekil için kaynak: (source-id: 409) "A Pattern Language for MVC Derivatives", authors: Takashi Kobayashi and Sami Lappalainen.

# MVVM (or Model View ViewModel)
Bazı kaynaklarda __Model–View–Binder__ olarakta isimlendirilir.

Presentation Model'den sonra, Microsoft yazılımcısı John Gossman tarafından, 2005 yılında ortaya atılmıştır.

KnockoutJS, MVVM yapısı üzerine kuruludur.

MVVM'de Presenter yerine ViewModel kullanılıyor.

MVVM'de data binding (yada reactive tarzı stream'ler) kullanmak şart. Çünkü; View, ViewModel'a erişiyor fakat tersi yapılamıyor. ViewModel, modele erişebiliyor fakat tersi yapılamıyor. Bu sebeple MVVM projelerinde çoğunlukla MVVM altyapısı sunan framework'lerden yararlanılır. örnek olarak; data binding özelliği Android tarafından destekleniyor: (source-id: 415).

View, model'deki verilere data binding yapar. Ve event'leri ViewModel'a bildirir. ViewModel, model'i günceller. modelde olan değişiklik, view'a, viewModel aracılığı ile binding olduğu için otomatik yansır.

View code:

```html
<Button
  style="red"
  onClick="@{viewModel.onEventX(buttonNumber)}"
  text='current points: @{viewModel.points} . Click to update your points'
/>
```

```java
class MyViewModel {

    // "ObservableField" is an example from Android "Data binding API".
    // But every framework has different API.
    public final ObservableField<String> points = new ObservableField<>();

    void onEventX(int buttonNumber) {
        points.set(buttonNumber);
    }
}
```

```
      User
      ^ v
*show ^ v *click
      ^ v
      ^ v
      ^ v      *onClick
      View  > > > > > > > > > > > > > ViewModel
                                      v  ^
                              *write  v  ^ *on-model-change-event
                                      v  ^
                                      Model
```

Şekil için kaynak: (source-id: 409) "A Pattern Language for MVC Derivatives", authors: Takashi Kobayashi and Sami Lappalainen.

# Comparison Table

| Pattern  | Project size            | Separation of Concerns | Code complexity | Modifi-ability | Testability | Requires view sync framework |
|----------|-------------------------|------------------------|-----------------|----------------|-------------|------------------------------|
| MVC      | Small/Medium            | Fair                   | Low             | Low            | Fair        | Yes                          |
| MVC2     | Medium/Enterprise       | Good                   | Medium/High     | Low            | Good        | No                           |
| MVP (SC) | Medium/Enterprise       | Fair                   | High            | High           | Fair        | Yes                          |
| MVP (PV) | Small/Medium/Enterprise | Good                   | High            | High           | Good        | No                           |
| MVVM     | Medium/Enterprise       | Good                   | Medium/High     | Low            | Very good   | Yes                          |

kaynak: (source-id: 409) "A Pattern Language for MVC Derivatives", authors: Takashi Kobayashi and Sami Lappalainen.

# Presentation Model (or Application Model)
Bu MVC ve türevlerine alternatiftir.

Martin Fowler tarafından 2004 yılında ortaya atılmıştır. MVP'den sonra ortaya atılmış, MVP'ye çok benzemektedir.
