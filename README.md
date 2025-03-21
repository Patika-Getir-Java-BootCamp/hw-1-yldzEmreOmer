[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/7TXVPuTD)
## 1- Why we need to use OOP? Some majore OOP languages?

OOP (Object-Oriented Programming), yazılım geliştirmede işleri daha düzenli, yönetilebilir ve tekrar kullanılabilir hale getirmek için kullanılır. Bir sürü kolaylığı ve kullanım detayı var ben bunlardan 3 tanesini açıklayacağım.

* Kodun Düzeni ve Yönetilebilirliği –> Kodları class ve object şeklinde organize ederiz. Mesela bir araba üretim sistemi yazıyorsak, Arabalar diye bir class oluşturup, markalara özel arabaları object olarak yaratabiliriz.
* Kod Tekrarını Azaltma (Reusability) -> Aynı kodu tekrar tekrar yazmak yerine, ortak özellikleri olan nesneleri inheritance (kalıtım) ile türetebiliriz. Klasik örneklerden biri de bir hayvan sınıfı yazıp, köpek ve kedi gibi alt sınıflar türetebiliriz.
* Gerçek Dünya Modellemesi –> Nesne tabanlı programlama, günlük hayattaki şeyleri kod içinde daha iyi ve kolayca temsil etmemizi sağlar.

##### En Popüler OOP Dilleri:

Java, OOP denince akla ilk gelen dillerden biri, C#, Microsoft dünyasında OOP’nin en güçlü temsilcisi, C++, ve python gibi diller OOP kullanır.

*Özetle, OOP kod yazmayı daha düzenli, tekrar kullanılabilir ve anlaşılır hale getiriyor. Büyük projelerde işleri kolaylaştırıyor ve gerçek dünya nesnelerini kod içinde daha iyi modellememizi sağlıyor.*



## 2- Interface vs Abstract Class? 

Öncelikle kısaca ikisini de tanıtayım daha sonra farkına geçelim. 

İnterface, tamamen soyut bir yapıdır ve sınıfların hangi metodları uygulamak zorunda olduğunu tanımlar. Ancak bu metodların nasıl uygulanacağını belirtmez.

Abstract class, hem soyut metodlar içerebilir hem de normal metodlar içerebilir. Yani, bazı işlevleri hazır sunarken, bazılarını alt sınıfların tanımlamasını ister.

**Farklar:**

- Interface içindeki metotlar gövdesizdir abstract olmak zorundadır, yani sadece ne yapacağını söyler ama nasıl yapacağını belirtmez. Abstract class içinde ise hem soyut (abstract) hem de normal (gövdeli) metotlar bulunabilir. Yani bazı işlemleri hazır olarak sunabilirken, bazılarını alt sınıflara bırakabilir.
- Interface içinde tüm değişkenler otomatik olarak public static final olur. Yani sabittirler ve değiştirilemezler. Abstract class içinde normal değişkenler tanımlanabilir ve bunlar değiştirilebilir.
- Bir sınıf birden fazla interface’i implemente edebilir. Yani çoklu kalıtım interface ile mümkündür. Bir sınıf sadece bir abstract class’ı extend edebilir, çünkü Java çoklu kalıtımı desteklemez.
- Interface içindeki metotlar otomatik olarak public kabul edilir ve private veya protected olamazlar. Abstract class içinde metotlar private, protected, public gibi farklı erişim belirleyicilerle tanımlanabilir.

**Hangisini Kullanmalıyım?**

- Eğer birden fazla sınıfa ortak bir davranış kazandırmak istiyorsan → Interface kullan.
- Eğer bir temel sınıf oluşturup bazı işlevleri hazır sunmak istiyorsan → Abstract class kullan.
- Eğer çoklu kalıtıma ihtiyacın varsa (çünkü Java'da extends sadece bir kez kullanılabilir) → Interface kullan



## 3- Why we need equals and hashcode? When to override?

Java'da nesneleri karşılaştırmak ve veri yapılarında verimli bir şekilde saklamak için equals() ve hashCode() metodlarını kullanırız.

**equals() Metodu:**

equals(), iki nesnenin içerik açısından aynı olup olmadığını kontrol etmek için kullanılır. Eğer override etmezsek, Java varsayılan olarak bellekteki adreslerini karşılaştırır (== operatörü gibi davranır). Bazen iki nesnenin bellekte farklı adreslerde olması önemli değildir, önemli olan içeriklerinin aynı olup olmadığıdır.

**hashCode() Metodu:**

hashCode(), bir nesneye ait integer (tamsayı) değeri döndüren bir fonksiyondur. HashMap, HashSet gibi koleksiyonlarda verimli arama yapmak için kullanılır. Eğer hashCode() override edilmezse, aynı içeriğe sahip nesneler farklı hash değerleri alabilir, bu da koleksiyonların yanlış çalışmasına neden olabilir.

**Ne Zaman equals() ve hashCode() Override Etmeliyiz?**

* Eğer nesnelerin içeriklerine göre karşılaştırılmasını istiyorsak (id, isim, email gibi alanlara göre).
* Eğer nesneleri HashMap, HashSet, HashTable gibi koleksiyonlarda kullanacaksak.
* Eğer nesnelerin bellekteki adreslerine göre değil, mantıksal olarak eşit olup olmadığını belirlemek istiyorsak.



## 4- Diamond problem in Java? How to fix it?

Java'da Diamond Problem (Elmas Problemi), çoklu kalıtımın getirdiği bir çakışma sorunudur. Eğer bir sınıf, aynı metodu içeren iki farklı üst sınıftan türetilirse, Java hangi metodu çağırması gerektiğini bilemez ve derleme hatası verir. Java'da bir sınıf sadece bir sınıfı miras alabilir (single inheritance). Ancak birden fazla interface implement edebilir.

Diamond problem, bir interface varsayılan (default) metot içerdiğinde ve bu metot birden fazla yerde miras alındığında ortaya çıkar.

**ÇÖZÜMLER:**

* Override Ederek Çözme (En Yaygın Çözüm)
  Diamond problem'i çözmenin en kolay yolu, alt sınıfta (D) metodu kendimiz override etmektir
* En yaygın çözüm budur ancak süper anahtar kelimesini kullanarak da çözebiliriz. 
* Bir diğer çözüm yolu ise abstract sınıf kullanmak. Interface yerine abstract sınıf kullanırsak, zaten Java çoklu kalıtımı desteklemediği için diamond problem oluşmaz.



## 5- Why we need Garbage Collector? How does it work?

Java'da hafıza yönetimi (memory management) otomatik olarak yapılır. Eskiden C/C++ gibi dillerde, kullanıcıların manuel olarak yapması gerekiyordu. Eğer bir nesneyi kullanmayı bıraktıktan sonra belleği serbest bırakmazsan, memory leak (hafıza sızıntısı) oluşur ve program gereksiz bellek tüketerek çökmeye başlar.

Java'nın Garbage Collector'ü (Çöp Toplayıcı) sayesinde bu dert ortadan kalkar! Kullanılmayan nesneleri otomatik olarak tespit eder ve siler. Ana amacı gereksiz nesneleri temizleyerek bellek sızıntısını önlemek ve performansı artırmak. Adımlar: 

1. Java'da Garbage Collector JVM (Java Virtual Machine) tarafından yönetilir. Java'da bir nesne artık erişilebilir değilse, o nesne kullanılmıyor demektir ve silinebilir. Garbage Collector'ün temel algoritması "Mark and Sweep" olarak bilinir.
2. "Mark" (İşaretleme) aşaması: JVM, hangi nesnelerin hala kullanılabilir olduğunu belirler. Eğer bir nesneye ulaşılmıyorsa, silinebilir olarak işaretlenir
3. "Sweep" (Temizleme) aşaması: İşaretlenen gereksiz nesneler bellekten temizlenir ve yer açılır. Nesil bazlı bellek yönetimi yapar (Young & Old Generation).
4. Sistem ihtiyacına göre otomatik çalışır.

**Kısacası:** Java sayesinde belleği elle yönetmek zorunda kalmazsın, ama Garbage Collector'ün nasıl çalıştığını anlamak performans optimizasyonları için önemlidir.



## 6- Java 'static' keyword usage? 

Java'da static, sınıfa ait bir değişken, metot veya blok tanımlamak için kullanılır. Yani nesneye (instance) değil, sınıfın kendisine ait olur.Bunu şu şekilde düşünebiliriz:
📌 Normal bir değişken veya metot → Nesneye aittir
📌 Static bir değişken veya metot → Sınıfa aittir

Bu yüzden nesne oluşturmadan static bir değişkene veya metoda erişebilirsin.

1. Static Değişkenler:

   Eğer bir değişken static olarak tanımlanmışsa, bu değişken sınıfa ait olur ve tüm nesneler için ortak olur. Yani  her nesne için ayrı ayrı saklanmaz, tüm nesneler için ortaktır.Nesne üzerinden çağırmak yerine sınıf adıyla çağırmak daha doğru olur.

2. Static Metotlar:

   Bir metodu static olarak tanımlarsan, bu metoda nesne oluşturmadan doğrudan sınıf adıyla erişebilirsin. Örnek: 

   ~~~java
   ```
   class MathUtils {
       static int square(int x) {
           return x * x;
       }
   }
   
   public class Main {
       public static void main(String[] args) {
           System.out.println(MathUtils.square(5)); // Çıktı: 25
       }
   }
   ```
   /* Burada neden static?
   Çünkü "kare hesaplamak" gibi bir işlem nesneye özgü değil, genel bir işlemdir. Bu yüzden static olarak tanımlayarak doğrudan sınıf üzerinden çağırabiliyoruz.*/
   ~~~

⚠️ Dikkat!
Bir static metot, static olmayan (instance) bir değişkene veya metoda doğrudan erişemez! Çünkü static metotlar nesne oluşturmadan çalışır, ama instance değişkenler bir nesneye bağlıdır.

3. Static Bloklar
   static bloklar, sınıf yüklenirken (class loading) yalnızca bir kez çalıştırılan kod bloklarıdır. Genellikle bir defaya mahsus ayarlamalar (initialization) yapmak için kullanılır.
4. Static İç Sınıflar
   Eğer bir iç sınıfı (inner class) static yaparsan, o sınıfa dış sınıfın nesnesi olmadan erişebilirsin.

**Static Kullanırken Dikkat Edilmesi Gerekenler**

Nesneye özel değişkenleri static yaparsan, tüm nesneler ortak bir değişken kullanır ve beklenmedik sonuçlara yol açabilir.
Static metodlar içinde this veya super kullanamazsın çünkü bunlar nesneye özeldir.                                                                             Çok fazla static kullanmak OOP'nin avantajlarını azaltır. Nesne yönelimli programlama prensiplerine ters düşebilir.

**Ne zaman kullanılır?**

Ortak bir veri veya metod varsa (örneğin, Math.sqrt())
Nesne oluşturmak gereksizse.



## 7- Immutability means? Where, How and Why to use it- 

Immutability, bir nesnenin oluşturulduktan sonra değiştirilememesi anlamına gelir. Yani, bir nesne oluşturduğunda o nesnenin içindeki veriler değiştirilemez. Java’da en iyi bilinen immutable (değişmez) sınıf String’dir. Bir String nesnesini değiştirmeye çalıştığında, aslında yeni bir nesne oluşturuluyor.

```java
String s1 = "Hello";
s1 = s1 + " World";  // Yeni bir nesne oluşturuluyor!
System.out.println(s1); // Çıktı: Hello World

/*Burada s1 değişmiş gibi görünüyor ama aslında yeni bir "Hello World" nesnesi oluşturuldu ve s1 artık yeni nesneyi gösteriyor. Eski "Hello" nesnesi çöp toplayıcı (Garbage Collector) tarafından temizlenecek.*/
```

Bir sınıfın immutable olması için şu kurallara uymalısın:

1️⃣ Sınıfı final yaparak kalıtımı engelle
2️⃣ Tüm değişkenleri private final yap
3️⃣ Değişkenleri setter metotları ile değiştirmeye izin verme
4️⃣ Mutable (değiştirilebilir) nesneleri korumak için defensive copy kullan
5️⃣ this referansını dışarıya sızdırma

**Ne Zaman ve Nerede Kullanılır?**

- Immutable nesneler thread-safe’dir. Birden fazla thread aynı anda immutable nesneyi değiştiremeyeceği için senkronizasyona gerek kalmaz.
- Immutable nesneler değişmeyeceği için önbelleğe alınabilir. Örneğin, Java’da String Pool immutable String nesnelerini saklar ve tekrar tekrar kullanır.
- Eğer bir nesneyi HashMap veya HashSet içinde anahtar olarak kullanacaksan, immutable olması hash kodunun değişmemesini garanti eder.
- Fonksiyonel programlama prensiplerinde değiştirilemez (immutable) veri kullanımı önerilir çünkü bu, yan etkileri azaltır ve kodu daha güvenilir hale getirir.

**Neden Önemli?**

* Immutable nesneleri senkronize etmeye gerek yoktur.
* Nesne değişmediği için, yan etkiler (side effects) oluşmaz.
* HashMap gibi koleksiyonlar için güvenli ve performanslıdır.
* Immutable nesneler, yanlışlıkla değiştirilemeyeceği için hata yapma ihtimalini azaltır.

Java’nın içinde zaten immutable olan bazı sınıflar vardır: String, Integer, Double, Boolean (Wrapper sınıflar),LocalDate, LocalTime, LocalDateTime immutable sınıflardır.



## 8- Composition and Aggregation means and differences? 

Composition ve Aggregation, Object-Oriented Programming (OOP)’de "Has-A" (Sahiplik) ilişkisini temsil eden iki farklı ilişki türüdür. 

Composition (Bileşim) → Bir nesne, başka bir nesnenin ayrılmaz bir parçasıdır.
Aggregation (Toplama) → Bir nesne, başka bir nesneyle ilişkilidir ama bağımsız yaşayabilir.
İkisi de Has-A ilişkisini temsil eder, ancak bağımlılık seviyeleri farklıdır.

**Composition**, bir nesnenin başka bir nesneye tamamen bağımlı olduğu ilişki türüdür. Eğer ana nesne yok olursa, bağlı nesne de yok olur. Gerçek Hayattan Örnekle daha iyi anlayabiliriz: 

- İnsan & Kalp → İnsan ölünce kalp de çalışmayı bırakır. 
- Araba & Motor → Araba olmadan motor tek başına işlevsizdir.

**Aggregation**, bir nesnenin başka bir nesneyle ilişkili olduğu ancak bağımsız yaşayabildiği bir ilişki türüdür. Eğer ana nesne silinirse, bağlı nesne silinmez. Gerçek Hayattan Örnek:

- Üniversite & Öğrenci → Bir öğrenci, bir üniversiteye kayıtlı olabilir ama üniversite yok olursa öğrenci var olmaya devam eder.
- Futbol Takımı & Oyuncular → Takım dağılırsa oyuncular yaşamaya devam eder.



## 9- Cohesion and Coupling means and differences?

**Cohesion**, bir sınıfın veya modülün kendi içinde ne kadar tutarlı ve odaklanmış olduğunu ifade eder. Yani, bir sınıfın yaptığı işler birbirine ne kadar bağlı ve anlamlı?

Yüksek Cohesion → Sınıf sadece belirli bir işi yapar ve o işe odaklanır. (Önerilen yaklaşımdır)
Düşük Cohesion → Sınıf çok farklı işlevleri içinde barındırır ve birçok sorumluluğu vardır. (Kod karmaşıklaşır)

ÖRNEK: 
Yüksek Cohesion: Bir OrderService sadece sipariş işlemleriyle ilgilenir.
Düşük Cohesion: OrderService içinde sipariş işlemlerinin yanı sıra, ödeme, kullanıcı doğrulama gibi alakasız işlemler de varsa cohesion düşüktür.

**Coupling**, iki farklı bileşen (sınıf, modül) arasındaki bağımlılık seviyesidir. Eğer bir bileşen başka bir bileşene aşırı bağımlıysa, coupling yüksek olur ve bu, değişiklik yapmayı zorlaştırır.

Gevşek (Loose) Coupling → Bileşenler birbiriyle minimum düzeyde bağlantılıdır. (Önerilen yaklaşımdır)
Sıkı (Tight) Coupling → Bileşenler doğrudan birbirine bağımlıdır ve değişiklik yapmak zorlaşır. (Kaçınılmalıdır)

ÖRNEK: 
Sıkı Coupling: PaymentService doğrudan OrderService'i çağırır ve değişiklik olduğunda her ikisini de düzenlemek gerekir.
Gevşek Coupling: PaymentService, OrderService ile bir arayüz (interface) üzerinden iletişim kurar, böylece bağımlılık azalır.

**Cohesion ve Coupling Arasındaki Farklar:**

* Cohesion, sınıfın kendi içindeki tutarlılığıdır; Coupling ise farklı sınıfların birbiriyle ne kadar bağımlı olduğudur.
*  Yüksek Cohesion her zaman iyidir, çünkü bir sınıfın tek bir sorumluluğa odaklanmasını sağlar.
*  Gevşek Coupling iyidir, çünkü sistemin esnek olmasını sağlar ve modüllerin bağımsız olarak değiştirilebilmesine olanak tanır.



## 10-  Heap and Stack means and difference?

Java'da bir program çalışırken, belleği yönetmek için Heap ve Stack olmak üzere iki ana alan kullanılır. Her ikisi de belleğin farklı kısımlarını temsil eder ve farklı türde verileri saklarlar.

**STACK**

Stack, metod çağrıları ve yerel değişkenler için kullanılan küçük ama hızlı bir bellek alanıdır. Özellikleri:

* LIFO (Last In First Out) prensibiyle çalışır. Yani en son eklenen veri ilk kaldırılır.
* Metod çağrıldığında, o metoda ait değişkenler stack'e eklenir.
* Metod tamamlandığında, ilgili değişkenler otomatik olarak stack'ten kaldırılır.
* Yerel değişkenler (int, double, boolean vb.) ve referanslar burada tutulur.

**HEAP**

Heap, Java’da nesnelerin (Object) tutulduğu büyük ve esnek bir bellek alanıdır. Özellikleri: 

* Dinamik bellek yönetimi sağlar.
* Tüm nesneler burada saklanır ve referansları Stack’te tutulur.
* Garbage Collector heap belleğini yönetir ve kullanılmayan nesneleri temizler.
* Daha büyük ve esnektir ama Stack’ten daha yavaştır.

``` java
   class Car { 
   		String brand;
}
public static void main(String[] args) {
    Car car1 = new Car(); // Heap bellekte saklanır, referansı stack’te tutulur
}

//Burada Car nesnesi Heap belleğe oluşturulur, ancak car1 referansı Stack içinde tutulur.
```

**Stack ve Heap Arasındaki Farklar**

1. Stack → Metod çağrıları ve yerel değişkenler için kullanılır.
   Heap → Nesnelerin saklandığı yerdir.
2. Stack çok hızlıdır.
   Heap daha yavaştır çünkü Garbage Collector yönetir.
3. Stack değişkenleri metod bitince yok olur.
   Heap nesneleri program çalıştığı sürece var olabilir.
4. Stack otomatik temizlenir.
   Heap Garbage Collector tarafından yönetilir.

Özetle; Küçük ve kısa ömürlü veriler için Stack kullanılır (primitive değişkenler, metod çağrıları). Büyük ve uzun ömürlü nesneler için Heap kullanılır (Nesneler, diziler).



## 11- Exception means? Type of exceptions?

Exception, Java programının çalışma zamanında (runtime) beklenmeyen bir durumla karşılaşması sonucu oluşan hatalara verilen isimdir. Bir exception oluştuğunda, program normal akışını kaybeder ve hata fırlatır. Java, bu hataları kontrol altına alabilmemiz için bir exception handling mekanizması sunar.

Java’daki exception’ları iki ana kategoriye ayırabiliriz:

- Checked Exception (Derleme Zamanı Hataları)
- Unchecked Exception (Çalışma Zamanı Hataları – Runtime Exceptions)

**Checked Exceptions (Denetlenen İstisnalar)**

Bu exception türü derleme (compile-time) aşamasında kontrol edilir. Yani, Java derleyicisi (compiler) bu tür hataları fark eder ve geliştiriciyi önlem alması için uyarır. Mutlaka try-catch bloğu içinde yakalanmalı veya throws ile üst metoda iletilmeli. Program çalışmadan önce tespit edilebilir. 

Örnek Checked Exceptions:

* IOException → Dosya bulunamazsa fırlatılır.
* SQLException → Veritabanı ile ilgili bir hata oluştuğunda.
* FileNotFoundException → Belirtilen dosya yoksa.
* InterruptedException → Thread kesildiğinde.

**Unchecked Exceptions (Denetlenmeyen İstisnalar)**

Bu tür exception’lar runtime sırasında oluşur ve derleyici tarafından kontrol edilmez. Yani, program çalışırken fark edilir ve try-catch bloğunda ele alınmazsa program çöker. Derleme aşamasında tespit edilmez. Çalışma zamanında (runtime) oluşur. Genellikle hatalı koddan kaynaklanır (örneğin, null referans kullanımı). 

Örnek Unchecked Exceptions:

* NullPointerException → null bir nesneye erişmeye çalışırken.
* ArrayIndexOutOfBoundsException → Dizinin sınırlarının dışına çıkıldığında.
* ArithmeticException → 0’a bölme işlemi yapıldığında.
* IllegalArgumentException → Metoda geçersiz argüman verildiğinde.



## 12- How to summarize clean code as short as possible?

Clean Code = Okunabilir, Bakımı Kolay ve Etkili Kod.

Okunabilir: Kod, açık ve anlaşılır olmalı, karmaşıklıktan kaçınmalı.
Bakımı Kolay: Değiştirmesi, genişletmesi ve hata ayıklaması zahmetsiz olmalı.
Etkili: Gereksiz karmaşıklık içermeden, problemi en iyi şekilde çözmeli.



## 13- What is method hiding in Java?

Method Hiding (Metot Gizleme), bir alt sınıfın (subclass) üst sınıftaki (superclass) aynı imzaya sahip static bir metodu yeniden tanımlaması durumunda ortaya çıkar. Ancak burada override (ezme) değil, gizleme (hiding) işlemi gerçekleşir çünkü static metotlar nesnelere değil, sınıfa aittir.

Nasıl Çalışır?

Sınıf adı üzerinden çağrıldığında, o sınıfa ait metot çalışır.
Nesne üzerinden çağrıldığında, referans tipine bağlı olarak çalışır.

**Özetle:** Eğer bir metot **static ise gizlenir (hiding), değilse override edilir (ezilir).**



## 14- What is the difference between abstraction and polymorphism in Java?

Abstraction (Soyutlama) ve Polymorphism (Çok Biçimlilik), Java'da nesne yönelimli programlamanın (OOP) temel prensiplerindendir, ancak farklı amaçlara hizmet ederler.

**Abstraction (Soyutlama) Nedir?**

Soyutlama, nesnenin sadece gerekli özelliklerini gösterirken, gereksiz detayları gizlemektir. Amaç, kullanıcıya nasıl çalıştığını göstermeden bir işlemi sunmaktır. Abstract class ve interface kullanılarak sağlanır.

Gerçek Hayattan Örnek: Bir araba kullanırken motorun iç yapısını bilmemize gerek yoktur. Sadece direksiyon çevirir, gaz-fren pedallarını kullanırız. Yani motorun detayları soyutlanmıştır.

**Polymorphism (Çok Biçimlilik) Nedir?**

Polymorphism, aynı isimli bir metodun farklı davranışlar sergileyebilmesini sağlar. Amaç, aynı metodun farklı sınıflarda veya aynı sınıfta farklı parametrelerle farklı şekillerde çalışmasını sağlamaktır. Method Overloading ve Method Overriding ile sağlanır.

Gerçek Hayattan Örnek:  Bir telefonun güç tuşu düşünelim.

* Kısa basarsak ekran açılır/kapanır.
* Uzun basarsak telefon kapanır veya farklı bir menü açılır.
* Aynı tuş, farklı şekillerde çalışır (çok biçimli davranır).

**Farklar:**

* **Abstraction ** ile detayları gizleriz, **polymorphism ** ile aynı metodu farklı şekillerde çalıştırırız.
* **Abstraction**, abstract class  veya  interface kullanılarak yapılırken, **polymorphism**  method overriding veya method overloading yoluyla gerçekleştirilir.
* **Abstraction**, nesnenin ne yaptığını tanımlar ancak nasıl yaptığına dair bir bilgi vermez, **polymorphism** ise aynı metodun farklı nesneler üzerinde farklı şekillerde çalışmasını mümkün kılar.

