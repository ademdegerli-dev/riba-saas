# BEP 2025-2026 Eskiz.xlsm inceleme ve alan eşleme raporu

## İncelenen yapı

| Sayfa | Etkin boyut / baskı alanı | Dolu veya biçimli hücre | Formül | Birleştirilmiş alan |
| --- | --- | ---: | ---: | ---: |
| BEP_VeriGir | A1:CO63 baskı alanı; veri/formüller 113. satıra uzanıyor | 9.777 | 234 | 0 |
| 1 | A1:E30 baskı alanı | 215 | 27 | 26 |
| 2 | A1:C15 | 29 | 15 | 5 |
| 3 | A1:J22 | 198 | 1 | 19 |
| 4 | B1:E29 baskı alanı; yardımcı hücreler BM sütununa uzanıyor | 121 | 29 | 15 |
| 5 | A1:E26 | 104 | 12 | 8 |
| 6 | A1:E29 görünümü; yardımcı hücreler BP sütununa uzanıyor | 117 | 28 | 16 |
| Kpk | A1:E35 | 83 | 4 | 10 |

Kaynakta çoğu çıktı A4 yataydır; 1 ve Kpk dikeydir. İstenen web çıktılarının tümünde A4 yatay, dar kenar boşluklu yazdırma CSS’i kullanılmıştır.

## BEP_VeriGir alanları

BEP_VeriGir ana tablosu A–CO arasında 93 başlık içerir:

- A–I: Sıra, Grup, No, Sınıfı/Şubesi, Adı Soyadı, Öğretmeni, Engel Durumu, Önerilen Hizmet, Doğum Tarihi.
- J–P: Önceki destek, güncel okul dışı destek, cihaz/materyal, sağlık, ortam düzenlemesi, BEP başlangıç ve bitiş tarihleri.
- Q–AC: Anne, baba, veli/vasi ad-soyad, telefon, ev/iş adresleri ve öğrenci T.C. kimlik numarası.
- AD–AQ: Gelişim öyküsü; altı gelişim alanı/ders ve altı performans düzeyi; davranış problemi.
- AR–BG: Dört okul içi destek hizmeti; her kayıtta hizmet türü, gelişim alanı/ders, haftalık süre ve sorumlu kişi.
- BH–BP: Aile bilgilendirme sıklığı/yolu, aile eğitimi kararı/yolu, üç diğer karar, sonraki toplantı ve genel değerlendirme.
- BQ–BZ: Komisyon başkanı, katılan veli, sınıf öğretmeni, beş alan öğretmeni, PDR uzmanı ve okul müdürü.
- CA–CO: Nakil, toplantı günü/saati/yeri, katılım, yabancı dil ve din dersi gün-saatleri, ek sütunlar ve not. Uygulamada anlamlı başlığı olan CA–CH ve CN korunmuş; yalnız “Sütun8–12 / Sütun63” adlı CI–CM ve CO için uydurma anlam üretilmemiştir.

BR, BS ve CO sütunlarında satır bazlı CONCATENATE formülleri vardır. BR aile adlarını, BS öğretmeni, CO anne ve baba adını birleştirir. Uygulama bunları merkezi veriden üretir.

## Sayfa bağımlılıkları

### 1 — Öğrenci ve aile bilgileri

27 formül, G7 sıra anahtarıyla BEP_VeriGir A:AY aralığında VLOOKUP yapar. E, D, C, AC, I, H, G, J–P ve Q–AB alanları kullanılır. Sabit üst kurum, okul, yıl ve dosya başlığı merkezi okul bilgisi yapılmıştır.

### 2 — Eğitsel performans

Başlık Kpk üzerinden üretilir. Gelişim öyküsü AD; altı alan/performans çifti AE–AP; davranış problemi AQ sütunundan gelir.

### 3 — Bireyselleştirilmiş eğitim planı

Yalnız başlık formüldür. B6:J17 arasındaki 12 plan satırının BEP_VeriGir bağlantısı yoktur. Her satırda uzun/kısa dönemli amaç, ölçüt, yöntem, materyal, başlangıç-bitiş, değerlendirme yöntemi/tarihleri ve performans gerekir. B5:J5 ders adı ve C19:J19 ortam düzenlemesi de gerekir. Bunların tamamı veri girişine eklenmiştir.

Birleşimler dört uzun dönemli amaç bloğunu gösterir: B6:B9, B10:B11, B12:B14 ve B15:B17.

### 4 — BEP geliştirme birimi kararları

AR–BG’den dört hizmet; BH–BK’den aile süreci; BL–BN’den üç karar; BO’dan sonraki toplantı; BP’den genel değerlendirme alınır.

### 5 — BEP geliştirme birimi üyeleri

BQ–BZ komisyon başkanı, veli, sınıf öğretmeni, beş alan öğretmeni, rehber öğretmen ve müdürü besler. BEP_VeriGir’de bulunmayan yedi alan vardır: Özel Eğitim Değerlendirme Kurulundan üye, beş meslek dersi alan öğretmeni ve Diğer. Bunlar giriş ekranına eklenmiştir. İmza hücreleri fiziksel çıktı alanıdır.

### 6 — Yıl sonu kararları

4. sayfayla aynı merkezi verileri kullanır. Sonraki toplantı alanı kaynakta sabit “Yıl sonunda değerlendirme yapılacak.” metnidir.

Kaynak 6. sayfadaki B21:B23 formülleri BL/BM’yi birleştirirken VLOOKUP sonuçları BO/BP’dedir; bu yüzden önbellekte yalnız “-” görünür. Uygulama kararları doğrudan merkezi BL–BN karşılığından gösterir.

### Kpk — Kapak

B16 tarih; B20 başlık; E31 öğrenci adı; E32 okul; E33 numara ve sınıf; B34 sınıf öğretmenidir. Okul adı kaynakta sabittir ve uygulamada merkezi okul bilgisine bağlanmıştır. Kapak tarihi boşsa güncel tarih kullanılır.

## Uygulama yaklaşımı

- Tek merkezi veri nesnesi tüm önizlemeleri besler.
- Değişiklikler localStorage alanına otomatik kaydedilir.
- JSON dışa/içe aktarma aynı veri şemasını yedekler.
- BEP_VeriGir yalnız giriş; 1–6 ve Kpk ayrı çıktı görünümleridir.
- PDF için çevrimdışı tarayıcı yazdırma özelliği ve A4 yatay, dar kenar boşluklu @page kuralı kullanılır.
