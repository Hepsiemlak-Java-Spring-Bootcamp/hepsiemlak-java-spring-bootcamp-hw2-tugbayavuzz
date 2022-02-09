# Hepsiemlak-Java-Spring-Bootcamp-HW2


Java dünyasındaki framework’ler ve çözdükleri problemler nedir? Kod Örneklendirini de 
içermelidir. 

Java framework, uygulama geliştirme için Java programlama dilini uyarlamak ve desteklemek üzere tasarlanmış ve geliştirilmiş önceden tanımlanmış kod parçaları veya yazılım geliştirme platformudur. 
Peki neden framwork’lere ihtiyaç duyarız?
Framework’ler, uygulamalarımıza bir yapı kazandırır. Örneğin, test için uygun bir framework varsa, birçok şeyi otomatikleştirebilir, doğru ve tutarlı sonuçlar elde edebiliriz. Aynı şekilde, ORM, web uygulamaları, veri yönetimi vb. için frameworkler varsa, bu bir geliştiricinin hayatını basitleştirecek ve bir etki alanı veya uygulamada kullanılan ortak kod parçaları hakkında ve işin mantığına daha fazla konsantre olmalarına yardımcı olacaktır.

Bu yazımda çok birkaç framework’ten bahsedeceğim.
- Spring
- Hibernate
- JavaServer Faces [JSF]

## Spring
Java uygulamalarını gelişirmeyi kolaylaştıran, hızlandıran Core Container AOP,DAO gibi modellerden oluşan bir frameworktür.Spring birçok problem alanına çözüm bulmaktadır.
Spring Framework, Java'da yazılım tasarımı, geliştirme ve deploy etmek için oluşturulmuş en yaygın kullanılan, lightweight(hafif) yazılım uygulama frameworklerinden biridir.
Bu Java framework’ü, Java için yazılım uygulaması geliştirme uzantıları içerir. Spring, büyük ölçüde Web Uygulamaları geliştirmede kullanılır.
Spring in nelere çözüm bulduğundan çok hangi avantajları sağladığını açıklamak istiyorum.
-	Gerçek bir Web Sunucusuna ihtiyaç duymadan Web Uygulamalarını çalıştırabiliriz.
-	Spring, XML yapılandırmalarıyla uyumludur.
-	Spring ile kolay bir şekilde JDBC bağlantılarını kurabiliriz
-	Spring, uygulamaları daha az sayıda hataya açık hale getirir ve böylece güvenilirliği artırır.

## Hibernate
Hibernate, Java'nın Persistence API desteğini genişletebilen en iyi frameworklerinden biridir.Hibernate, açık kaynaklı, performans odaklı ve ORM aracıdır.
Hibernate, veritabanı etkileşimi ve çok daha fazlası gibi özellikleri aracılığıyla uygulamaların geliştirilmesini basitleştiren, amaca yönelik olarak oluşturulmuş bir Java frameworkudur. 
-	Hibernate, JDBC API aracılığıyla fazlalığı azaltır.
-	Hibernate, üretkenliği ve sürdürülebilirliği artırır.
-	Hibernate, Persistence API'lerini destekler.
-	Hibernate  ORM uygulama ile herhangi bir veritabanı arasında iletişime izin verir.

Peki Hibernate nasıl kullanacağız?
Öncelikle projemize Hibernate’i maven kullanarak pom.xml dosyasına dependency ekleyelim


```
<dependency>
   <groupId>org.hibernate</groupId>
   <artifactId>hibernate-core</artifactId>
   <version>5.6.5.Final</version>
</dependency>

```
Kullanılacak veritabanı için JDBC driver'ını kurmamız gerekmektedir.JDBC şart değil ancak Hibernate arka planda JDBC kullanmaktadır.Ben PostgreSQL için dependency ekleyeceğim. Siz İstedğiniz veritabanının dependency ekleyebilirsiniz.

```
<dependency>
   <groupId>org.postgresql</groupId>
   <artifactId>postgresql</artifactId>
   <scope>runtime</scope>
</dependency>
```
Daha sonra ise veritabanı bağlantısı için veritabanı bilgilerini application.properties dosyasına yazmamız gerekiyor.
```
spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.hibernate.show-sql=true
spring.datasource.url=jdbc:postgresql://localhost:5432/database adı
spring.datasource.username=postgres
spring.datasource.password=database sifresi
```
<br>
Bir proje oluşturduktan sonra ”src” dosyasının altında application.properties dosyasına bu bilgileri yazdığımızda veritabanı bağlantısını yapmış oluyoruz.
<img src="https://github.com/Hepsiemlak-Java-Spring-Bootcamp/hepsiemlak-java-spring-bootcamp-hw2-tugbayavuzz/blob/main/hibernate1.png" align=center>
<br>

Buradaki örnek kodda Tablo ismimi (job_titles) ı tanımlayarak tabloya ve sütunlarına erişim sağlıyoruz. CRUD işlemlerini veritabanında kolaylıkla yapabiliriz. Hibernate bu kolaylığı bize sağlamaktadır.

```
@Entity
@Table(name = "job_titles")
public class JobTitle {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "title")
    private String positionName;
    
}
```

## JavaServer Faces [JSF]
JavaServer Faces java dilinin web frameworklerinden bir tanesidir.JSP’den daha gelişmiş bir frameworktur.Kullanıcı arayüzünü destekler. MVC yapısına uygundur. Api ve tagları içerir. 
Herhangi bir web sayfası nasıl olursa olsun bir JSF sayfası 6 işlemden geçmektedir.

JSF Yaşam Döngüsü

<img src="https://github.com/Hepsiemlak-Java-Spring-Bootcamp/hepsiemlak-java-spring-bootcamp-hw2-tugbayavuzz/blob/main/jsflifecycle.png" align=center>
<br>

Aşağıda gösterilen adımlar ile bir jsf projesi oluşturalım.
<img src="https://github.com/Hepsiemlak-Java-Spring-Bootcamp/hepsiemlak-java-spring-bootcamp-hw2-tugbayavuzz/blob/main/jsfcreateproject1.png" align=center>
<br>

<img src="https://github.com/Hepsiemlak-Java-Spring-Bootcamp/hepsiemlak-java-spring-bootcamp-hw2-tugbayavuzz/blob/main/jsfcreateproject2.png" align=center>
<br>

<img src="https://github.com/Hepsiemlak-Java-Spring-Bootcamp/hepsiemlak-java-spring-bootcamp-hw2-tugbayavuzz/blob/main/jsfcreateproject3.png" align=center>
<br>

<img src="https://github.com/Hepsiemlak-Java-Spring-Bootcamp/hepsiemlak-java-spring-bootcamp-hw2-tugbayavuzz/blob/main/jsfcreateproject4.png" align=center>
<br>

Projemizi IntellijIdea’da bu şekilde oluşturup geliştirebiliriz.

## Spring frameworkünün kullandığı design patternlar neler?
Spring frameworkunda birçok Design patternlar kullanılmaktadır.  
-	MVC Pattern
-	Proxy Pattern 
-	Factory Pattern
-	Singleton Pattern
-	Template method Pattern
-	Prototype Pattern

## MVC Pattern
Bir sistem veya alt sistemin(Model, View,Controller) bileşenlerini ayıran yazılım tasarımıdır.MVC aslında arayüz ve mantık kısmını birbirinden ayırır.
- Model;uygulamanın veya componentlerin durumuyla ilgili veriler içerir.Verilerin işlendiği katman olarak söylebiliriz.
- View; html sayfalarının görünüm  kısmını burda gerçekleştiriyoruz.
- Controller; mantık kısmını bu katmanda gerçekleştiriyoruz.

<img src="https://www.mshowto.org/images/articles/2020/05/mvcnedir.jpg" align=center>
<br>

## Proxy Pattern 
Var olan bir nesneye ulaşılmak istendiğinde Proxy Pattern oluşturulur. Nesneyle istemci arasına yeni bir katman koyarak nesnenin kontrollü bir şekilde paylaşılması sağlanır. Böylece istemci, işlem yapan sınıfla doğrudan temasa geçmemiş olur. Bu durum sayesinde işlemin yapılma performansında bir düşüklük olmaması sağlanır. Bu yüzden Proxy Pattern fazla yük getiren işlemlerde kullanılır.

<b>Image.java</b>
```
public interface Image {
    void display();
}
```


<b>RealImage.java</b>
```
public class RealImage implements Image {

    private String fileName;

    public RealImage(String fileName){
        this.fileName = fileName;
        loadFromDisk(fileName);
    }

    @Override
    public void display() {
        System.out.println("Displaying " + fileName);
    }

    private void loadFromDisk(String fileName){
        System.out.println("Loading " + fileName);
    }
}
```
ProxyImage.java
```
public class ProxyImage implements Image{

    private RealImage realImage;
    private String fileName;

    public ProxyImage(String fileName){
        this.fileName = fileName;
    }

    @Override
    public void display() {
        if(realImage == null){
            realImage = new RealImage(fileName);
        }
        realImage.display();
    }
}
```

ProxyPatternDemo.java
```
public class ProxyPatternDemo {

    public static void main(String[] args) {
        Image image = new ProxyImage("test_10mb.jpg");

        //image will be loaded from disk
        image.display();
        System.out.println("");

        //image will not be loaded from disk
        image.display();
    }
}
```
```
Output :
Loading test_10mb.jpg
Displaying test_10mb.jpg

Displaying test_10mb.jpg
```

The source code : https://www.tutorialspoint.com/design_pattern/proxy_pattern.htm

### Factory Pattern
Factory kelimesinden yola çıkarak bu patterni açıklayalım. Factory kelime anlamı fabrika olarak kullanılmaktadır.Peki arasındaki bağ nedir de Factory demişler bir bakalım. Fabrika denilince üretim aklımıza gelmektedir. Peki ne üretecek? Programlamada nesne üretecektir. Nesneyi oluşturma görevini müşteriden fabrikaya bırakmak için bu tasarımı kullanırız. Çok basit örnekle kullandığımız eşya, giysi vb. ürünleri fabrikalar üretir ve biz bunları satılan yerlerden (bayi, mağaza vb.) alırız. Bizde nesneyi üretme işlemini bayi veya mağazalardan değil fabrikalara vereceğiz.
Teknik olarak açıklamak gerekirse Factory Method tasarım; aynı interface'i veya abstract sınıfı implement etmiş etmiş factory nesnelerinin üretiminden sorumlu tasarımdır.

### Singleton Pattern
Singleton tasarımının amacı bir sınıftan sadece bir nesne oluşturmak için kurulmuş bir mimaridir. Her yerde bu nesneyi üretemeyeceğiz. Ben nerde istersem orda üretebileceğim. Singleton Pattern, bir nesnenin tek olmasını garanti eder. Nerden ulaşmak istersem ulaşayım aynı nesneye ulaşacağımı garanti eder. Bu nesneye de Getter ve Setter ile ulaşabileceğiz. Peki ya nesne oluşturmadıysak?Kontrole ihtiyacımız var. Eğer biz daha önce nesneyi oluşturmadıysak
```
if(instance == null){
     instance = new Singleton();
   }
```
ile bir kontrolünü sağlayarak nesneyi oluşturabiliriz.	

### Template Method Pattern
Bir algoritmanın adımlarını tanımlamayı sağlar ve alt sınıfların bir veya daha fazla adımların implementasyonunu yapmasını olanak tanır. Örneğin bir çay demleme algoritmasını ele alalım.Önce suyu emliğe koyup kaynamasını bekleyip sonra cay demleme işlemi yapılıp en sonunda afiyetle içeriz. Hepsini sırayla gerçekleştirip ortaya bir ürün çıkarttık.Bu pattern amacı ise benzer adımlara sahip sınıfları tasarlarken aynı kodları tekrar tekrar kullanmayı engellemek için tasarlanmıştır. Kod tekrarından kurtarır. Final keyword sayesinde standart bir tasarım sağlar.Bu tasarımı kullanmak için gerekli bazı kurallar mevcuttur. 
- Türü abstract olan, template metodu içeren süper sınıf
- En az iki tane somut Template sınıfı
- Client sınıfı
 
Game Sınfı(Game.java)
```
public abstract class Game {

     abstract void initialize();
     abstract void start();
     abstract void end();

     public final void play(){

          //initialize the game
          initialize();

          //start game
          start();

          //end game
          end();
     }
}
```
Chess sınıfı Game sınıfını extend etsin
```
public class Chess extends Game {
     @Override
     void initialize() {
          System.out.println("Chess Game Initialized! Start playing.");
     }
     @Override
     void start() {
          System.out.println("Game Started. Welcome to in the chess game!");
     }
     @Override
     void end() {
          System.out.println("Game Finished!");
     }
}
```
Soccer Sınıfı da Game sınıfını extend etsin
```
public class Soccer extends Game {

     @Override
     void initialize() {
          System.out.println("Soccer Game Initialized! Start playing.");
     }

     @Override
     void start() {
          System.out.println("Game Started. Welcome to in the Soccer game!");
     }

     @Override
     void end() {
          System.out.println("Game Finished!");
     }
}
```
Template sınıfımız TemplatePatternDemo(Client sınıfımız)
```
public class TemplatePatternDemo {

     public static void main(String[] args) throws InstantiationException, IllegalAccessException, ClassNotFoundException {

          Class c=Class.forName(args[0]);
          Game game=(Game) c.newInstance();
          game.play();
     }
}
```


### Prototype Pattern
Prototype Pattern kullanılmasının amacı üretilen nesnenin çok kaynak tüketmesi durumunun engellenmesini sağlamaktır. Yeni bir nesne yaratmanın maliyeti pahalı ve kaynak yoğun ise bu model izlenmelidir. Alt sınıflama ihtiyacını azaltır. Nesne oluşturmanın karmaşıklığını gizler.

#Creational Patterns neler? 
Yazılım nesnelerinin nasıl yaratılacağı hakkında genel olarak öneriler sunarak kullandığı esnek yapı sayesinde daha önceden belirlenen durumlara bağlı olarak gerekli nesneleri yaratır.
-	Singleton Pattern
-	Factory Pattern
-	Abstract Factory Pattern
-	Builder Pattern
-	Prototype Pattern


YARARLANILAN KAYNAKLAR<br>
https://www.javainuse.com/spring/spring-design-patterns<br>
http://cemkefeli.com/post/2016/05/17/Java-Server-Faces-(JSF)-nedir.aspx<br>
https://kurukod.wordpress.com/2015/07/06/spring-nedir-neden-kullanilir/<br>
https://aksoytolga.com/2020/07/04/spring-framework-nedir/<br>
https://mvnrepository.com/artifact/org.hibernate/hibernate-core/5.6.5.Final<br>
https://medium.com/an-idea/design-patten-in-spring-framework-24bfd07a449b<br>
https://www.yusufsezer.com.tr/spring-web-mvc/<br>
https://blog.burakkutbay.com/design-pattern-factory-pattern-nedir.html/<br>
https://bidb.itu.edu.tr/seyir-defteri/blog/2013/09/08/vekil-kal%C4%B1p-(proxy-pattern)<br>
https://www.javatpoint.com/template-pattern<br>





