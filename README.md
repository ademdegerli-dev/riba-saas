# BEP Yerel Web Uygulaması

## v26 yenilikleri

- Bireysel izleme çizelgesindeki aylık değerlendirme başlıkları Excel'deki “Metni Yukarı Döndür” görünümüne dönüştürüldü.
- Toplantı Ajandasına `0000` şifreli “Tüm toplantı randevu tarihlerini sil” işlemi eklendi; tarih ve saatler temizlendikten sonra yeniden planlama bildirimi gösterilir.
- Uygulama açılırken bugüne ait toplantılar varsa öğrenci, sınıf, saat ve yer bilgileriyle hatırlatma gösterilir.
- Sınıf, engel türü, grup, destek eğitim, toplantı ve RAM kademe uyarısı dağılımlarını gösteren İstatistikler sayfası eklendi.
- E-Okuldan indirilen `IOG02009_99.XLS` biçimi desteklenir. Aynı okul numarasının tekrar eden satırları tek öğrenciye dönüştürülür ve engel türleri birleştirilir; dosyanın sonundaki indirme tarih/saat satırı yok sayılır.
- Tüm ekranların altında geliştirici adı ve iletişim adresi gösterilir.

## v25 yenilikleri

- Sınıf veya tüm öğrenciler için toplu PDF kaydında RAM/E-Okul sınıf kademesi uyumsuzluğu bulunan öğrenciler otomatik olarak dışarıda bırakılır; bu kayıtlar açık öğrenci üzerinden bireysel indirilebilir.
- Öğrenci veritabanına sınıf öğretmeni ve engel türü sütunları ile engel türü filtresi eklendi. Eğitim yılı listede yalnızca yıl aralığı olarak gösterilir.
- “Yıllık BEP verilerini temizle” düğmesi, `0000` şifresi ve ikinci onay sonrasında yıllık plan/toplantı/karar verilerini temizler; kimlik, aile özlük bilgileri, sağlık/geçmiş/düzenlemeler ve eğitsel performansı korur.

Sol menüdeki BEP iş akışı sayfalarının tamamı doğrudan bağlantıdır. Kullanıcı **Önceki** ve **Devam** düğmelerini kullanmak zorunda değildir. Ayrı PDF sayfaları, sol menüyü kalabalıklaştırmadan **Çıktılar** ekranından açılır.

## Excel'den toplu öğrenci aktarımı

Öğrenci Veritabanı sayfasındaki **E-Okul’dan öğrenci yükle** bölümü, E-Okuldan alınan listeyi doğrudan okur. Bölümde “E-Okuldan indirilen özel eğitim gereksinimli öğrenci listesini Excel verisi olarak buraya yükleyiniz.” açıklaması gösterilir. Okul No, sınıf/şube, ad-soyad, cinsiyet, engel durumu ve önerilen hizmet bilgileri aktarılır. Aynı okul numarasına ait tekrar satırlar tek öğrenciye dönüştürülür ve bütün engel durumları birleştirilir. Okul bilgilerinde bulunmayan sınıflar otomatik oluşturulur. Sadeleştirilmiş öğrenci listesine ihtiyaç yoktur.

Normal sınıf adları aktarım sırasında kısa biçime dönüştürülür: `1. Sınıf / A Şubesi` değeri `1-A`, `2. Sınıf / B Şubesi` değeri `2-B` olur. Adında Zihinsel, Otizm veya Otistik bulunan özel eğitim sınıflarının özgün sınıf adı korunur.

## Toplantı katılımı ve imzalar

Aile bilgileri bölümünde anne, baba ve varsa vasi için 1., 2. ve 3. toplantıya katılım işaretlenebilir. İşaretlenen kişiler yakınlıkları ve adlarıyla BEP geliştirme birimi üyeleri sayfasına aktarılır. PDF sayfa 2 ve 3'te dört kişilik, sayfa 4'te beş kişilik imza bölümü bulunur; kayıtlı yönetici, öğretmen, rehber öğretmen ve veli adları otomatik kullanılır.

## Değerlendirme çizelgesi ve güncel PDF düzeni

Çıktılar ekranındaki **Değerlendirme** seçeneği, BEP planı hazırlanan her ders için Eylül-Haziran sütunlarını içeren ayrı bir bireysel izleme çizelgesi üretir. Eğitim yılı okul ayarlarından, ders öğretmeni ilgili dersin BEP planından ve tarih güncel tarihten alınır. Birinci sayfada veli beyanı, anne-baba-vasi imzaları ve açıklama notları; üçüncü sayfada öğrencinin gelişim öyküsü bulunur. Kapak logosu isteğe bağlıdır ve yüklendiğinde kapağın ortasında gösterilir.

Sınıf bilgi girişi, sınıf adının solda sabit kaldığı ve öğretmen, sınıf düzeyi ile eğitim saati bilgilerinin sağa doğru genişleyen tek bir satırda görüntülendiği çalışma çizelgesi düzenindedir.

Bu klasördeki index.html dosyasına çift tıklayın. Uygulama internet veya kurulum gerektirmeden güncel bir masaüstü tarayıcısında çalışır.

## Kullanım

1. Veri Girişi sayfasında okul, öğrenci, aile, performans, hizmet, karar, kurul ve bireyselleştirilmiş eğitim planı alanlarını doldurun.
2. Sol menüden 1–6 veya Kpk sayfasını açarak çıktıyı inceleyin.
3. PDF / Yazdır düğmesine basın. Yazdırma penceresinde hedef olarak “PDF olarak kaydet” seçin.

Öğrenciler ve her eğitim yılına ait BEP planları tarayıcının yerel IndexedDB veritabanına kaydedilir. Öğrenci Veritabanı sayfasındaki Aç düğmesi planı geri çağırır. Sınıf atlat düğmesi öğrenci ve aile bilgilerini yeni eğitim yılına kopyalar, sınıfı bir kademe yükseltir ve yeni bir BEP kaydı hazırlar.

Okul Bilgileri sayfasındaki kurum, okul ve eğitim yılı değerleri tüm öğrencilere ortak uygulanır. Yeni öğrencinin sıra numarası program tarafından ardışık olarak verilir. BEP başlangıcı yeni kayıtta bugündür; bitiş tarihi ileri Haziran ayının ikinci haftasındaki cuma günü olarak gelir ve değiştirilebilir.

Okul Bilgileri sayfasında sınıf/şubeler sınıf öğretmeniyle birlikte istenen sayıda eklenebilir, güncellenebilir veya çıkarılabilir. Ayrıca dört rehber öğretmen, dört müdür yardımcısı, okul müdürü ve okul logosu tanımlanabilir. Öğrenci sınıfı bu listeden seçilince sınıf öğretmeni otomatik gelir.

Öğrenci Veritabanı ekranındaki arama kutusu ad, T.C. kimlik numarası, okul numarası, sınıf, grup ve eğitim yılı içinde arama yapar. Aç / Güncelle düğmesi eski BEP’i bütün alanlarıyla geri çağırır.

Çıktılar ekranında tek bir sayfa ayrı açılabilir veya istenen sayfalar işaretlenerek tek işlemle toplu PDF/yazdırma görünümü hazırlanabilir. Kapakta okul logosu gösterilir. Kapak dışındaki çıktılarda öğrenci adı ve sayfa numarası bulunur.

Kpk kapak sayfası ve 1. sayfa dikey; diğer çıktı sayfaları yatay yazdırılır. Toplu çıktı görünümü her sayfanın kendi yönünü korur.

Ana Sayfa’ya sol menüden veya sol üstteki BEP simgesinden dönülebilir. Destek Eğitim Listesi, destek/kaynaştırma hizmeti bulunan öğrencileri topluca gösterir; öğrenci adı ve sınıfa göre filtrelenebilir.

Düzenlenebilir seçenek listelerinin her biri ekran yüksekliğinin en az yarısını kullanır ve başlangıçta açık gelir. Sınıf kayıtları Excel benzeri tabloda sınıf/şube, sınıf öğretmeni, sınıf düzeyi ve Sabah/Öğlen/Tam Gün bilgileriyle tutulur.

Eğitsel Performans sayfasında seçilen her ders için ayrı BEP planı oluşturulur. BEP Planı sayfasındaki ders düğmeleriyle dersler arasında geçilir. Her ders ilk olarak bir uzun dönemli amaçla açılır; yeni uzun dönemli amaç veya aynı amaca bağlı ek kısa dönemli amaç eklenebilir. Başlangıç ayı güncel ay, bitiş ayı Haziran’dır.

BEP birimi ekranında katılan kişinin önce yakınlık düzeyi, ardından adı soyadı girilir. Çıktıda aynı sıra korunur. Bütün çıktı sayfalarının üst bilgisinde öğrenci adı ve sınıfı birlikte bulunur.

Okul logosu isteğe bağlıdır; yüklendiğinde kapak sayfasının ortasında gösterilir.

## Dersler ve BEP planı

İlkokul dersleri.pdf içindeki ders adları taranmış sayfa görsellerinden çıkarılmış, tekilleştirilmiş ve Türkçe alfabetik sıraya konmuştur. Ders/gelişim alanı kutularına yazıldıkça liste filtrelenir; listede olmayan bir ad yazıldığında yeni seçenek olarak saklanır.

Bir uzun dönemli amaç için “Kısa dönemli amaç” düğmesiyle birden fazla alt amaç oluşturulabilir. Ölçüt; Bağımsız veya belirtilen yüzde seçeneklerinden seçilir. Başlama ve bitiş ayları Eylül-Haziran akademik sırasındadır. Yöntem ve teknikler ile hizmet türleri çoklu seçilebilir.

Engel durumları, dersler, yöntem/teknikler ve aile eğitimi yolları Okul Bilgileri sayfasındaki Düzenlenebilir Seçenek Listeleri bölümünden eklenebilir, değiştirilebilir veya silinebilir. Engel durumu ayrıca doğrudan öğrenci ekranından düzenlenebilir.

Veli/vasi alanları yalnız “anne veya babadan başka biri” seçildiğinde gösterilir. Toplantı tarihi yeni kayıtta bugünün tarihidir. Komisyon başkanı varsayılan olarak ilk müdür yardımcısıdır; diğer müdür yardımcıları veya okul müdürü seçilebilir.

JSON yedekle bütün veritabanını indirir; JSON geri yükle daha önce indirilen yedeği açar.

## Son arayüz ve toplu işlem geliştirmeleri

- RAM sınıf kademesi uyarı kartı kırmızı zemin/beyaz yazıyla gösterilir; karta tıklanınca yalnız bu durumdaki öğrenciler listelenir.
- Öğrenci veritabanı sınıf sırasındadır ve sütun düzeni Sıra, Sınıf, No, Öğrenci Adı Soyadı şeklinde başlar. Tüm öğrencileri bir üst eğitim-öğretim yılına topluca aktarma düğmesi bulunur.
- Sınıflar, sınıf düzeyine göre topluca Sabah, Öğlen veya Tam Gün yapılabilir. “Özel Eğitim Okul Öncesi” sınıf düzeyi desteklenir.
- Kimlik, tarih ve aile alanları daha kompakt ve simetrik düzenlenmiştir; veri giriş kutuları arka plan alanlarından belirgin renkle ayrılır.
- Açık öğrenci şeridinde öğrencinin adı, sınıfı, sınıf öğretmeni ve grup bilgisi gösterilir.
- Anne ve baba için çalışma durumu girilebilir; “Çalışıyor” seçildiğinde iş telefonu ve iş adresi alanları açılır.
- T.C. Kimlik Numarası yalnızca rakam kabul eder; kayıt sırasında 11 hane ve çift rakamla bitme koşulu denetlenir.
- Anne ve baba bilgi kartları masaüstünde aynı satırda ekranı eşit paylaşır. Veli/vasi kartı da aynı genişlikte, geniş adres alanlarıyla gösterilir.
- Cinsiyet alanı yalnız Erkek veya Kız seçimine izin verir.
- Eğitsel performans başlangıçta tek ders satırıyla açılır; dersler gerektikçe eklenip kaldırılabilir. Toplantı kararlarındaki hizmet satırları seçilen ders sayısına göre otomatik oluşur.
- Aile eğitimi “Evet/Hayır” seçimine bağlıdır; eğitim yolu yalnız Evet seçildiğinde gösterilir. Diğer karar alanları da birer birer eklenir.
- Bir sonraki toplantı tarih alanıdır ve varsayılan olarak Şubat ayının ikinci pazartesi gününü kullanır. Toplantı yeri listeden seçilir, veli katılımı aile bilgilerindeki toplantı işaretlerinden otomatik hesaplanır.
- PDF 1. sayfadaki ayrı imza bloğu kaldırılmıştır; veli beyanı alanı imza için kullanılır. BEP planı çıktısında her ders ayrı bir PDF sayfasına yerleştirilir.
- Eğitsel performans ve toplantı kararlarındaki iç satırların sayfada dar görünmesine neden olan sütun yerleşimi düzeltilmiştir. Ders ve performans alanları eşit yarım genişliktedir; ders ekleme düğmesi ilk ders satırının hemen altında bulunur.
- Kademeye göre toplu eğitim saati bölümü, sınıf tablosunun üzerinde tam genişlikte ve taşma olmadan gösterilir.
- Öğrenci kimlik alanları yeniden dengelenmiş; otomatik sıra ve okul numarası kutuları küçültülürken uzun bilgiler için daha geniş alan ayrılmıştır.
- Referans görsele göre öğrenci bilgileri üç simetrik satıra ayrılmıştır: temel kimlik ve sınıf bilgileri; cinsiyet, doğum, grup ve eğitim yılı; BEP başlangıç/bitiş tarihleri.
- Önceki/Devam çubuğunun uzun formlardaki veri giriş alanlarını örtmemesi için çubuk normal sayfa akışına alınmıştır.
- Otomatik sıra ve okul numarası alanları yaklaşık yüzde 40 küçültülmüş, kazanılan alan öğretmen kutusuna aktarılmıştır. Grup alanı genişletilmiş; eğitim ve öğretim yılı BEP tarihleriyle aynı alt satıra taşınmıştır.
- Eğitsel performanstaki ders ekleme düğmesi son ders satırının altında, daha büyük ve belirgin biçimde gösterilir.
- BEP Planı sayfasındaki Devam düğmesi önce sıradaki dersin planına geçer; bütün dersler tamamlandığında Toplantı Kararları sayfasını açar.
- Eğitsel performans PDF’indeki imzalar kaldırılmış ve açıklama notları eklenmiştir. BEP planı ve karar çıktılarında okul müdürü imzası bağımsız sağ-alt alandadır.
- Destek Eğitim Listesi yazdırılırken “BEP’i aç” işlem sütunu gizlenir.

## Toplantı ajandası, randevu mesajları ve son PDF düzeni

- Toplantı Ajandası aylık takvim görünümündedir. Her öğrenci için tarih, saat ve toplantı yeri girilebilir; kayıtlı randevular ilgili günün içinde öğrenci adıyla gösterilir.
- “RAM Rapor sınıf kademesi ile E-Okul sınıf kademesi farklıdır. RAM ' a başvurunuz” durumundaki öğrenciler ajandada kırmızı uyarıyla kilitlenir ve bu öğrenciler için randevu oluşturulamaz.
- Randevu Mesajları sayfası ajandadaki randevudan öğretmene ve veliye yönelik ayrı bilgilendirme metinleri hazırlar. Metinler düzenlenebilir ve tek düğmeyle panoya kopyalanabilir.
- BEP Geliştirme Birimi Üyeleri çıktısında okul müdürü tablo dışında, sayfanın sağ alt köşesinde tarih, ad-soyad, unvan ve imza alanıyla yer alır.
- Bireysel İzleme Çizelgesi'nde ay sütunları daraltılmış, Amaçlar sütunu genişletilmiş ve yıl sütununda yalnız sayısal eğitim yılı gösterilmiştir.
- Kapak daima dikeydir. Üstte ortalanmış T. C., il ve okul bilgileri; ortada varsa okul logosu; altta öğrenci bilgileri bulunur.

## Ajanda planlama ve veli katılım takibi

- Öğrenci toplantı planları öğrenci adına göre değil, sınıf/şube adına göre sıralanır; aynı sınıftaki öğrenciler kayıt sırasını korur.
- Toplantı yeri yeni randevularda varsayılan olarak PDR Servisi gelir ve listeden değiştirilebilir.
- Takvimde bir güne tıklanınca o güne öğrenci, saat ve toplantı yeri seçilerek doğrudan randevu eklenebilir. Randevu aynı zamanda sınıf sıralı alt listeden de düzenlenebilir.
- “Sıralı listeyi yazdır” düğmesi randevuları tarih ve saate göre sıralayan, A4 yatay ve renkli katılım durumlu bir çıktı hazırlar.
- Toplantı zamanı geçmiş ve aile katılım işareti bulunmayan kayıtlar sarı “Veli Katılmadı”; katılım işaretli kayıtlar yeşil “Veli Katıldı” olarak gösterilir. İleri tarihli toplantılar “Bekleniyor” durumundadır.
- Öğretmen ve veli mesajlarında toplantı tarihi, haftanın günü, saat ve yer açıkça yazılır. Öğretmen mesajı ayrıca BEP hazırlanacak derslere ilişkin eğitsel performans ile uzun ve kısa dönemli amaçların hazır getirilmesini hatırlatır.

## PDF tablo yazıları ve amaç yerleşimi

- Bireyselleştirilmiş Eğitim Planı çıktısındaki imza bölümüne rehber öğretmen ve okul bilgilerinde kayıtlı adı eklenmiştir.
- Bireyselleştirilmiş Eğitim Planı, Eğitsel Performans ve Ders Bazlı BEP Bireysel İzleme Çizelgesi tablolarının iç yazıları 11 punto olarak düzenlenmiştir.
- Aynı uzun dönemli amaca bağlı kısa dönemli amaçlar tek hücre içinde tutulur; her kısa dönemli amaç ayrı bir alt satırda gösterilir. Ölçüt, yöntem, materyal, tarih ve değerlendirme bilgileri de ilgili kısa amaçla aynı satır düzenini korur.
- İzleme çizelgesi 11 puntoyla tek A4 yatay sayfaya sığacak şekilde sekiz amaç satırıyla hazırlanır; daha fazla gerçek amaç varsa ek satırlar korunur.

## PDF dosyalarını doğrudan kaydetme ve toplantı katılımı

- Çıktılar sayfasındaki “PDF dosyalarını bilgisayara kaydet” bölümünde varsayılan kapsam açık öğrencidir. İstenirse bir sınıftaki bütün BEP kayıtları veya veritabanındaki tüm öğrenci/BEP kayıtları tek PDF dosyasına kaydedilebilir.
- PDF'e yalnız Çıktılar bölümünde işaretli sayfalar eklenir. Kapak ve 1. sayfa dikey, diğer sayfalar yatay kalır. PDF oluşturma bileşenleri uygulama klasöründedir; internet bağlantısı gerekmez.
- Veli katılım durumu, aile bilgilerindeki üç toplantı işaretine göre “1. Toplantıya Katıldı”, “1. ve 2. Toplantılara Katıldı”, “1. ve 3. Toplantılara Katıldı”, “2. ve 3. Toplantılara Katıldı” veya “Tümüne Katıldı” biçiminde otomatik yazılır.
- Her dersin Sorumlu kişi(ler) alanı toplantıya katılımı işaretlenen anne/baba/vasi adı, sınıf öğretmeni ve ilgili dersin öğretmeninden otomatik oluşturulur. Bulunmayan isimler eklenmez.
- Hizmet türlerine Sağlık Kuruluşuna Yönlendirme, Veli Eğitimi ve Yeniden RAM İncelemesi seçenekleri eklenmiştir.

## Önemli notlar

- BEP_VeriGir bir veri giriş ekranıdır ve PDF çıktısı yoktur.
- PDF düğmesi tarayıcının yerleşik yazdırma/PDF özelliğini kullanır. Yazdırma penceresinde yön “Yatay”, kenar boşluğu “Dar” ve ölçek “Sayfaya sığdır” olarak görünmüyorsa bunları seçin.
- 6. sayfa, Excel örneğindeki “Yıl sonunda değerlendirme yapılacak.” metnini korur.
- Alanların Excel kaynağı ve bağımlılıkları EXCEL-ALAN-ESLEME-RAPORU.md dosyasında belgelenmiştir.

## E-Okul liste karşılaştırması ve BEP planı seçimleri

- E-Okuldan alınan `IOG02009_99.XLS` biçimindeki yeni öğrenci listesi doğrudan içe aktarılmadan önce mevcut eğitim yılıyla karşılaştırılır. Yeni öğrenciler, yeni dosyada bulunmayan eski öğrenciler ve engel türü değişen öğrenciler ayrı listelerde gösterilir.
- Kullanıcı onay verene kadar öğrenci veritabanı değiştirilmez. Güncelleme uygulandığında yeni öğrenciler eklenir ve değişen engel türleri güncellenir; yeni listede bulunmayan eski kayıtlar güvenlik amacıyla otomatik silinmez.
- Her karşılaştırma tarih, dosya adı ve fark ayrıntılarıyla yerel arşive kaydedilir; arşiv kayıtları ayrıca JSON olarak indirilebilir.
- BEP Planında yeni amaçların varsayılan ölçütü `%50 Bağımsız Yapar`dır ve istenirse değiştirilebilir.
- Materyaller ile değerlendirme yöntemleri görünür onay kutularından birden fazla seçilebilir. Yeni plan satırlarında Doğrudan gözlem, Kontrol listesi, Uygulamalı değerlendirme ve Yazılı değerlendirme varsayılan seçilidir.
- Performans her kısa dönemli amaç için `1/1` ile `1/5` arasında renk kodlu seçeneklerle girilir.

## Materyal, değerlendirme ve performans alanlarının ergonomisi

- Materyal ve değerlendirme seçeneklerindeki onay kutuları sabit 16×16 piksel boyutuna küçültülmüştür.
- Seçenek metinleri kutunun yanında, 13 piksel kalın yazıyla ve gerektiğinde alt satıra geçerek eksiksiz gösterilir.
- Yatay taşma kaldırılmış, seçenekler masaüstünde iki sütunlu ve dar ekranlarda tek sütunlu hale getirilmiştir.
- Performans seçeneklerinde radyo düğmeleri 14×14 piksel boyutundadır; `1/1`–`1/5` değerleri renkli alanların ortasında okunaklı biçimde gösterilir.

## Windows kurulum sürümü

- `BEP-Yerel-Kurulum-28.0.0.exe` Windows 64 bit bilgisayarlara kurulum yapar ve masaüstü ile Başlat menüsü kısayolları oluşturur.
- Öğrenci, okul, BEP ve karşılaştırma arşivi verileri her Windows kullanıcısının uygulamaya özel yerel veri klasöründe IndexedDB veritabanında kalıcı olarak saklanır.
- Uygulama çevrimdışı çalışır. Başka bilgisayara veri taşımak veya ek yedek almak için uygulamadaki JSON yedekleme ve geri yükleme düğmeleri kullanılabilir.
