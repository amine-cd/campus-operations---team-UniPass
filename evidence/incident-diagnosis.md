# Incident Diagnosis: YerimVar Vakası

Bu çalışmada, YerimVar sisteminin başarısızlık/çöküş süreçlerine ait 3 kritik kopma noktası (breakpoint) ve arkasındaki mühendislik süreç eksiklikleri teşhis edilmiştir.

---

## Breakpoint 1: Hayalet Rezervasyon ve Sürekli Varlık Kontrolü Eksikliği

### What happened?
Kullanıcılar sistem üzerinden yer bildirimi yaptıktan sonra alandan ayrılmalarına veya masaya hiç oturmamalarına rağmen sistemde masa "dolu" görünmeye devam etti. Bu durum, sisteme güvenip alana gelen diğer kullanıcıların boş sanılan masaları dolu bulmasına veya atıl kalmış boş masalara oturanamamasına yol açtı.

### Process Gap
Geliştirme sürecinde **Kullanıcı Yaşam Döngüsü ve Davranış Modeli (User Lifecycle & Behavior Modeling)** eksikti. Mühendislik ekibi sistemi yalnızca "Giriş/İşgal Etme" eylemi üzerine tasarlamış; "Çıkış/Terk Etme", "Zaman Aşımı (Timeout)" ve "Unutma" durumları için durum makinesi (state machine) ve otomatik doğrulama süreçlerini kurgulamamıştır.

### Missing Evidence
- Gerçek zamanlı varlık kanıtı (Heartbeat / Passive Presence Evidence).
- Kullanıcı terk etme/çıkış oranlarını ve zaman aşımı durumlarını gösteren telemetry test verileri.

---

## Breakpoint 2: Uzaktan Bildirim ve Sahte Konum Suistimali (Proxy / Location Spoofing)

### What happened?
Kullanıcılar fiziki olarak kütüphane veya derslikte bulunmadıkları halde, QR kod görselinin fotoğrafını arkadaşlarıyla paylaşarak veya konum şaşırtma (spoofing) yöntemleriyle uzaktan kendilerini alandaymış gibi gösterdi. Bu durum veri güvenilirliğini tamamen yok etti.

### Process Gap
**Güvenlik ve Tehdit Modellemesi (Threat Modeling & Zero-Trust Verification)** süreci yürütülmemiştir. Statik verilerin (sabit QR kodlar) fiziksel kanıt yerine geçemeyeceği gerçeği göz ardı edilmiş, istemci tarafındaki (client-side) verilere koşulsuz güvenilmiştir.

### Missing Evidence
- İstemcinin fiziksel lokasyonda olduğunu doğrulayan çok katmanlı doğrulama kanıtı (Dynamic Token / Geofence / Local Network Check).
- Kötüye kullanım senaryolarına karşı yapılan sızma ve güvenlik testi raporları.

---

## Breakpoint 3: Yoğun Zamanlarda (Pik Saatlerde) Eşzamanlı İstek Yükü Çöküşü

### What happened?
Sınav haftaları ve ders başlangıç saatleri gibi eşzamanlı kullanımın tavan yaptığı pik dönemlerde sistem aşırı istek yükünü kaldıramayarak çöktü veya yanıt veremez hale geldi.

### Process Gap
**Performans ve Kapasite Planlama Süreci (Load & Stress Testing)** mühendislik yaşam döngüsüne dahil edilmemiştir. Sistem yalnızca düşük kullanıcı sayılı basit senaryolarda test edilmiş, gerçek kampüs pik yük koşulları altında doğrulanmamıştır.

### Missing Evidence
- Eşzamanlı kullanıcı (Concurrent Users) ve İstek/Saniye (RPS) yük testi raporları (Load / Spike Testing Reports).
- Sistem darboğazlarını (Bottleneck) ve veritabanı kilitlenmelerini gösteren performans metrikleri.

---

## AI Usage Record
AI Tool(s): ChatGPT /  Gemini
AI Role: Drafting / Reviewing
Human Review: Completed
Final Decision: Team