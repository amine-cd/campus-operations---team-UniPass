# AI–Human Engineering Evidence (`ai_human_evidence.md`)

## 1. Bağlam ve Mühendislik İlkesi
- **Proje:** Campus Operations (UniPass) — Kütüphane & Derslik Yönetim Konsolu
- **İncelenen Sürüm:** `index.html`
- **Temel İlke:** `AI Proposes → Human Decides → Evidence Supports Verification`

## 2. AI Kullanım Beyanı
- **Kullanılan AI Aracı:** Antigravity (Gemini 3.8 Flash High)
- **Kullanım Amacı:** Tanımlanan 6 test senaryosu (`TEST-L1`, `TEST-L2`, `TEST-M1`, `TEST-M2`, `TEST-H1`, `TEST-H2`) üzerinden `index.html` kodundaki fonksiyon, DOM ve state akışlarını inceleyerek bulguları ve olası riskleri raporlamak.
- **Kayıt Kanıtı:** Test süreci ekran görüntüleriyle sırayla kayıt altına alınmıştır.

## 3. İnsan Kararı ve Doğrulama Tablosu (Human-in-the-Loop)

| Test / İnceleme Alanı | AI'nın Çıktısı / Bulgusu | İnsan Kararı ve Doğrulaması | 
|---|---|---|
| **TEST-L1** (Rol & Sekme Geçişi) | Rol ve sekme geçişlerinin çalıştığı; ancak alt görev çubuğunun (Superbar) senkronize olmadığı ve RBAC kısıtı bulunmadığı raporlandı. | Prototip kapsamının simülasyon olduğu göz önünde bulundurularak bulgu test raporuna eklendi; sonraki iterasyon için not alındı. | 
| **TEST-L2** (Masa Filtreleme) | Filtrelerin `AND` mantığıyla çalıştığı; ancak `updateStatsSummary()` fonksiyonunun filtrelenmiş veri yerine tüm listeyi baz aldığı tespit edildi. | İstatistik hesaplama mantığı ve erken dönüş (`early return`) notu rapora işlendi. | 
| **TEST-M1** (15 Dk Mola Akışı) | Mola state ve sayacının güncellendiği; ancak `isMine` kontrolünün `ghost_warning` temasını görsel olarak ezdiği belirtildi. | Mola ve görsel öncelik davranışı kayıt altına alındı. | 
| **TEST-M2** (Derslik Yoklama) | Durum geçişi ve manuel öğrenci eklemenin çalıştığı; ancak durum değişiminde eski `time`/`method` alanlarının kalabildiği ve `prompt` iptalinde `null` ID riski bulunduğu belirtildi. | Veri tutarlılığı notu test dokümanına dahil edildi. |
| **TEST-H1** (Zaman Aşımı / Ghost Release) | Zaman aşımında masanın boşaltılıp olay günlüğüne eklendiği; modal açıkken senkronizasyon kaybı riski bulunduğu raporlandı. | Otomatik boşaltma ve loglama davranışı doğrulandı; modal senkronizasyonu iyileştirme listesine eklendi. | 
| **TEST-H2** (Dayanıklılık & Kalıcılık) | Harici backend olmadan çalıştığı; ancak `localStorage` kullanılmadığı için sayfa yenilemede verilerin sıfırlandığı ve Tailwind CDN bağımlılığı bulunduğu belirtildi. | Kalıcılık (persistence) ve çevrimdışı dayanıklılık bulgusu net şekilde kaydedildi. |

## 4. Sonuç ve İyileştirme Notları
AI tarafından üretilen test raporu ekran görüntülerle belgelenmiş ve insan kontrolünden geçirilerek test dokümanına aktarılmıştır. Sonraki geliştirmelerde `localStorage` entegrasyonu, `isMine` ve `ghost_warning` görsel önceliğinin düzenlenmesi ve görev çubuğu senkronizasyonu önceliklendirilecektir.
