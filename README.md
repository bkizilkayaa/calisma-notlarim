# Bu repoda teknik mülakat hazırlığı yapıyorum. Kendimce notlar alıyorum.


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
