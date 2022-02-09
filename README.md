# Hepsiemlak-Java-Spring-Bootcamp-HW2#1


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
