# Problem Statement (v1 — Saha Görüşmesi ve Ampirik Veri Temelli Genişletme)

Bu doküman, kampüs kütüphane yetkilileriyle gerçekleştirilen yarı yapılandırılmış saha mülakatından elde edilen birincil nitel ve nicel veriler ışığında, *Campus Operations* projesinin problem uzayını daraltmak ve doğrulamak amacıyla güncellenmiştir.

---

## 1. Bu problemi kim yaşıyor?
- **Öğrenciler:** 1.423 kişilik toplam oturma/çalışma kapasitesine sahip kütüphane altyapısında, özellikle vize ve final haftalarında boş masa bulma baskısı yaşayan, masalarda uzun süreli sahipsiz bırakılan eşyalar ("hayalet işgal") nedeniyle fiziksel kaynaklara erişimi kısıtlanan öğrenciler.
- **Akademisyenler ve Ders Sorumluları:** Ders başı yoklama süreçlerinde manuel imza ve yoklama takibi yaparak değerli ders sürelerini harcayan eğitimciler.
- **Kütüphane / İdari Personel ve Bilgi İşlem:** Yoğun dönemlerde anlık doluluk verisini izleyemeyen, giriş turnike/sayaç sistemlerinin sınav dönemlerinde sıfırlanması nedeniyle kapasite planlamasını reaktif ve öngörülemez şekilde yürüten idari birimler.

---

## 2. Şu anda ne oluyor? (Saha Verileriyle Mevcut Durum Analizi)
Kütüphane yönetimiyle yapılan mülakat sonucunda elde edilen bulgular şu şekildedir:
- **Kapasite ve Pik Zaman Eşikleri:** Kütüphane bünyesinde 1.423 kişilik oturma alanı ve ~38.000 kitap bulunmaktadır. Yoğunluk özellikle sabah saatleri ile **10:00 – 13:00 aralığında** ve ders aralarında tavan (pik) yapmaktadır.
- **Dönemsel Davranışsal Değişimler:** 
  - *Normal Eğitim Dönemi:* Saat 17:00 sonrasında kütüphane salonları büyük ölçüde boşalmakta ve öğrencilerin masada kalış süresi ortalama 1–2 saat ile sınırlı kalmaktadır.
  - *Vize / Final Sınav Dönemi:* 17:00 sonrasında dahi yoğunluk artarak devam etmektedir. Öğrenciler sabah 09:00'dan akşam 17:00'ye kadar (veya tüm gün) aralıksız olarak masaları işgal etmektedir.
- **"Hayalet İşgal" ve Eşya Terk Vakaları:** Masalara mont, kitap ve çanta bırakılarak uzun süre masadan uzaklaşılması kronik bir sorundur. Mülakat bulgularına göre; **2 ay boyunca masada bırakılmış bir mimarlık projesi** veya **bir yarıyıl boyunca unutulan çantalar** gibi aşırı vakalar yaşanmış, bu durum öğrenciler arasında yer kapma tartışmalarına ve şikayetlerine zemin hazırlamıştır.
- **Gözetilemeyen Kapasite Metrikleri (Sayaç Kısıtı):** Girişteki sayaç sistemi yıl boyunca aktif çalışmasına rağmen, en kritik dönemeçler olan vize ve final haftalarında sıfırlanmaktadır. Bu teknik/idari aksaklık, en çok ihtiyaç duyulan anlarda idarenin net ve anlık doluluk oranını raporlayamamasına neden olmaktadır.
- **Arıza Bildirim Gecikmeleri:** Priz, bilgisayar ve donanım arızaları merkezi olarak otomatik izlenememekte; sürecin tamamen öğrenci bildirimine bağımlı olması nedeniyle müdahale süresi 1 gün ile 1 hafta arasında değişmektedir.

---

## 3. Bu problem neden önemli?
- **Bilişsel Yük ve Zaman Maliyeti:** 1.423 kişilik geniş bir alanda boş yer arayan öğrenci ciddi bir fiziksel ve bilişsel zaman kaybı yaşamakta, bu durum akademik stresini doğrudan artırmaktadır.
- **Kaynak Verimsizliği ve Fırsat Eşitsizliği:** Fiziksel olarak boş görünen ancak "hayalet işgal" altındaki masalar, gerçek anlamda ders çalışmak isteyen öğrencilerin adil erişim hakkını gasp etmektedir.
- **Veri Körlüğü (Data Blindness):** İdarenin kampüs kaynaklarını optimize edeceği en kritik dönemlerde (sınav haftaları) anlık analitik veriden mahrum kalması, geleceğe yönelik altyapı ve kaynak yatırımlarının yanlış yönlendirilmesine yol açmaktadır.

---

## 4. Problem hakkında henüz neyi bilmiyoruz?
- Sahipsiz bırakılan nesnelerin (çanta, kitap vb.) ortalama masayı terk etme/suistimal etme süresinin istatistiksel dağılımı.
- Giriş sayaç sistemlerinin sınav haftalarında neden ve hangi mekanizmayla sıfırlandığının teknik kök nedeni (Technical Root Cause).
- Öğrencilerin anlık doluluk bildirim mekanizmalarına (örn. mobil/QR tabanlı check-in) uyum sağlama ve sistemi manipüle etmeme (oyunlaştırma/suistimal) eğilimlerinin oranı.

---

## 5. Hangi varsayımlarda (assumptions) bulunuyoruz?
1. Öğrencilerin sistemsel olarak masaya otururken hızlı bir doğrulama (örn. QR okutma) yapmayı alışkanlık haline getireceği.
2. Sahipsiz eşya sorununu çözmek adına uygulanacak dijital zaman aşımı (timeout / inactivity timeout) mekanizmalarının caydırıcı olacağı.
3. Kütüphane yönetiminin ve idari birimlerin, şeffaf doluluk verilerini sunan bir operasyonel gösterge paneline (Dashboard) operasyonel destek vereceği.

---

## 6. Hangi bilgileri daha sonra kanıtlamamız/doğrulamamız gerekiyor?
- Kütüphane içi anlık doluluk ve bekleme süreleri ile öğrenci genel başarı/memnuniyet oranları arasındaki istatistiksel korelasyon.
- QR tabanlı dinamik yoklama ve doluluk takibinin kütüphane personelinin denetim yükünü ne ölçüde azalttığının pilot çalışma ile ölçülmesi.

---

## AI Usage Record
AI Tool(s): Gemini / ChatGPT
AI Role: Data Structuring / Synthesis of Field Interview Metrics
Human Review: Completed
Final Decision: Team