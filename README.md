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
