# Instructor Feedback — Week 01 Engineering Evidence

**Course:** Yazılım Geliştirme Süreçleri  
**Project:** Campus Operations — Team UniPass  
**Team:** Amine Sığırcı · Rabia Düzen · Afnan Mustafa  
**Review:** Week 01 Engineering Evidence

---

## Overall Assessment

Takımınızın Week 01 çalışmasını başarılı ve dersin Engineering Evidence
yaklaşımıyla uyumlu buldum.

Çalışmanızın en güçlü yönü yalnızca istenen dosyaları oluşturmuş olmanız değil;
problem, varsayım, yapay zekâ önerisi, insan kararı ve ihtiyaç duyulan kanıt
arasındaki ilişkiyi görünür hâle getirmenizdir.

Özellikle aşağıdaki mühendislik yaklaşımı repository genelinde açık biçimde
görülebilmektedir:

**Problem → Human Judgment → AI Assistance → Engineering Evidence → Repository**

Bu, ders boyunca geliştirmeye devam edeceğimiz mühendislik düşüncesinin
doğru bir başlangıcıdır.

---

## 1. Problem Definition — Strong

`docs/problem-statement-v0.md` yalnızca bir proje fikri tanımlamakla
kalmıyor; problemi farklı stakeholder perspektiflerinden ele alıyor:

- öğrenciler,
- akademisyenler,
- kampüs yönetimi.

Ayrıca **“henüz neyi bilmiyoruz?”**, **assumptions** ve
**“hangi bilgileri doğrulamamız gerekiyor?”** ayrımının yapılmış olması
özellikle değerlidir.

Bu yaklaşım, problem tanımını kesin bir gerçek gibi kabul etmek yerine
doğrulanması gereken bir **v0 engineering hypothesis** olarak ele aldığınızı
gösteriyor.

### Challenge

İlerleyen aşamalarda özellikle şu varsayımı kanıtlamaya çalışın:

> Problemin temel nedeni gerçekten fiziksel alan yetersizliği değil,
> mevcut alanların doluluk bilgisinin güvenilir ve zamanında
> paylaşılamaması mı?

Bu varsayım projenizin yönünü ciddi biçimde etkileyebilir.

---

## 2. AI → Human → Evidence — Very Strong

`evidence/ai-human-evidence.md` çalışmanız Week 01'in en güçlü
çıktılarından biridir.

AI önerilerini doğrudan kabul etmek yerine:

- **MODIFY**
- **REJECT**
- **ACCEPT**
- **UNCERTAIN**

kararlarının tamamını kullanmış olmanız, AI'yı karar mercii değil
**engineering thought partner** olarak kullandığınızı gösteriyor.

Özellikle sabit QR önerisini güvenlik ve operasyonel nedenlerle
**MODIFY**, tamamen otomatik yoklama önerisini **REJECT** ve turnike
verisiyle doluluk tahminini **UNCERTAIN** olarak değerlendirmeniz
güçlü Human Judgment örnekleridir.

Daha da önemlisi, kararların arkasına **Evidence Needed** eklemişsiniz.

Bu yaklaşımı dönem boyunca koruyun:

> **AI önerir → İnsan değerlendirir → Evidence doğrular veya sorgulatır.**

Unutmayın:

> **AI output ≠ Engineering Evidence**

---

## 3. Incident Diagnosis — Strong Engineering Reasoning

`evidence/incident-diagnosis.md` içinde yalnızca “sistem çalışmadı”
demek yerine üç problemi ayrı ayrı:

**What Happened → Process Gap → Missing Evidence**

mantığıyla incelemeniz başarılıdır.

Özellikle;

- hayalet rezervasyon,
- uzaktan/sahte konum bildirimi,
- pik saatlerde eşzamanlı yük

gibi farklı failure scenario'larını yalnızca kod hatası olarak değil,
mühendislik sürecindeki eksik doğrulama noktaları olarak ele almanız
dersin temel amacıyla uyumludur.

### Important Note

Burada kullandığınız **Threat Modeling, Zero-Trust Verification,
Load/Stress Testing, State Machine** gibi kavramlar ilerleyen haftalarda
daha ayrıntılı mühendislik bağlamlarına oturacaktır.

Şimdilik önemli olan bu kavramları erken “çözüm” olarak sabitlemek değil,
hangi **evidence'ın eksik olduğunu fark etmiş olmanızdır.**

---

## 4. Repository as Engineering Memory — Good Start

Repository yapınız temiz ve anlaşılır:

```text
campus-operations---team-UniPass/
├── README.md
├── docs/
│   └── problem-statement-v0.md
└── evidence/
    ├── incident-diagnosis.md
    └── ai-human-evidence.md
