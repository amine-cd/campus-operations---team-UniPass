# Software Development Process Selection

## 1. Project Information

- Project Name: Campus Operations (UniPass)
- Team Name: Team UniPass
- Repository: https://github.com/amine-cd/campus-operations---team-UniPass.git
- Date: 2026-10-17
- Version: 1.0

---

## 2. Project Overview

Kampüs genelinde özellikle vize ve final haftalarında yaşanan kütüphane/derslik doluluk problemini çözmek, "hayalet işgal" (sahipsiz eşya bırakma) sorununu ortadan kaldırmak ve yoklama süreçlerini dijitalleştirmek amacıyla geliştirilen yazılım projesidir.

- **Intended Users (Hedef Kitle):** 
  1. Öğrenciler (Boş masa arayan, hızlı check-in yapmak isteyenler)
  2. Akademisyenler (Ders yoklamalarını pratik şekilde alanlar)
  3. Kütüphane ve İdari Personel (Anlık kapasiteyi ve doluluğu izleyen yönetim birimi)
- **Problem Addressed (Çözülen Problem):** 1.423 kişilik kütüphane kapasitesinin verimsiz kullanımı, yer ararken harcanan zaman maliyeti, manuel yoklama süreçlerindeki ders verim kaybı ve anlık veri eksikliği.
- **Value Provided (Sağlanan Değer):** Şeffaf ve anlık doluluk haritası, QR tabanlı adil ve hızlı yer yönetimi, optimize edilmiş ders yoklama süreçleri ve idare için veri odaklı karar alma altyapısı.

---

## 3. Project Characteristics

| Criterion | Assessment | Explanation |
|---|---|---|
| Requirements Clarity | Medium | Temel problem net (yer bulma ve yoklama) ancak saha mülakatları ve kullanıcı geri bildirimleriyle kurallar (örn. süre aşımı, suistimal önleme) zamanla şekilleniyor. |
| Requirements Volatility | Medium | Kullanıcı deneyimi (UX) testleri ve test pilotları ilerledikçe QR doğrulama mekanizmaları ve arayüz gereksinimleri güncellenebilir. |
| Technical Complexity | Medium | Mobil/Web arayüzleri, QR okutma mantığı, zaman aşımı (timeout) state machine yapıları ve veri tabanı eşzamanlılığı gerektiriyor. |
| Project Risk | Medium | Öğrencilerin sistemi suistimal etme (uzaktan QR okutma / proxy) riski ve sistemin benimsenme oranı en büyük proje riskleridir. |
| Stakeholder Feedback Need | High | Kütüphane idaresinin ve öğrenci kullanıcıların geri bildirimleri projenin başarısı için kritik öneme sahiptir. |
| Team Experience | Medium | Ekip üyeleri yazılım geliştirme ve temel mimari konularda eğitim almakta olup, çevik süreçleri ilk kez uçtan uca pratik etmektedir. |

---

## 4. Process Alternatives

| Approach | Advantages for Our Project | Limitations |
|---|---|---|
| Waterfall | Planlaması ve aşamaları baştan çok net bellidir, dokümantasyonu basittir. | Değişen gereksinimlere (saha mülakatı bulguları vb.) karşı çok katı ve esneksizdir; erken geri bildirim alınamaz. |
| Scrum | Belirli sprint'lerle çalışmaya olanak tanır, düzenli teslimat ve paydaş geri bildirimi sağlar. | Proje ölçeğimiz ve ders süreci göz önüne alındığında sık sprint toplantıları ve katı rolleri yönetmek mevcut ekip yapısı için fazla ağır gelebilir. |
| Kanban | Akış odaklıdır, iş yükünü görselleştirir (To Do -> In Progress -> Done), değişen önceliklere karşı esnektir ve küçük takımlar için sürdürülebilirdir. | Sıkı sprint bitiş tarihleri olmadığından disiplin sağlanmazsa işler uzayabilir. |

---

## 5. Selected Development Approach

### 5.1 Our Decision

- **Development Approach:** Agile (İteratif ve Artımlı Yaklaşım)
- **Team Management Framework / Method:** Kanban-Scrum Hibrit (Esnek Akış ve Kısa Döngüler)
- **Workflow Visualization Method:** GitHub Projects (Kanban Board)

### 5.2 Selection Rationale

1. **Project requirements:** Gereksinimlerimiz saha mülakatları ile zenginleştiği ve evrildiği için esnek ve değişime açık bir yaklaşım şarttır.
2. **Expected changes:** QR doğrulama ve zaman aşımı kurallarında kullanıcı testlerine bağlı olarak değişiklikler yapılması beklenmektedir.
3. **Team size and experience:** 3 kişilik takımımız için aşırı bürokratik roller barındırmayan, doğrudan iş odaklı bir model gereklidir.
4. **Technical risks:** Suistimal senaryolarına karşı erken prototipleme ve test gerektirdiğinden iteratif ilerlemek riskleri azaltır.
5. **Feedback and delivery needs:** Kütüphane yönetimi ve kullanıcıların geri bildirimleri süreç içinde ürüne hızlıca entegre edilmelidir.

---

## 6. Team Organization

| Team Member | Responsibilities |
|---|---|
| Amine Sığırcı | Mimari Tasarım, Core Backend/Logic, Git/Repository Yönetimi |
| Afnan Mustafa| Arayüz Geliştirme (UI/UX) ve Dokümantasyon (`docs/`) |
| Rabia Düzen| Veritabanı Tasarımı ve İş Süreçleri Analizi (`evidence/`) |
|all members | Test Senaryoları, Kalite Kontrol ve Saha Verisi Entegrasyonu |

**Koordinasyon Düzeni:** Takım haftada 2 kez çevrim içi/yüz yüze kısa senkronizasyon toplantıları yapar; görev dağılımı ve ilerleme durumu GitHub Projects panosu üzerinden takip edilir.

---

## 7. Development Workflow

İşler bir fikir aşamasından tamamlanmış ürüne şu adımlarla taşınır:
`Backlog` → `To Do` → `In Progress` → `Review` → `Done`

- **Task Selection:** Backlog'daki öncelikli görevler ekip toplantısında belirlenir ve ilgili kişiye atanır.
- **Task Assignment:** Her üye uzmanlık alanına göre görevi üstlenir.
- **Progress Monitoring:** GitHub Projects panosu üzerinden haftalık olarak izlenir.
- **Completion Criteria:** Kod veya doküman tamamlanıp takım arkadaşı tarafından incelendiğinde (`Review`) bitti kabul edilir.

---

## 8. Quality Assurance

### Definition of Done (DoD)
Bir işin tamamlandı (`Done`) kabul edilmesi için şu şartları sağlaması gerekir:
- [ ] İlgili `.md` veya kod dosyası eksiksiz yazılmış ve kurallara uygun formatlanmıştır.
- [ ] Takım üyelerinden en az biri tarafından gözden geçirilmiştir (Peer Review).
- [ ] GitHub repository'sine anlamlı bir commit mesajıyla (`git commit -m`) gönderilmiştir.
- [ ] Projenin genel amaç ve mühendislik kriterleri ile çelişmediği doğrulanmıştır.

---

## 9. Process Evaluation and Improvement

- **Identifying Problems:** GitHub panosunda biriken işler veya zamanında tamamlanamayan görevler süreç tıkanıklıklarını gösterir.
- **Review Frequency:** Her hafta sonunda 15 dakikalık kısa bir retrospektif (durum değerlendirmesi) yapılır.
- **Handling Failures:** Seçilen yaklaşım yavaş kalırsa veya görev dağılımında aksama olursa Kanban limitleri daraltılır ve iş yükü yeniden dengelenir.

---

## 10. AI Usage Declaration

- **AI Tool:** Gemini / ChatGPT
- **Purpose of Use:** Dokümanın yapılandırılması, akademik ve mühendislik terminolojisine uygun metin düzenlemesi.
- **Human Verification:** Takım tarafından okunmuş, proje gerçekleriyle (saha mülakatı verileri) karşılaştırılıp onaylanmıştır.
- **Final Decision Made By:** Team UniPass (Tüm Takım Üyeleri)

---

## 11. Team Decision

We confirm that the selected development approach has been discussed and agreed upon by the team.

| Team Member | Agreement |
|---|---|
| Amine Sığırcı | Approved |
| Rabia Düzen | Approved |
| Afnan Mustafa | Approved |
