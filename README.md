# Bu repoda teknik mülakat hazırlığı yapıyorum. Kendimce notlar alıyorum. <br/>
## Soruların herhangi bir sırası yoktur. Aklıma geldikçe ekleme yapıyorum. Yanlış/eksik gördüğünüz kısımları issue açarak belirtebilirsiniz.


### 1-) Multi-Inheritence javada nasıl sağlanır?
Multi-Inheritence yani çoklu kalıtım Java'da sağlanamaz. Diamond Problem dediğimiz bir problem ortaya çıkar. Bu problemi aşabilmek ve çoklu-kalıtımı uygulayabilmek için arabirimleri kullanırız (Interfaces). Implements keywordü ile bunu sağlarız ve bir classın, birden çok classın özelliklerine sahip olabilir olmasını sağlayabiliriz. <br/>

### 2-) Access Modifierlardan bahseder misin?
Javada 4 tane acces modifierımız mevcut. Bunlar; public, protected, default, private. Public kullanıldığında classımız veya metodumuz her yerden erişilebilirken, private kullanıldığında sadece o sınıf özelinde erişim söz konusudur. Protected modifierı ise class, paket ve subclasslar arasında kullanılabilir demektir. Hiçbir şey yazılmadığında Default modifier'ı devreye girer ve o classta ve pakette geçerli bir erişim sağlar. <br/>

### 3-) Spring Framework Nedir?
Spring açık kaynaklı Java tabanlı bir frameworktür. Anotasyon bazlı web geliştirme yapabileceğimiz bir modeldir. Uygulama ayağa kalkıyorken gereken configurasyonları hızlıca yapabildiği için geliştirmeyi kolaylaştırır. Sadece Business-Logic geliştirilerek bir projenin ayağa kalkması sağlanabilir.

### 4-) Bean Scope kavramı nedir? Kaç çeşit scope kavramı vardır?
Bean, Spring IOC container tarafından yönetilen nesnelere denir. Eğer bir metodu @Bean anotasyonu ile tanımlarsak Spring’in Application Context dediğimiz kısmına yüklemiş ve Spring tarafından yönetilen bir Bean üretildiğini belirtmiş oluruz. 
Scope kavramını ise bir kapsam alanı gibi düşünebiliriz. Spring’de ise 5 çeşit scope kavramı vardır. Bunlar; <br/>

a- Singleton <br/>
b- Prototype <br/>
c- Request <br/>
d- Session <br/>
e- Global Session <br/>

a-) Singleton Scope : Bir nesnenin sadece bir instance'ı vardır ve yenisi üretilmez. Her request ile aynı nesne paylaşılır.  Default olarak her bean Singleton'dır. <br/>
b-) Prototype Scope : Bir nesnenin birden çok instance'ı vardır. Her request için yeni bir instance oluşturulur. Bir bean'i Prototype tanımlama yapabilmek için @Scope("prototype") eklenmelidir. Çok Threadli Uygulamalar için ideal. <br/> 
c-) Request Scope : Her HTTP isteği geldiğinde oluşturulur. API call yapıldığında, controller isteği aldığında, service methodunu çağırır ve yeni bir Bean API response olarak geri gönderilene kadar aynı instance kullanılır. Fakat yeni bir HTTP Request geldiğinde, farklı bir instance oluşturulur. <br/>

### 5-) Hibernate ve JPA arasındaki farklar nelerdir?
Java Persistence API bir spesifikasyondur, kurallar bütünüdür. Kendi başına bir şey yapamaz, implementasyonlara ihtiyaç duyar. Bu implementasyonlardan bazıları şunlardır; <br/>
Hibernate JPA, EclipsLink, Open JPA <br/>
Hibernate, Java geliştiricileri için geliştirilmiş bir ORM kütüphanesidir. Nesne yönelimli modellere göre veritabanı ile olan ilişkiyi sağlar, veritabanı işlemlerini kolaylaştırır. <br/>

### 6-) Bir proje için database tercihini nasıl yaparız? Hangi database'in projemize uygun olduğunu nasıl belirleriz?
Birçok faktörü mevcuttur. Öncelikle nasıl veriler tutacağız? Saklayacağımız veriler yapısal(stuctured) mı, yoksa Semi-sturctured mı, yoksa Unstructured mı bunları belirlemeliyiz.<br/>
a-) Query Patterns (Atılacak Sorguların kalıpları) <br/>
Hangi fieldlara göre sorgulama yapılacak? Ne tarz sorgulamalar yapılacak. Birçok alana göre sorgulama yapılacaksa MySQL, Oracle gibi güçlü veritabanı seçimleri yapılması gerekirken, sadece key'lere göre arama yapılacaksa key-value database seçilebilir. örn: redis. Metinlerden arama yapılacaksa Elasticsearch gibi gibi. <br/>
b-) Consistency (Tutarlılık) <br/>
Kullanacağımız veritabanı ne kadar tutarlı? Bir veriyi yazdıktan hemen sonra okuma yapacaksak güçlü ve tutarlı bir veritabanına ihtiyacımız var. Önce yazma, hemen ardından okuma yapmak için vs. MySQL, PostgreSQL gibi tutarlı veritabanları, doküman bazlı veritabanlarından(mongo db) daha iyi bir tercihtir. <br/>
c-) Storage Capacity (Ne kadar kapasite lazım? Uygulamanın kapsamı nedir?) <br/>
Veritabanı sistemleri disk'in alanıyla sınırlıdır. Dünya dolusu data tutacaksak daha az maliyetli olduğu için S3 seçilebilir. <br/>
d-) Performance (Sorgularımız ne kadar hızlı?) <br/>
Okuma-Yazma hacmi arttıkça sorguların dönüş değeri ms cinsinden giderek artar. Daha yavaş çalışan bir sistemimiz olur. Bunu istemiyorsak Amazon'un DynamoDB'si örneğin bir çözüm olabilir. <br/>

### 7-) Array & ArrayList farkları nelerdir? <br/>
Arrayler yani diziler sabit uzunlukta tanımlanırlar ve boyutları değiştirilemez. ArrayListte ise kısıtlama yok, eleman eklendikçe boyutu artar. <br/>
ArrayListlerde tutulacak olan tip Reference-Type olacağı için aslında o reference-type tipe ait olan fonksiyonlarını da kullanabildiğimiz bir yapı kurmuş oluyoruz. <br/>
Fakat Arrayler genellikle statik ve sabit boyutlu oldukları için ArrayListlere göre daha hızlıdırlar. <br/>
Dizi tanımlamada elemanların tipini belirlememiz gerekiyor ArrayListlerde ```<Object>``` keywordüyle bu sorunu ortadan kaldırıyoruz. Farklı tipte veriler ekleyebiliyoruz.
<br/>

```
        ArrayList<Object> myList= new ArrayList<>();
        myList.add(1);
        myList.add("abc");
        System.out.println(myList);

Process finished with exit code 0
[1, abc]
```
<br/>

### 8-) HTTP Methodları nelerdir? Açıklar mısın? <br/>
4 adet ana HTTP methodunu sıklıkla kullanırız. Bunların dışında da HTTP Methodları mevcuttur fakat en çok kullandığımız 4 metodu açıklayacağım. <br/>
a-) GET <br/>
Get metoduyla bir sunucudan veri almak için "request" oluşturabiliriz. Bunun karşılığında ise bir "response" alırız. Bu response içerisinde StatusCode, Header, Body ve içerikleri olur. StatusCode, eğer Get isteği başarılıysa 200'dür. Bu başarılı bir Get isteğine işaret eder. Header içerisinde ise nasıl bir tip dönüldüğü yazar. Mesela json formatta bir response döndüğünü söyleyebilir. Body içerisinde ise response vardır. <br/>
b-) POST <br/>
Post metodu bir sunucunun kullandığı veritabanına kayıt eklemek için kullandığımız HTTP metodudur. Doğru bir şekilde istekte bulunduysak, StatusCode=201 Created olmalıdır. <br/>
c-) PUT <br/>
PUT metodu, bir kaydı başka bir kayıtla güncellemek için kullanılır. Tüm alanlar güncellenir. İlgili kaydın sadece bir alanını güncelleyemeyiz. Eğer başarılı bir istek yaparsak karşılığında StatusCode=200 alabiliriz. Bu uygundur. <br/>
d-) DELETE <br/>
Bu metodla veritabanından bir kaydı silebiliriz. <br/>

### 9-) Java ile Solidity teknolojilerini birlikte kullanarak bir uygulama yapabilir miyiz? Web3 geliştirmede Java ne işe yarar? Nasıl deployment yapılır? Javanın rolü ne olur? <br/>
Evet, Java ve Solidity programlama dillerini kullanarak birçok geliştirme yapılabilir. Son dönemde bunu en iyi açıklayan rol, "Blockend Developer" rolüdür. Geleneksel Backend geliştirme ile Blockchain kavramlarının harmanlanmış halidir. <br/>
Java, web3 geliştirmede ethereum ağına bağlanmak, akıllı sözleşmeleri okumak, state değişikliği yapmak için kullanılabilir. Javada bu işler için kullanılan Web3j kütüphanesi popüler bir Web3 kütüphanesidir. <br/>

![ornek](https://github.com/bkizilkayaa/calisma-notlarim/assets/88281419/b0a57592-98bf-489d-b367-3ef7d6f7200b)
<br/>

### 10-) Versiyon Kontrol Sisteminin kullanıldığı bir projenin ilerletildiğini, fakat kullanılamaz halde olduğunu varsayalım. Uygulamanın çalışır halini nasıl elde ederiz? <br/>
Uygulamanın çalışır haline son sağlıklı commite giderek ulaşabiliriz. HEAD pointer, uygulamadaki commitler arası gezen bir pointerdır. Bu pointer, son sağlıklı commitin hash id'sini point edebilir. Bu sayede uygulamanın son çalışır haline erişilebilir. Hatalı değişiklikler geri alınabilir. <br/>

### 11-) Backend uygulamanın testlerini neyle yazarız? Sen test yazarken ne kullanıyorsun? (Burada test yazmak hakkında ne düşündüğüm ölçüldü bence) <br/> 
JUnit, Java'da en çok kullanılan test frameworkü. Ben de uygulamalarımı JUnit kullanarak yazıyorum. Anotasyon bazlı testler yapılabilir, her testten önce ve sonrasında ne yapılacağı belirlenebilir. JUnit bu geliştirmeleri kolaylastiriyor ve sadece business-logic'e bağlı kalmamızı sağlıyor. <br/>

### 12-) Transaction Nedir? <br/>
Transactionlar bir işlemler bütününü ifade eder. Veritabanlarındaki Transaction, Insert,Update gibi sorguların herhangi birinde hata çıkması halinde, o işlemin ROLLBACK edilmesini sağlar. Transactiondaki operasyonların her birinin(Insert,Update) gibi işlemlerin başarılı olması halinde ise Transaciton'ı commitler. Bu sayede ACID kavramı da sağlanmış olur. <br/>
A. Atomicy: Tüm işlemler başarılı olduğu taktirde Transaction onaylanır. Bu Bölünmezliği sağlar. <br/>
C. Consistency: Tutarlılık, Transaction tamamlanana ve commit edilene kadar karşımıza çıkan değerler aynıdır. Ancak transaction bitince etkilenir ve değişir. Bu da tutarlılığı sağlar. <br/>
I. Isolation: Dış müdahaleye kapalıdır. Başka bir transaction'dan etkilenmez. Kendini bu sayede izole eder. <br/>
D. Durability: ROLLBACK yapan mekanizmadır. <br/>

### 13-) AOP Nedir?<br/>
Aspect Oriented Programming bir programlama paradigmasıdır. Bu paradigmayla, tekrar eden kod kalabalığının önüne geçilmesi ve kodun maliyetinin düşürülmesi hedeflenmektedir. <br/>
Cross Cutting Concern nedir? <br/>
Uygulamanın herhangi bir bölümünde ``` logging, performance, transaction management, security, caching, validation, exception handling``` gibi işlemler gerçekleştirilebilir. CCC, o bölgelerden bağımsız olarak bu tarz sürekli kullanılan kod bloklarının işlemlerini gerçekleştirir. <br/>
AOP ise, CCC uygulayan bir paradigmadır. <br/>

### 14-) IoC Container Nedir? <br/>
Spring Framework'ün çatısı olan IoC Container program akışını ve Bean yaşam döngüsünü kontrol eder. <br/>
Uygulama başlatıldığında tüm dosyaları tarar ve anotasyonlarla işaretlenen Classları tarayıp Bean'leri ayıklar. Bu Bean'lerin instance'larını Singleton olacak şekilde oluşturur ve Application Context e yükler. <br/>
Application Context, bir memory gibi davranır. IoC prensiplerinin uygulamasıdır. <br/>

### 15-) Dependency Injection Nedir? <br/>
Dependency Injection, birbirine ihtiyaç duyan sınıfların injection'ını loosely-coupled olacak şekilde sağlar. Uygulamamızdaki katmanların bağımlılıklarının okunabilirliğini arttırır. <br/>
Bu ifadeyi daha da Türkçeleştirelim ve anlam kazandıralım. <br/>
Dependency Injection'ın Constructor Injection, Setter, Field gibi Injection yöntemleri mevcut. <br/>
Örneğin, bir servis başka bir servisin metotlarına ihtiyaç duysun. Bu case sıklıkla karşımıza çıkan bir casedir. Muhtemelen ihtiyaç duyan ve ihtiyaç duyulan servisler @Service anotasyonu ile işaretlenmiştir ve IoC Container tarafından Application Contexte yüklenmiş ve instanceı oluşturulmuştur. <br/>
Dependency Injection pattern'ı ise bu ihtiyaç duyan servisin constructor'ına/setter'ına ihtiyaç duyulan servisin instance'ının inject edilmesidir. <br/>

### 16-) IoC Container ile Dependency Injection farkı nedir? <br/>
IoC Container ve Dependency Injection Spring Framework'ün kullandığı patternlardır. <br/>
Temel farkları ise, IoC Container Bean oluşturma ve yönetme işlemlerinden sorumluyken, DI bu Beanler'in Inject edilmesinden sorumludur. <br/>
Her defasında bir bağımlılığa sahip olan servis içerisinden ```new``` keywordü ile nesne oluşturamayız. <br/>
Application Context'te oluşturulan Bean instance'ını tekrar tekrar kullanabilir ve inject edebiliriz. <br/>
Oluşturma ve yönetme işi IoC Container sorumluluğundayken, Inject etme yöntemleri Dependency Injection sorumluluğundadır. <br/>

### 17-) @Controller ile @RestController Anotasyonu arasındaki fark nedir? <br/>
@Controller anotasyonu ile Html ve statik sayfalarla çalışabileceğimizi belirtiyorken (DispatcherServlet), <br/>
@RestController anotasyonu ile RESTful web servisler dönebiliyoruz. (Json formatta veriyi döner, ResponseBody içerisinde) <br/>

### 18-) DispatcherServlet Nasıl çalışır? <br/>
DispatcherServlet, HTTP isteklerini bekler ve handle eder. Gelen bu ilk isteği handlerMapping karşılar. handlerMapping, bu HTTP isteğinin hangi modelle (Entity) ile çalışacağını tespit eder. <br/>
Ardından handlerAdapter, hangi HTTP metodun çalıştırılacağını "HEADER" kısmından okur, gerekli metotları çalıştırır ve en son gereken sonuç response adı altında dönülür <br/>
RestController'a gelen isteği debug ettiğimde aslında çokça uzun bir süreç çıkıyor karşıma fakat bu şekilde özetlenebilir. Her şeyi bilemeyiz. Çok fazla class'ta doğrulamalar vsvs. yapılıyor çünkü.. <br/>

### 19-) Maven vs Gradle? Farkları nelerdir? <br/>
Öncelikle Maven ve Gradle, build toollardır. Bu build toollar günün sonunda aynı işleri yaparlar. Configurasyon dosyamızdaki kodları okurlar, uzak sunucudan gereken bağımlılığı projemizde kullanılmak üzere indirirler. <br/>
Bize de bu bağımlılıkları kullanıp ortaya ürün çıkartmak kısmı kalır. <br/>
Maven, Gradle'a göre daha eski bir build tool olduğu için şuan daha yavaş build etmesine rağmen daha çok kullanılıyor. <br/>
Maven xml, Gradle ise JSON olarak configleri tutuyor. <br/>
Maven build edilirken her şeyi silip en baştan yüklemeye çalıştığı için daha uzun süreler boyunca beklememizi gerektiriyorken, Gradle, cache mekanizması sayesinde sadece değişikliklerin yapıldığı kısımları build ederek zamandan tasarruf sağlıyor. Bunu Virtual DOM muhabbetine benzetebiliriz bence. <br/>

### 20-) Exception ve Error nedir? Hangisi, nasıl handle edilebilir? <br/>
Error'lar handle edilemezler. Bunun sebebi OutOfMemory, StackOverFlow gibi donanımsal hatalar alınmasıdır. I/O Errorlar da bu kategoriye girer.<br/>
Fakat Exception sınıfı kesinlikle handle edilebilirler ve doğru bir şekilde kullanılırlarsa uygulamayı yönlendirebilirler.<br/>
Örneğin, NullPointerException için ```Optional``` sınıfı kullanılabilir, veya ```try-catch``` bloğuyla exception yakalanarak ilgili hata hakkında bilgi mesajları verilebilir. <br/>
Exceptionlar unchecked ve checked olmak üzere iki gruba ayrılırlar. Checked exceptionlarda ilgili exception try-catch bloğuyla yakalanıp bilgi verilmelidir. Ancak Unchecked Exceptionlarda böyle bir zorunluluk yoktur compile time da kontrol edilmedikleri için. <br/>
Herkesi mutlu etmek adına, yine de tüm Exceptionların ```try-catch/try-with-resources``` bloklarıyla kontrol altına alınmaları önemlidir. <br/>

### 21-) try-with-resources nedir? try-catch-finally bloğundan farkı nedir? <br/>
Try-catch-finally bloklarını tanıyarak başlayalım.<br/>
Try bloğunda belli başlı bir mantığa göre kodlar işlenir, fırlatılan bir Exception olursa catch bloğunda bu Exception yakalanır ve handle edilir. Ardından finally bloğuyla Exception alınsa da alınmasa da son işlemler gerçekleştirilir ve ```try-catch-finally``` bloğu tamamlanır. <br/>
```try-with-resources``` bloğunda ise şu şekilde bir kod bloğu görmemiz mümkündür. <br/>

```
 try (BufferedReader br = new BufferedReader(new FileReader(path))) {
            br.readLine();
        }
        catch (IOException e) {
            System.out.println("exception occured: "+e);
        }
```
<br/>

Bu kod bloğunda try parantezleri içerisinde tanımlanan BufferedReader classına ait nesne aslında bir  ```AutoClosable```  nesnesidir. JVM AutoClosable nesnelerinin otomatik olarak kapanmalarını sağlar. İsmindeki resources'da buradan gelir. Kapatılması gereken herhangi bir kaynak varsa (database bağlantıları gibi) JVM bunu try-with-resources bloğuyla handle edebilir. <br/>
