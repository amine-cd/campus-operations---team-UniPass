# UniPass Campus Operations — MVP QA Test Raporu

- **İncelenen Dosya:** `index.html` (İstemci Taraflı Prototip)
- **Test Ortamı:** Antigravity QA İncelemesi (Kod & Simülasyon Analizi)
- **Kapsam:** 2 Düşük, 2 Orta, 2 Yüksek Seviye Test Senaryosu

---

## Düşük Seviye Testler (Low-Level)

### TEST-L1: Rol Geçişi ve Sekme Senkronizasyonu
- **İncelenen Yapılar:** `switchRole(role)`, `switchSection(section)`, `showToast(message, type)`, `#btn-role-student`, `#btn-role-faculty`, `#btn-role-admin`, `#current-user-title`, `#section-library`, `#section-classrooms`, `#section-analytics`, `#address-bar-path`.
- **Bulgular:** `faculty` ve `admin` rollerine geçişte `currentRole` güncellenmekte, `#current-user-title` ilgili kullanıcıya (`Doç. Dr. Selin Doğan` / `Kaan Erdem`) çevrilmekte ve `switchSection()` aracılığıyla ilgili sekme görünür hâle gelirken diğer sekmeler gizlenmektedir.
- **Tespit Edilen Risk / Not:**
  - **Alt görev çubuğu (Superbar) senkronizasyonu:** `switchSection()` yalnızca üst `.win7-tab` elemanlarını güncellemekte; alt görev çubuğundaki `.win7-task-item` elemanları senkronize olmamaktadır.
  - **Erişim denetimi (RBAC):** Rol geçişi yalnızca görünüm yönlendirmesi yapmaktadır; kullanıcı üst sekmelerden diğer görünümlere doğrudan geçiş yapabilmektedir.

### TEST-L2: Masa Filtreleme ve Arama Kombinasyonu
- **İncelenen Yapılar:** `renderDesks()`, `selectZone(zone)`, `handleFilterChange()`, `handleDeskSearch()`, `filterByStatus(status)`, `togglePowerFilter()`, `updateStatsSummary()`, `desks` dizisi (35 örnek masa).
- **Bulgular:** Bölge (`#zone-btn-*`), durum (`#status-filter`), priz (`#toggle-power-filter`) ve masa ID araması (`#desk-search`) `AND` mantığıyla filtrelenmektedir. Eşleşme olmadığında boş durum (`Empty State`) mesajı gösterilmektedir.
- **Tespit Edilen Risk / Not:**
  - **İstatistik tutarsızlığı:** `updateStatsSummary()` filtrelenmiş liste yerine ham `desks` dizisi üzerinden kapasite çarpanıyla hesaplama yapmaktadır.
  - **Erken dönüş (Early return):** `filtered.length === 0` durumunda `return` öncesinde `updateStatsSummary()` çağrılmamaktadır.
  - **Arama kapsamı:** Arama yalnızca `d.id` alanı üzerinden yapılmakta; öğrenci adı veya numarasıyla arama yapılmamaktadır.

---

## Orta Seviye Testler (Medium-Level)

### TEST-M1: 15 Dakikalık Mola Başlatma ve Görsel/Durum Güncellemesi
- **İncelenen Yapılar:** `toggleStudentBreak()`, `updateActiveSessionBanner()`, `renderDesks()`, `formatSeconds(sec)`, `#btn-take-break`, `#break-timer-display`, `#break-countdown`, `studentSession`, `desks`.
- **Bulgular:** Mola başlatıldığında `studentSession.inBreak = true` olmakta, `breakSecondsRemaining` ve `desk.breakTime` değerleri `900` saniye olarak ayarlanmakta, `desk.status` değeri `'ghost_warning'` yapılmakta ve geri sayım banner'da gösterilmektedir.
- **Tespit Edilen Risk / Not:**
  - **Görsel ezilme (`isMine` override):** `renderDesks()` içinde `if (isMine)` koşulu `desk.status === 'ghost_warning'` kontrolünden sonra çalıştığı için mola durumundaki kendi masanız `desk-ghost` yerine `desk-mine` temasıyla çizilmektedir.

### TEST-M2: Derslik Yoklama Durumu Değiştirme ve Manuel Öğrenci Ekleme
- **İncelenen Yapılar:** `toggleStudentAttendanceStatus(index)`, `addNewStudentPrompt()`, `renderAttendanceTable()`, `playSound(type)`, `#attendance-tbody`, `#stat-attended-count`, `#stat-excused-count`, `#stat-absent-count`, `#proj-attended-count`, `attendanceList`.
- **Bulgular:** Durum geçişi `attended → excused → absent → attended` döngüsüyle çalışmakta; `addNewStudentPrompt()` ile eklenen öğrenci `attendanceList.unshift(...)` aracılığıyla listenin başına eklenmekte ve katılım sayıları yenilenmektedir.
- **Tespit Edilen Risk / Not:**
  - **Eski alanların temizlenmemesi:** Durum `attended` → `excused`/`absent` değiştiğinde önceki `time` ve `method` değerleri temizlenmemektedir.
  - **`prompt` iptal durumu:** İsim boşsa çıkış yapılmakta ancak öğrenci numarası `prompt`'unda iptal basılırsa `id` değeri `null` kalabilmektedir.
  - **Kayıtlı öğrenci sayısı:** Karttaki `65` değeri statik kalırken liste boyutu dinamik artmaktadır.

---

## Yüksek Seviye Testler (High-Level)

### TEST-H1: Mola Zaman Aşımı ve Otomatik Masa Boşaltma (Ghost Seat Release)
- **İncelenen Yapılar:** `simulateGhostTimeout()`, `startSessionTimer()`, `renderGhostLogs()`, `renderDesks()`, `updateActiveSessionBanner()`, `playSound('warning')`, `showToast(...)`, `#active-session-banner`, `#ghost-logs-container`, `#modal-desk`.
- **Bulgular:** Zaman aşımı tetiklendiğinde ilgili masa `available` durumuna çekilmekte (`user: null`, `breakTime: 0`), `studentSession` sıfırlanmakta, oturum banner'ı gizlenmekte ve `ghostLogs` başına zaman damgalı kayıt eklenmektedir.
- **Tespit Edilen Risk / Not:**
  - **Açık kalan modal senkronizasyonu:** Masa detay penceresi (`#modal-desk`) açıkken arka planda zaman aşımı gerçekleşirse pencere otomatik kapanmamakta veya içeriği güncellenmemektedir.
  - **Çift sayaç azaltımı:** `startSessionTimer()` içinde hem `studentSession.breakSecondsRemaining` hem de `desks` dizisindeki `d.breakTime` her saniye azaltılmaktadır.

### TEST-H2: İstemci Tarafı Dayanıklılık, Zamanlayıcılar ve Kapsam Sınırı
- **İncelenen Yapılar:** `startSessionTimer()`, `startOtpTicker()`, `initLiveClock()`, `playSound()`, `desks`, `attendanceList`, `ghostLogs`, `issuesList`, `studentSession`.
- **Bulgular:** Uygulama harici bir backend API veya veritabanı gerektirmeden istemci belleğinde çalışmaktadır. Ancak tasarım için harici Tailwind CDN (`gstatic.com`) bağlantısı kullanılmaktadır.
- **Tespit Edilen Risk / Not:**
  - **Veri kalıcılığı (`localStorage` eksikliği):** Sayfa yenilendiğinde (`F5`) `localStorage` / `sessionStorage` kullanılmadığı için tüm oturum, yoklama, olay günlüğü ve arıza değişiklikleri sıfırlanmaktadır.
  - **Tarayıcı sekme yavaşlatması (`tab throttling`):** Sekme arka plana alındığında `setInterval` zamanlayıcıları gecikebilmektedir.