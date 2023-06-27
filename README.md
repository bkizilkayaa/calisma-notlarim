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

### 22-) HashMap ile HashTable arasındaki farklar nelerdir? <br/>
HashMap, bir Map implementasyonudur. Key Value çiftinde veri saklar. Burada Key bir Set veri yapısıyken, Value bir List'tir. <br/>
HashTable ise yine bir Map implementasyonudur. Key Value çiftinde veri saklar. <br/>
Farkları ise HashTable'ın synchronized çalışmasıdır. Multithread bir yapı kuracaksak HashTable kullanılması önemlidir. <br/>
Ancak thread-safe çalışmamız gerekmiyorsa HashMap kullanılması Java dokümantasyonunda tavsiye edilir. <br/>

### 23-) Set veri yapısı nedir? <br/>
Set interface'i Collection interface'inden kalıtılmıştır. <br/>
İçerisinde duplicate veri barındırmayan, buna izin vermeyen bir veri yapısıdır. <br/>

### 24-) Spring Data JPA ve Hibernate farkı nedir? <br/>
Spring Data JPA, Hibernate ve Eclipse Link gibi JPA sağlayıcılarını kullanarak repository katmanında CRUD işlemlerinin implementasyonlarını kolaylaştıran bir çerçevedir. <br/>
Hibernate ise JPA implementasyonlarından birisidir, sadece CRUD işlemlerinde gerekli kod kalabalığının önüne geçilmek için Spring Data JPA tarafından üstüne eklemeler yapılarak implementasyonları daha kolay bir hale getirilmiştir. <br/>

### 25-) SOLID prensipleri nelerdir? Örneklendirerek anlatabilir misin? <br/>

Single Responsibility : Her bir servisin, methodun, classın sadece tek bir işten sorumlu olması gerektiğini savunan bir prensiptir. Fazlalıklar ayrıştırılmalıdır. <br/>

Open/Closed Prenciple :  Bu prensip, kodun geliştirmeye açık fakat değişikliklere kapalı olması gerektiğini savunur. Örneğin her bir durum için yeni yeni if/else statement'lar oluşuyorsa, bu kod değişiklik yapılması gereken bir koddur. <br/> 
Bu durumun önüne geçmek için Interface'lerin gücünden faydalanıyoruz. <br/>
Yazdığımız interface her class tarafından gerekli lojiklerle kendi içinde implemente edilerek Genel bir Tip oluşturulabilir.
(Ara katmanda Interface kullanılarak bu prensip uygulamaya koyulabilir.) <br/>

Liskov Substitution : Liskov değişim prensibi. Bu prensip, alt sınıfların her birinin, üst sınıfların yerine kullanılabilir olması gerektiğini savunur. Yani, bir üst sınıfın nesnesi yerine alt sınıfın nesnesi kullanıldığında, programın beklenen şekilde çalışması gerekir. <br/>

Interface Segregation : Interface segregation, interfaceler onları implement eden classları bir fonksiyonu yorumlamalarına zorlamamalıdır. Bir interface içinde çokça method varsa bu interface küçük parçalara bölünmeli ve İsteyen classlara implement edilmelidir. Bu sayede İnterfaceler ayrılığı sağlanır. <br/>

Dependency Inversion : Bağımlılıkların terse çevrilmesi olarak Türkçeleştirilebilir. <br/>
Yüksek seviyeli sınıfların düşük seviyeli sınıfları soyut halleriyle kullanmasıdır. Bu da bağımlılığın düşmesini sağlamaktadır. <br/>
Örneğin Mail Service sınıfının Gmail,Hotmail,Yandex gibi sınıflardan mail atabilir olduğu varsayılsın. Bu servis sadece Gmaile ya da Hotmaile bağımlı olmamalıdır. Veyahut yeni bir Gönderim yöntemi eklendiğinde tekrardan Servis içinde kodların değiştirilmemesi gerekmektedir. O yüzden araya bir Interface atılır. IMailService Interfacei ile tüm gönderim yöntemleri bu interface i implement eder ve Servisimiz artık küçük sınıflarınaa bağımlı olmaz. Soyut halleriyle ilgilenir. <br/>

### 26-) DRY prensibi nedir? <br/>
DRY prensibi, Don't Repeat Yourself'ten gelir. Bu prensibin ihlali olarak, her bir instance için aynı fonksiyonları tekrar tekrar çalıştırmak örnek olarak verilebilir. Bunun yerine kendimizi tekrar etmeyecek şekilde, tek bir fonksiyonda bu işlemler yapılabilir. <br/>
Örneğin bir Interface oluşturarak bu sınıfların o metodu implement etmesi sağlanabilir. Ardından tek bir döngüyle tüm bu classlar gezilip o metotlar ve implementasyonları çağırılabilir. <br/>

### 27-) KISS prensibi nedir? <br/>
Bu prensip "Keep It Simple, Stupid"'den gelmektedir. Bir methoda gereğinden fazla geliştirme yapılmamalıdır. İleride şu da olabilir mi acaba? düşüncesiyle gereksiz kod kalabalığına sebebiyet verilmemelidir. Minimal davranmaktır. <br/>

### 28-) Design Pattern'lar nedir? Birkaç örnek verebilir misin? <br/>
Design Pattern'lar yazılım geliştirme süreçlerinde sıklıkla karşılaşılan problemlere çözüm olarak geliştirilmiş kalıplardır. <br/>
Bu problemler, bir nesne oluşturulurken meydana gelebilirken, bir nesnenin diğer nesneyle olan ilişkisini kontrol etmede de meydana gelebilirler.. <br/>
Örneğin Singleton Pattern, bir Creational Pattern'dır ve uygulamaya bu classın sadece bir instance ı olacağını garanti eder. <br/>
Örneğin Builder Pattern, bir Creational Pattern'dır ve karmaşık field'lara sahip classların instancelarını oluştururken çıkacak karışıklığın önüne geçer. fieldları set ede ede oluşturma yöntemidir. <br/>
Örneğin Factory Pattern, bir Creational Pattern'dır ve alt sınıfların hangi koşullarda oluşturulduğunu client tarafından gizler. Bir FactoryMethod sınıfı yazılır ve o metod içerisindeki parametrelere göre alt sınıf oluşturulup instance'ı dönülür. Bu sayede soyutlama sağlanır. <br/>
Örneğin Adapter Pattern, bir Structural Pattern'dır ve iki class arasındaki uyumsuzlukları kontrol eder. Bir Adapter classı yazılarak, iki class/interface arasındaki uyumsuzlukları yok etmek amaçlanır. <br/>

### 29-) Encapsulation Nedir? <br/>
Kapsülleme, sınıfların propertylerini korumaya almayı amaçlayan OOP'nin 4 prensibinden birisidir. <br/>
Objelerin manipüle edilip değerlerinin kontrolsüz bir şekilde değiştirilmemesini amaçlar. Dışarıya public/private metotlar açılarak set edilecek olan değerin kontrol altına alınıp, belirli koşullar sağlanırsa set edilmesini sağlar. Bu sayede kontrol altına alınır.

### 30-) Encapsulation uygulanırken, setter yazmanın amacı nedir? Zaten datayı manipüle edebiliyorsak neden public setter yazıyoruz? <br/>
Zaten public yazılıyor, fakat burada ana amaç set edilecek olan değerlerin kontrol altına alınmasıdır. <br/>

### 31-) İki sınıfı extends ettiğimizde bir diamond problem söz konusu oluyorken, iki interface'i implement ettiğimizde neden diamond problem söz konusu olmuyor? Yada iki aynı metot imzasından hangisinin çalışacağını nasıl bilebiliyor? <br/>
Bunun sebebi, bir interface'in iki interface'i implement etmesi sonucu ikisine de o metodu implement edeceğini bildirmesinden kaynaklanır. Günün sonunda JVM bir şeye karar vermez ve böylelikle diamond-problem oluşmaz. <br/>
@Override anotasyonu ile başlayan satırda show metodu artık ezilmiştir ve ne iş yapacağı gövdede belirlenebilir. <br/>
Günün sonunda tek bir implementasyon çalışacağı için JVM bize kızmaz.

<br/>

```
public class Inheritence implements C{
    @Override
    public void show() {
        System.out.println("inside show method");
    }
    
    public static void main(String[] args) {
        Inheritence i=new Inheritence();
        i.show();
    }
}

interface A{
    void show();    
}

interface B{
    void show();
}

interface C extends A,B{}
``` 

<br/>

### 32-) İki değişkenin yerini, üçüncü bir değişken kullanmadan değiştirebilir miyiz? <br/>
Aritmetik işlemler kullanılarak yapılabilir <br/> 
Örneğin: 

```
int a=5;
int b=10;
a=a+b; //Bu satırda a=15 olarak atanmıştır
b=a-b; //Bu satırda b=5 olarak atanmış ve değişiklik sağlanmıştır
a=a-b; //Bu satırda son aritmetik işlemle a=10 atanarak değişiklik yapılmıştır.

```

<br/>

### 33-) Veritabanında indexing diye bir şey var. Arkada hangi algoritmayı kullanıyor sence? <br/>
Indexing arkada Tree'ler kullanarak aranan key ile value'ya hızlı bir şekilde ulaşmayı sağlar. <br/>

### 34-) StackOverFlow Error'unu ne koşullarda alırız? Stack neden dolar? <br/>
StackOverFlow Error'u memorynin stack bölgesi dolduğunda alıyoruz. Örneğin, rekürsif bir fonksiyona handle edemeyeceği bir değer, veya sonsuz büyüklükte bir değer göndererek fonksiyon çağrıları yaparak Stack taşmasına sebep verebiliriz. <br/>

### 35-) Error ve exceptions arasındaki farklar nelerdir? <br/>
Error alındığında programın işleyişi durur. Hata verir. <br/>
Ancak Exceptionlar handle edilebilirler. Bu yüzden sağlıklı bir mimaride custom exceptionlar yazılarak bilgiler verilmelidir. <br/>

### 36-) Stack ve Queue arasındaki farklar nelerdir? Stack uygulamamızda ne tarz veriler tutar? <br/>
Stack, LIFO çalışıyor. Yani stack veri yapısına eklenen veri en altta kalacaktır. <br/>
Queue ise FIFO çalışıyor. Kuyruk veri yapısına eklenen veri en önde yer alır ve ilk çıkan olacaktır. <br/>

### 37-) Bu kod bloğu compile olur mu? Olursa ne çıktı verir? <br/>

```

public class Test {
    public void topla(int a, int b) {
        System.out.println(a + b);
    }

    public int topla(int a, int b) {
        int r = a + b;
        return r;
    }

}
    public static void main(String[] args) {
        Test t1 = new Test();
        t1.topla(3, 4); //JVM burada karar veremez. Compile Error
    }
}


``` 

<br/>

Bu kod bloğu compile olmaz, tıpkı diamond problem gibi JVM karar veremez ve compile işlemi gerçekleşmez. Metot imzaları farklı olmalıdır.

<br/>


### 38-) Ogrenci ve Dersler tablosunda veri tutacağız. Nasıl ilişki kurarız? <br/>
Bir öğrencinin birçok derse, Birçok dersin de birçok öğrenciyle ilişkilendirilebileceğini düşünürsek, Many-to-Many ilişki söz konusudur. Bunun için Ogrenciler tablosunda id,name,surname,number gibi propertyler bulunuyorken, Dersler tablosunda id,name gibi propertyler bulunabilir. <br/> 
Bir başka tabloda ise bu iki id değerlerinin birleştiğini ve hangi öğrencinin hangi dersi aldığı bir yapı kurgulayabiliriz.  <br/>

### 39-) Ogrenci obj= new Ogrenci(); satırında neler gerçekleşir? <br/>
Eşitliğin sol tarafında esasen bir işlem gerçekleşmez. Programa, Ogrenci tipinde bir veri tutacağı söylenen bir obj değişkeni tanımlanır. Eşitliğin sağ tarafi ise daha kritiktir. Çünkü Ogrenci nesnesi orada ```new``` keywordü ile oluşturulmaktadır. Referansı ise obj değişkenine atılmaktadır. Artık obj, Ogrenci referansı tutan değişkendir. <br/>

### 40-) Reference Type-Value Type nedir hiç duydun mu? Farkları nelerdir? <br/>
Reference-Type'da referansları gönderilirken, Value-Type'da değerin ta kendisi kopyalanır. Value-Type'da o değer üzerinden yapılan bir değişiklik fonksiyona gönderilen değeri manipüle etmez. Fakat Reference Type değerler, örneğin int[] arrayi, manipüle edilebilirler. 
<br/>

### 41-) Fonksiyon çağrıları nasıl çalışır? <br/>
Fonksiyon çağrıları şu şekilde çalışıyor, Örneğin A metodu B metodunu, B metodu C metodunu, C metodu D metodunu çağırsın. Çağrılar içiçe açılarak ilerler ve D metodunun dönüş değerinden sonra program C metodunun, C metodunun dönüş değerinden sonra ise B metodunun ve en son A metodunun dönüş değerini okuyarak program sonlanır. Çağrılar içiçe geçmiştir. <br/>

### 42-) C++ ile Java arasındaki farklar nelerdir? Java neyi farklı yapar? <br/>
C++ ve Java Object-Oriented dillerdir. C++'ta 84 tane keyword varken Java'da 50 keyword vardır. <br/>
Java, C++'tan farklı olarak, Object referanslarının heap'ten atılması için bir mekanizma geliştirmiştir. Garbage Collector, artık point edilmeyen objeleri heapten temizler. <br/>
Ayrıca Java, compatible'dır. Her çalışma ortamında çalışabilir. Bunun sebebi JVM mimarisidir. <br/>
