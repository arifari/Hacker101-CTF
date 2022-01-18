# Hacker101-CTF
## Açıklama
**HackerOne;** işletmeleri, sızma testi uzmanları ve siber güvenlik araştırmacıları ile birleştiren, güvenlik açıklarının yer aldığı bir platformdur. Bu platformda yer alan **Hacker101,** web güvenliği alanı için zafiyetli oluşturulmuş ücretsiz bir sınıftır. Güvenlik açıklarından esinlenen bu sınıf, kullanıcılar için Bayrak Yakalama (CTF) becerilerini pratiğe dökmelerine imkan sağlamaktadır. Keşfedilebilirliği zorluk seviyesine göre değişiklik gösteren güvenlik açıklarını tespit edip  kullanarak bayrak elde etmeye çalışılmaktadır.

## Laboratuvarlar

## A Little Something To Get You Started (Başlangıç)
## Micro-CMS v1 (Flag 0)
## Micro-CMS v1 (Flag 1)

Çalışmada HackerOne CTF'ine dair bazı başlıkların çözümüne değinilmiştir. CTF’in çözümü için öncelikle HackerOne'a kayıt olunması gerekmektedir. Ardından ctf.hacker101.com adresinden CTF çözülebilir.
### A Little Something To Get You Started (Başlangıç)
Hacker101'de ki ilk CTF olan ısındırma amaçlı bu başlangıç bölümü için sayfa görüntülendiğinde karşımıza bu şekilde bir yazı çıkacaktır.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B11.PNG)

Sayfada başka bir şey olmadığı için kaynak kod incelenebilir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B12.PNG)

Sayfanın kaynak kodu incelendiğinde body tagları arasında background.png adlı bir url nin mevcut olduğu görülecektir. 

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B13.PNG)

Sayfa üzerinde background.png adresine gitmek istediğimizde başlangıç flagimizi elde etmiş olacağız.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B14.PNG)

Elde ettiğimiz flagin, Submit a Flag sayfasından kontörü sağlanabilir. Bundan sonrası içinde elde edilen flaglerin kontrolü bu şekilde yapılmaktadır.

### Micro-CMS v1 (Flag 0)
Sayfa üzerinde ki testing ve markdown test adlı dizinler kurcalandığında kayda değer bir şey olmadığı farkedilecektir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B15.PNG)

Sayfa oluşturabileceğimiz bir (Create a new page) alan var. Burada learn adında bir sayfa oluşturduğumuzda adres kısmında page/16 olarak gelmektedir. İlk iki sayfa ise sırasıyla page/1 ve page/2 olarak gelmekte. Peki 3, 4, 5 ………, 13. sayfalar nerede ve bunlarda neler var?

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B16.PNG)

Aradaki sayfa numaralarıyla tek tek adrese gidilebilir. 

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B17.PNG)

Her sayfada ekranda olduğu gibi bir yazı var fakat farklı olarak 5.sayfa da “burada bir sayfanın mevcut olduğu ve sayfaya erişim için yetkimizin olmadığını” bildiren bir yazı görülecektir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B18.PNG)

Sonrası için testing > edit this page diyerek sayfa düzenlemek istiyorum. Burada içeriği değiştirebiliriz yani bize verilen bir yetki söz konusudur. Peki bu yetki 5. Sayfa içinde geçerli mi düşüncesiyle adres üzerinde page/5 olarak denendiğinde flagi elde etmiş olacağız.

### Micro-CMS v1 (Flag 1)
Bu bölümde tek işlem yapabildiğimiz yer Edit page adlı düzenleme sayfasıdır. Fakat burda da bir şey elde etmemiz söz konusu değildir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B19.PNG)

Dolayısıyla ipuçları da incelenerek burada bir SQL injection açığı varmı test edilebilir. Kodda sıkıntı çıkarabilir düşüncesiyle en basitinden form girişine ‘ (kesme işareti) verdiğimizde flag elde edilecektir. 

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B110.PNG)

### Micro-CMS v1 (Flag 2)
Edis this page sayfasında bir save alanı mevcuttu. Burada XSS açığı var mı test edilebilir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B111.PNG)

XSS açığı tespiti için birçok script denenebilir. Basit olarak  <script>alert(23)</script>  olarak test edilidiinde açığın var olduğu görülecek, flag elde edilecektir. Kolaylık sağlaması açısından Github üzerinde birçok XSS scripti vardır. Bu scriptler kullanılabilir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B112.PNG)

### Micro-CMS v1 (Flag 3)
XSS scriptleri bir hayli fazladır ve burada sadece birden fazla XSS açığı olabilir. Bir önce ki walkthrough da XSS scriptini save alanında ki başlık kısmına girmiştik. Şimdi metin kısmı üzerinde test edelim.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B113.PNG)

Birkaç deneme sonucu img formatında ki bir XSS scriptinin sonuç verdiğini görmüş olacağız. Sayfa da görüntülenmeyen bir image dosyası var.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B114.PNG)

Sayfa kodu incelendiğinde bu flagi de bulmuş olacağız.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B115.PNG)

### Micro-CMS v2 (Flag 0)
Sayfa üzerinde bulunan başlıkların kaynak kodu incelendiğinde yada sayfa oluşturabileceğimiz dizine gidildiğinde bir login sayfasının olduğu görülecektir. Basit bir sql injection testi yapalım.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B116.PNG)

Karşımıza gelen bu yazı incelendiğinde SQL injection açığına karşı savunmasız olduğu yani doğru bir format kulanıldığında başarı olunabileceği farkedilecektir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B117.PNG)

Bundan sonrası için bir UNION atağı denenebilir. 'UNION SELECT '123' AS password FROM admins WHERE '1' = '1' sorgusunu denendiğinde login olacağız ve özel bir sayfa oluşacaktır.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B118.PNG)

Sonrası için Private Page adlı sayfa görüntülenirse flag elde edilmiş olacaktır.

### Micro-CMS v2 (Flag 1)
İpuçlarında, farklı isteklerin genellikle farklı yetkilere sahip olduğu ve ayrıca isteğin bir yöntemle başarısız olmasının, farklı bir yöntemle başarısız olacağı anlamına gelmediği belirtilmiştir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B119.PNG)

İpuçları yardımıyla Page Edit sayfasına istek gönderip burpsuite ile incelemeye alalım. Ardından isteği repeater a gönderip send ettiğimizde bir not found hatası alacağız. 

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B120.PNG)

Bu nedenle de, istek başlığındaki oturum çerezini kaldırıp, istek başlığını "POST" olarak sunucuya gönderirsek bu flagi de elde etmiş olacağız.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B121.PNG)

### Micro-CMS v2 (Flag 2)
Oturum açma sayfasında SQL enjeksiyonuna karşı savunmasız olduğundan, bir kullanıcının kimlik bilgilerini almak için veritabanını kullanabiliriz. 

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B122.PNG)

Farklı yöntemlerle yapılabilir. Ben sqlmap aralığıyla gerçekleştirdim.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B123.PNG)

Kullanıcının kimlik bilgilerini veritabanı üzerinden elde ettikten sonra giriş yapabiliriz fakat sonuçta bizi flagi otomatik olarak verdiği için gerek kalmadı.

### Encrypted Pastebin (Flag 0)
Bu bölümde post edebileceğimiz bir alan var ve burada rastgele değerler girilerek post edilebilir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B124.PNG)

Ardından  ipucuna bakıldığında bizden url yi kontrol etmemizi, base64 gibi kodlamaların genellikle URL'ler de değiştirilmesi gerektiğini açıklamaktadır.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B125.PNG)

Url üzerinde birkaç oynama yapmakta fayda var. Farklı değerler girilebilir ya da boş gönderilebilir. Post değeri boş döndürüldüğünde flag elde edilecektir.

### Photo Gallery (Flag 0)
Bu bölümün sayfasında 3 kedi fotoğrafından başka bir şey mevcut değildir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B126.PNG)

Sayfanın kaynak kodu incelendiğinde görüntülerin alınması için fetch yöntemi kullanıldığını ve görüntülerin tanımlanması için id kullanıldığını göreceğiz. fetch?id=1 ile tanımlanan adres görüntülendiğinde aşağıdaki gibi absürt bir ekran karşımıza çıkacaktır.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B127.PNG)

Bu sayfa üzerinde mevcut olan kombinasyonlar neler yada bir sql açığı  var mı diye sqlmap aracıyla bir tarama gerçekleştirebiliriz.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B128.PNG)

Tarama sonucu flagimizi elde etmiş olacağız.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B129.PNG)

### Photo Gallery (Flag 1)
Bir önceki bölümde sqlmap tarama sonucunda flag ile beraber dönen files/adorable.jpg dikkatimi çekmişti. Tarayıcıda union select files/adorable.jpg olarak izlendiğinde bize yine aynı absürt sonucu döndürecektir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B130.PNG)

İpuçlarına başvurulduğunda bize bu uygulamanın uwsgi-nginx-flask-docker görüntüsünde çalıştığı belirtilmiştir. Bu, aradığımız dosyanın uwsgi.ini içinde olduğunu gösterir. 

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B131.PNG)

Bir web sitesinde SQL injection gerçekleştirmeye çalışırken union operotörü sıklıkla kullanılmaktadır. Burada da union denendiğinde ekrana gelen yazıda modül dosyasının main olarak çağrıldığı belirtilmiştir. main ve app olmak üzere 2 dosyanın mevcut olduğunu düşünebiliriz. 

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B132.PNG)

Son olarak sorgu üzerinde uwsgi.ini yerine main.py değerini verdiğimizde main.py adlı bu dosyanın içindeki flag i göreceğiz.

### Cody's First Blog (Flag 0)
Bu bölümde yorum yapmamıza imkan tanıyan bir alan var ve XSS açığı var mı test edilebilir.  Ayrıca verilen bilgiler blogun PHP ile yazıldığını ve PHP include () fonksiyonunu kullanabileceğimizi bildirmektedir. 

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B133.PNG)

Blog PHP ile yazıldığından burada çalışıp bazı PHP etiketleri çalıştırabiliriz. En basitinden <?php phpinfo()?> çalıştırdığımızda başarılı sonuç dönecek flag elde edilecektir.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B134.PNG)

### Cody's First Blog (Flag 1)
Sayfa kaynağına baktığımızda belirtilen satırın yorumlandığını görebiliriz. Bir dizin olabilir ve url'sine erişebiliriz.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B135.PNG)

Önce ?page=admin.auth.inc olarak denendiğinde bir şey bulamayacağız fakat ?page=admin.inc adresine gittiğimizde bu flagide elde etmiş olacağız.

![](https://github.com/arifari/Hacker101-CTF/blob/main/images/Ekran%20Al%C4%B1nt%C4%B1s%C4%B136.PNG)

Bu CTF'in çözümüde bu şekildedir.


