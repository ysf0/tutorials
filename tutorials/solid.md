############################

############################
# SOLID
############################

############################

# SOLID prensipleri
object orianted için çıkmış 5 tane prensibi birarada bulunduran bir terimdir (baş harflerini birleştirilmiştir): SRP, OCP, LSP, ISP, DIP.

## Single Responsibility Principle (or SRP or Tek Sorumluluk Prensibi)
Bir sınıfın yahut metotun tek bir sorumluluğu olmalıdır. eğer metotun/sınıfın değişmesi gerekiyorsa; muhtemelen ona yeni sorumluluklar mı eklenecek şüphesi yaratmalıdır.

## Open/closed principle (or OCP)
code/software should be open for extension, but closed for modification. yani; yeni eklemeler yapıldığında programda minimum değişiklik yeterli olabilmelidir. örneğin; online ödemeler. yeni bir ödeme geldiğinde yeni ödemeyi bir sınıftan implemente edip bir listeye eklememiz yeterli olabilmelidir.

Farklı bir değişle; yeni geliştirme geldiğinde; varolan kodumuzu az düzenlemeliyiz fakat yeni sınıflar yaratmalıyız. Bunu ne kadar iyi yapabiliyorsak, kodumuz OCP'ye o kadar yakındır.

2 gerçek örnek:
- Observer pattern. Yeni observer class'ları yarattığımızda, subject'i değiştirmeye gerek kalmıyordu.
- JDBC-driver. Yeni driver eklediğimizde, sistemde daha önceden kullanılan driver'ları hiç değiştirme gereği duymuyoruz. 

## Liskov'un Yerine Geçme Prensibi (or Liskov Substitution Principle or LSP)
Alt sınıflardan oluşan nesnelerin, üst sınıfın nesneleri ile yer değiştirdikleri zaman, aynı davranışı sergilemesi gerekmektedir.

implementasyonlarımızda not-implemented hatası fırlatan metotumuz varsa, bu kuralı ihlal ediyoruz anlamına gelir.

Örneğin Ördek sınıfımız olsun. Bu sınıftan oyuncak örnek ve gerçek ördeği implemente edelim. gerçek ördeğin fly metotu varken, oyuncak ördeğin fly metotu not-implemented fırlatacaktır. Bu durumda alt sınıfı üst sınıf ile yer değiştirirse kodumuz hata verecektir. Bunu istemiyoruz. Bunun için farklı çözümlere gidilebilir. Örneğin; UçanÖrdek (sadece fly metotunu implemente eder) ve YüzenÖrdek arayüzlerimizi yazarız. Her implementasyon birkaç hangi özellikleri destekliyorsa sadece onları implemente eder.

## Interface Segregation Principle (or ISP or Arayüz Ayrımı Prensibi)
Direk örnek üzerinden gidelim: Mesaj arayüzümüz olsun. bunu implemente eden bir MesajImpl sınıfımız olsun. MesajImpl kendi içinde attachmentVideo, attachmentPhoto gibi özellikler içerecek. fakat her mesajda video olmayabilir. sadece foto olabilir. bu sebeple burada önerilen; birden fazla MesajImpl olsun ve her biri video için yada photo için spesifik geliştirilsin. (bir mesajda hem foto hem video olamayacağını varsayarak örnek verilmiştir). bu şekilde her implementasyon sadece tek bir işe odaklı yani; arayüzün metotlarını implemente etmeye odaklı olmalıdır. böylece kullanılmayan metotlar çıkarılmış olacaktır.

## Bağımlılığın Ters Çevrilmesi Prensibi (or Dependency Inversion Principle or DIP)
iki kuralı vardır:

1. High-level modules should not depend on low-level modules. Both should depend on other high levels.

2. Abstractions should not depend on details. Details should depend on abstractions.

Burada; High level'dan kasıt şudur: üst seviyeli sınıf alt seviyeli sınıf'ın metotlarını çağırarak işlem yaratır. Örneğin; shopping servisi, ödeme servisini çağırarak işlem yapar.

Yukarıdaki iki maddeden çıkaracağımız şudur: Üst seviyeli modüller/sınıflar, alt seviyeli sınıflara/modüllere bağımlı olmamalıdır. Alt seviyeli modüller üst seviyeli modüllere(modüllerin arayüzlerine) bağımlı olabilir.

Örnek üzerinden gidelim; online ödemeler yapılacaktır. Birçok online ödememiz mevcut. Shop abstract'ımız (burada üst seviyeli sınıf/modül oluyor) online ödemeleri bu şekilde kullanıyor olsun:

```java
public abstract Shop {

private TaksitliOdeme taksitliOdeme;
private KrediKartiOdeme krediKartiOdeme;

public ode(){

    if(taksitliOdeme){
        alert("Taksitli ödeme için vade farkı alınacaktır");
        taksitliOdeme.ode();
    } else if(krediKartiOdeme){
        krediKartiOdeme.ode();
    }
}
```

DIP prensibi yukarıdaki durumun yerine tüm ödemeleri bir arayüzden extend edip, bu arayüzü Shop sınıfına inject edip kullanmamızı öneriyor. Çünkü aksi durumda ödeme sistemlerinde olacak bir logic değişikliği, shopping class'ında değişikliğe sebep olacaktır.
