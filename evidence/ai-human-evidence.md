# AI vs. Human Decision Evidence

Takımımızın Campus Operations projesi kapsamında yapay zeka (AI) araçları ile gerçekleştirdiği fikir geliştirme oturumu sonucunda sunulan öneriler ve insan (mühendislik) kararlarımız aşağıda sunulmuştur.

---

## AI Proposal 1: Kütüphanedeki Her Tekil Masaya Sabit QR Kod Yapıştırılması

### AI Proposal
AI Önerisi: Kütüphanedeki her masaya benzersiz ve sabit bir QR kod yapıştırılsın. Öğrenciler oturduklarında bu QR kodu okutarak masayı kendilerine rezerve etsinler.

### Human Decision
MODIFY

### Why?
Sabit QR kodlar kolayca fotoğraflanıp arkadaş grupları arasında paylaşılabilir. Öğrenci kampüs dışından QR fotoğrafını okutarak uzaktan masa kapatabilir. Ayrıca her masa için fiziki QR basımı ve bakımı operasyonel yük oluşturur. Bu öneri; **Dinamik QR (ekranda değişen)** veya **Geofencing (Konum Doğrulama)** katmanı eklenerek değiştirilmelidir.

### Evidence Needed
- Kampüs içi Wi-Fi / GPS konum belirleme hassasiyeti test verileri.
- Sabit QR kod kullanımındaki suistimal oranlarını ölçen pilot alan testi kanıtı.

---

## AI Proposal 2: Derslik Kapısındaki QR Kod İle %100 Otomatik Yoklama Alınması

### AI Proposal
AI Önerisi: Derslik kapılarına tek bir QR kod konulsun. Öğrenciler içeri girerken QR okutsun ve yoklama akademisyen müdahalesi olmadan tamamen otomatik olarak sisteme işlensin.

### Human Decision
REJECT

### Why?
Ders başlangıç saatlerinde kapı önünde ciddi yığılma ve darboğaz (queue bottleneck) oluşacaktır. Ayrıca derse girmeden kapıdan geçerken QR okutup giden öğrencilerin tespiti imkansızlaşır. Yoklamanın %100 otomatikleşmesi yerine, akademisyenin ekranda okutan kişilerin listesini tek tıkla onayladığı/gözden geçirdiği hibrit bir yapı kurulmalıdır.

### Evidence Needed
- Ders giriş saatlerindeki öğrenci akış hızı (Throughput) ölçümleri ve kapı önü simülasyon sonuçları.
- Akademisyenlerin manuel kontrol süresi ile dijital liste onay süresi karşılaştırma analizi.

---

## AI Proposal 3: Kütüphane Krokisi Üzerinde Canlı Isı Haritası (Heatmap) Gösterimi

### AI Proposal
AI Önerisi: Öğrencilere kütüphane krokisi üzerinde bölge ve kat bazlı doluluk oranlarını renkli ısı haritası (Heatmap) şeklinde anlık olarak gösterin.

### Human Decision
ACCEPT

### Why?
Öğrencilerin tek tek masa aramak yerine genel boş alanları önceden görüp doğrudan o kata/bölgeye yönelmesini sağlar. Kullanıcı deneyimini (UX) iyileştirir, aramaya harcanan zamanı azaltır ve sistemin tekil masa hatalarına karşı toleransını artırır.

### Evidence Needed
- Kullanıcı Arayüzü (UX) A/B test sonuçları: Isı haritası gören ve görmeyen öğrencilerin boş yer bulma sürelerinin karşılaştırılması.

---

## AI Proposal 4: Okul Ana Giriş Turnike Verileri İle Derslik ve Kütüphane Doluluğunun Tahmin Edilmesi

### AI Proposal
AI Önerisi: Okul giriş-çıkış turnike verilerini makine öğrenmesi modeline besleyerek kütüphane ve dersliklerdeki anlık doluluk oranlarını tahmin edin.

### Human Decision
UNCERTAIN

### Why?
Okula giren her öğrencinin kütüphaneye mi, yemekhaneye mi yoksa dersliğe mi gittiği belirsizdir. Turnike verisi ile spesifik alan doluluğu arasındaki korelasyon düşük olabilir. Bu veri tek başına yetersiz kalabilir ancak ikincil bir destekleyici veri seti olabilir.

### Evidence Needed
- Geçmiş turnike giriş-çıkış sayıları ile kütüphane/derslik fiili doluluk sayıları arasındaki istatistiksel korelasyon analizi.

---

## AI Usage Record
AI Tool(s): ChatGPT / Gemini
AI Role: Drafting / Reviewing
Human Review: Completed
Final Decision: Team