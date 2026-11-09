# FEEDBACK_w06 — AI-Assisted MVP Development Guidance

**Ders:** Yazılım Geliştirme Süreçleri  
**Proje:** Campus Operations – UniPass  
**Takım:** Amine Sığırcı, Rabia Düzen, Afnan Mustafa  
**Konu:** MVP Development, Testing, Debugging & Engineering Evidence  
**Belge türü:** Öğretim Elemanı Geri Bildirimi ve Örnek Cursor Destek Promptu

## 1. Genel Değerlendirme

Sevgili UniPass Ekibi,

Önceki çalışmalarınızda kütüphane doluluk problemini, saha görüşmelerini, kullanıcı gereksinimlerini ve yapay zekâ destekli çözüm alternatiflerini sistematik biçimde ele almanız olumlu.

Özellikle sabit QR kodlarının kötüye kullanılabilmesi, hayalet rezervasyonlar, eşzamanlı erişim sorunları ve insan doğrulaması gereksinimlerini belirlemeniz güçlü mühendislik yaklaşımlarıdır.

Artık projenizi ilk çalışan prototipe dönüştürme aşamasına geçebilirsiniz.

Bu aşamadaki temel beklentimiz:

**Problem → Requirement → MVP → Testing → Engineering Evidence**

Aşağıdaki Cursor promptu örnek destek materyalidir. Öğrenciler tarafından doğrudan uygulanması zorunlu değildir. Alternatif teknik çözümler, gerekçelendirilerek tercih edilebilir.

---

## 2. Cursor Prompt 01 — UniPass Library Desk Management MVP

Sen, Yazılım Geliştirme Süreçleri dersinde üç kişilik bir öğrenci takımına rehberlik eden deneyimli bir yazılım mühendisisin.

**Repository:** https://github.com/amine-cd/campus-operations---team-UniPass

### A. Önce repository'yi incele

Şu dosyaları oku:

- `README.md`
- `docs/problem-statement-v0.md`
- `docs/problem-statement-v1.md`
- `docs/software-development-process.md`
- `FEEDBACK_w01.md`
- `FEEDBACK_w04.md`
- `evidence/ai-human-evidence.md`
- `evidence/incident-diagnosis.md`

Mevcut belgeleri ve Git geçmişini koru.

Özellikle QR suistimali, sahipsiz masa işgali, eşzamanlı işlemler, insan denetimi ve izlenebilirlik konusundaki önceki değerlendirmeleri dikkate al.

### B. MVP hedefi

12 masalık simülasyon alanı üzerinde çalışan basit bir kütüphane masa kullanım yönetimi uygulaması geliştir.

Bu prototip, gerçek kütüphane sistemine bağlı olmayacaktır.

İlk sürümde öğrenci kimlik doğrulaması, gerçek QR tarama, turnike entegrasyonu veya otomatik yoklama sistemi geliştirme.

**Teknolojiler:**

- HTML5
- CSS3
- Vanilla JavaScript
- LocalStorage

Gerekmedikçe React, backend ve veritabanı ekleme.

### C. Temel işlevler

**1. Desk Dashboard**

Ekranda 12 masa göster.

Her masa aşağıdaki durumlardan birinde bulunabilsin:

- AVAILABLE (Boş)
- OCCUPIED (Dolu)

Her masanın benzersiz bir kimliği olsun: D01–D12.

**2. Check-in**

Boş masaya Check-in yapılabilsin.

Check-in işlemi başarılıysa masa OCCUPIED durumuna geçsin.

Zaten dolu bir masaya ikinci kez Check-in yapılması engellensin.

**3. Check-out**

Dolu masaya Check-out yapılabilsin.

İşlem sonrasında masa AVAILABLE durumuna dönsün.

Boş masaya Check-out yapılmaya çalışıldığında sistem kontrollü bir uyarı versin.

**4. Occupancy Dashboard**

Şu bilgiler otomatik hesaplansın:

- Toplam masa sayısı
- Dolu masa sayısı
- Boş masa sayısı
- Doluluk yüzdesi

Sayaçlar her işlemden sonra güncellensin.

**5. Activity Log**

Check-in ve Check-out işlemleri için basit bir işlem geçmişi tutulabilsin.

Kayıtlarda masa kimliği, işlem türü ve zaman bilgisi yer alsın.

**6. Demo Reset**

Simülasyonu başlangıç durumuna döndüren bir buton oluştur.

Bu işlemden önce kullanıcıdan onay al.

### D. Requirements ve Acceptance Criteria

`docs/mvp-requirements.md` dosyasını oluştur.

Aşağıdaki gereksinimleri tanımla:

- REQ-01: Sistem 12 masanın durumunu gösterir.
- REQ-02: Kullanıcı boş masaya Check-in yapabilir.
- REQ-03: Kullanıcı dolu masaya Check-out yapabilir.
- REQ-04: Sistem aynı masaya ikinci Check-in işlemini reddeder.
- REQ-05: Doluluk sayacı doğru hesaplanır.
- REQ-06: İşlem geçmişi kaydedilir.
- REQ-07: Simülasyon başlangıç durumuna döndürülebilir.
- REQ-08: Verilerin eğitim amaçlı simülasyon olduğu açıkça belirtilir.

Her gereksinim için ölçülebilir kabul kriterleri yaz.

### E. Testing ve Verification

`docs/test-cases.md` dosyasında en az 10 test senaryosu oluştur.

Özellikle şunları test et:

1. Boş masaya Check-in.
2. Dolu masaya Check-out.
3. Aynı masaya ikinci Check-in.
4. Boş masaya Check-out.
5. Tüm masalar boşken doluluk hesabı.
6. Tüm masalar doluyken doluluk hesabı.
7. Check-in sonrası sayacın güncellenmesi.
8. Check-out sonrası sayacın güncellenmesi.
9. Sayfa yenileme sonrasında veri tutarlılığı.
10. Simülasyonun sıfırlanması.

Her senaryoda Test ID, Requirement ID, Preconditions, Test Steps, Expected Result, Actual Result ve Status alanları bulunsun.

Gerçekten çalıştırılmayan testleri PASS olarak işaretleme.

### F. Debugging ve Regression Testing

Hatalar bulunduğunda şu yaklaşımı kullan:

**Reproduce → Diagnose → Fix → Retest → Regression Test**

Örneğin doluluk sayacı yanlış çalışıyorsa yalnızca görüntülenen değeri değiştirme; sayacın hangi uygulama durumundan hesaplandığını araştır.

Düzeltme sonrasında daha önce çalışan işlevleri yeniden kontrol et.

### G. Technical Risks

Aşağıdaki riskleri `docs/technical-risks.md` dosyasında değerlendir:

- Aynı masaya tekrar Check-in.
- Eşzamanlı işlem girişimleri.
- Tarayıcı sekmeleri arasında veri tutarsızlığı.
- Kullanıcının Check-out yapmadan masayı terk etmesi.
- QR kodun başka biri tarafından kullanılması.
- İnternet bağlantısının kesilmesi.

Bu MVP'nin LocalStorage tabanlı ve tek tarayıcıya odaklı olduğunu açıkça belirt.

Gerçek çok kullanıcılı eşzamanlılık kontrolü, güvenli kimlik doğrulama ve QR suistimalini önleme mekanizmalarının bu mimariyle doğrulanamayacağını gizleme.

### H. Engineering Evidence

`docs/engineering-evidence.md` dosyasında şu bilgileri hazırla:

- Geliştirilen işlevler.
- Gereksinimlerle kod arasındaki bağlantılar.
- Test senaryoları ve gerçek sonuçları.
- Bilinen sorunlar.
- AI tarafından önerilen değişiklikler.
- İnsan tarafından gözden geçirilen kararlar.
- Eksik veya sonraki sürüme bırakılan özellikler.

Test ve inceleme kayıtlarını uydurma.

### I. Development Process

Takımın seçtiği Iterative & Incremental yaklaşımını ve Scrum–Kanban hibrit iş akışını koru.

İlk yinelemenin amacı, 12 masalık kullanım prototipini doğrulanabilir biçimde geliştirmek olsun.

Kanban akışı:

Backlog → To Do → In Progress → Review → Done

Üç kişilik takım için başlangıç WIP limitini gerekçelendirerek öner.

### J. Definition of Done

Bir görev ancak şu koşullarda tamamlanmış kabul edilebilir:

- Kabul kriterleri karşılanmıştır.
- Gerekli testler uygulanmıştır.
- Test sonuçları belgelenmiştir.
- Kod değişiklikleri izlenebilirdir.
- Belgeler güncellenmiştir.
- Takım arkadaşının kod incelemesi yapılmıştır.

### K. Çalışma sırası

1. Repository analizi.
2. MVP gereksinimleri.
3. Basit arayüz ve uygulama mantığı.
4. Test senaryoları.
5. Teknik risk analizi.
6. Engineering Evidence.
7. README güncellemesi.
8. Sonuç raporu.

Benim açık onayım olmadan Commit, Push, Pull Request veya Merge yapma.

Sonuç raporunda yapılan değişiklikleri, doğrulanan gereksinimleri, çalıştırılan testleri ve tamamlanmamış işleri belirt.

---

## 3. Öğretim Elemanı Beklentileri

UniPass ekibinden yalnızca çalışan bir uygulama değil, aşağıdaki mühendislik yeterliliklerini göstermesi beklenmektedir:

- İşlevsel gereksinimlerden test senaryosu türetebilmek.
- Olumlu ve olumsuz testleri gerçekleştirebilmek.
- Hataları sistematik biçimde ayıklayabilmek.
- Kod değişikliklerinin etkisini regresyon testleriyle incelemek.
- Yapay zekâ çıktısını insan denetimine tabi tutmak.
- GitHub üzerinden mühendislik izlenebilirliği sağlamak.
- Teknik sınırlılıkları ve doğrulanmamış varsayımları açıkça belgelemek.

## 4. Akademik Değerlendirme İlkesi

**AI-Assisted Development ≠ Autonomous Engineering**

**Working Prototype ≠ Verified Software**

**Requirement → Implementation → Test → Engineering Evidence**

Bu prompt bir örnek rehberdir. Öğrencilerin değerlendirilmesinde esas alınacak unsur, yapay zekânın ne kadar kod ürettiği değil; öğrencilerin kendi kararlarını gerekçelendirebilmesi, testleri gerçekleştirmesi ve mühendislik kanıtlarını sunabilmesidir.

Başarılar dilerim.

**Dr. Öğr. Üyesi Murat Göksu**
