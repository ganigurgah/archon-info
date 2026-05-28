---
marp: true
paginate: true
backgroundColor: #0d1117
color: #e6edf3
style: |
  section {
    font-family: 'Segoe UI', Tahoma, sans-serif;
    padding: 48px 64px;
  }
  h1 { color: #58a6ff; margin-bottom: 0.4em; }
  h2 { color: #79c0ff; }
  h3 { color: #a5d6ff; }
  strong { color: #ffa657; }
  em { color: #8b949e; }
  code {
    background: #1f2937;
    color: #a5f3fc;
    padding: 2px 6px;
    border-radius: 4px;
  }
  table { width: 100%; border-collapse: collapse; font-size: 0.85em; }
  th { background: #1c2a3a !important; color: #79c0ff !important; padding: 10px 14px; }
  td { padding: 8px 14px; border-bottom: 1px solid #30363d; background: #0d1117 !important; color: #e6edf3 !important; }
  tr:nth-child(even) td { background: #0d1a26 !important; }
  blockquote {
    border-left: 4px solid #58a6ff;
    margin: 0;
    padding: 12px 20px;
    background: #0d1a26;
    border-radius: 0 8px 8px 0;
    font-style: italic;
  }
  section.lead {
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
  }
  section.lead h1 { font-size: 2.4em; }
  section.lead p { font-size: 1.2em; color: #8b949e; }
  .stat-big { font-size: 3em; font-weight: 900; color: #58a6ff; }
  ul li { margin-bottom: 0.5em; line-height: 1.6; }
  pre {
    background: #161b22 !important;
    border: 1px solid #30363d;
    border-radius: 8px;
    padding: 16px 20px;
  }
  pre code {
    background: transparent !important;
    color: #c9d1d9 !important;
    padding: 0;
    font-size: 0.78em;
    line-height: 1.8;
  }
  @media print {
    section { background-color: #fff !important; color: #1a1a2e !important; }
    h1 { color: #1a56db !important; }
    h2 { color: #1e429f !important; }
    h3 { color: #1c3d7a !important; }
    strong { color: #b45309 !important; }
    em { color: #4b5563 !important; }
    code { background: #f3f4f6 !important; color: #0e7490 !important; }
    th { background: #dbeafe !important; color: #1e3a8a !important; }
    td { border-bottom: 1px solid #d1d5db !important; }
    tr:nth-child(even) td { background: #f8fafc !important; }
    blockquote { background: #f0f7ff !important; border-left-color: #2563eb !important; color: #1e3a8a !important; }
  }
---

<!-- ═══════════════════════════════════════════════════ -->
<!--                    GİRİŞ                           -->
<!-- ═══════════════════════════════════════════════════ -->

<!-- _class: lead -->

# Herhangi bir geliştiriciye sorun:

## *"Bu projede işler neden böyle çalışıyor?"*

---

<!-- _class: lead -->

# Cevap tek bir kişinin kafasında.

## O kişi yarın ayrılıyor.

---

<!-- _class: lead -->

# **Archon**

### Her projeye, o projeyi bilen bir yapay zeka mimar.

*Kaynak kodunuzu, analiz belgelerinizi ve bakım geçmişinizi öğrenen — tamamen kurumunuzun sunucusunda çalışan AI.*

### **AI'ın en güçlü olduğu yer, kendi bağlamınızla çalıştığı yerdir; genel cevaplar değil.**
---

<!-- ═══════════════════════════════════════════════════ -->
<!--                   ÖRNEKLER                         -->
<!-- ═══════════════════════════════════════════════════ -->

# Mert ile tanışın.

8 yıldır aynı kurumsal fintech projesinde yazılım geliştiriyor.

Ödeme modülünün neden bu mimaride tasarlandığını **tek bilen o**.
Hangi iş kuralının neden o şekilde çalıştığını **tek açıklayan o**.
Yeni geliştiricilerin ilk üç ayında sordukları tüm soruların yanıtı **onun kafasında**.

Bu ay, daha iyi bir teklif aldı. **Ayrılıyor.**

---

# Selin ile tanışın.

Üç ay önce takıma katıldı. İlk görevi: Mert'in yazdığı ödeme modülüne yeni bir mutabakat özelliği eklemek.

Belgeler eksik. Kaynak kod 600.000 satır.

Mert'e ulaşmaya çalışıyor — ama Mert artık başka bir şirkette, başka bir projenin içinde.

Selin'in tek sorusu: **"Bu neden böyle tasarlanmış?"**

*Cevap yok.*

---

# Selin ne yapıyor?

- Kaynak kodu baştan okumaya çalışıyor — **haftalarca**
- Kıdemli geliştiricilerin zamanını alıyor — **onlar da yavaşlıyor**
- Tahmin ederek ilerliyor — **yanlış varsayımlarla**
- Bir yıl sonra, o da ayrılacak — **ve döngü tekrarlanacak**

*Genel yapay zeka araçları bu sorunu çözmüyor.*
*ChatGPT Selin'e cevap verebilir — ama NexaCore'un kodunu tanımıyor.*

---

# Archon olsaydı ne olurdu?

Selin soruyu Archon'a sorar:

> *"ExchangeRateService neden bu şekilde tasarlanmış? FX oranları harici API'den mi geliyor?"*

Archon 8 yıllık kaynak kodu, 120 ADR kaydını ve bakım notlarını çapraz sorgular.

**"ExchangeRateService birincil FX API'yi kullanır; API yanıt vermezse dahili kur tablosuna düşer. Bu fallback stratejisi, 2021'deki regülasyon güncellemesi sonrası eklendi — bkz. ADR-047."**

**Mert hâlâ orada gibi.**

---

# Gerçek bir senaryo: NexaCore · 600K satır Java

PR #512 açıldı — ödeme modülüne batch reconciliation servisi eklendi. **1.400 satır değişiklik.**

Archon NexaCore'un mimari standartlarına ve güvenlik profiline göre inceledi. PR comment'e yazdıkları:

- **[Kritik]** `ReconciliationBatch.process()` içinde exception yutulmuş — mutabakat hatası sessizce geçiyor
- **[Yüksek]** `@Transactional(rollbackFor)` eksik — kısmi yazımda veri tutarsızlığı riski
- **[Orta]** Batch fetch size ayarsız — 50K+ kayıtta `OutOfMemoryError` olası. `ReportBatchService`'teki konfigürasyon buraya da uygulanabilir

*Code reviewer'ın saatlerce okuyacağı şeyi Archon **dakikalar içinde** buldu.*

---

<!-- ═══════════════════════════════════════════════════ -->
<!--                  İSTATİSTİKLER                     -->
<!-- ═══════════════════════════════════════════════════ -->

# Rakamlarla

Selin gibi kaç geliştirici var?

Yazılım sektöründe **ortalama çalışan devir hızı %20'nin üzerinde**.

10 kişilik bir ekipte bu, **her yıl 2 kişinin ayrılması** demek.
Her ayrılan kişiyle birlikte giden bilgi transferi: ortalama **3–4 aylık verimlilik kaybı**.

*Kaynak: LinkedIn Workforce Report · Stack Overflow Developer Survey 2024*

---

# Archon farkı somut olarak ne ifade eder?

| | Archon'suz | Archon ile |
|---|---|---|
| **Code review süresi** | Haftada ~25 adam-saat | **%60 azalır → ~10 adam-saat** |
| **Onboarding süresi** | 2–4 ay | **2–4 hafta** |
| **Bilgi kaybı (kıdemli ayrılması)** | Kritik — yeniden keşif | **Archon'da kalır** |
| **Veri güvenliği** | Bulut araçlara gider | **0 veri dışarı çıkmaz** |

*10 kişilik ekipte yıllık tasarruf: **780+ adam-saat** — bu bir geliştiricinin 4 aylık kapasitesine eşit.*

---

<!-- ═══════════════════════════════════════════════════ -->
<!--                    KAPANIŞ                         -->
<!-- ═══════════════════════════════════════════════════ -->

# Neler tamamlandı — sırada ne var?

```
████████████████████████████░░░░░░░░░░  Q2 2026 — Mevcut
  ✓ On-premise kurulum · RAG + Fine-tuning (QLoRA)
  ✓ Otomatik PR Review (GitHub / GitLab webhook)
  ✓ SDLC faz yönetimi · Multi-tenant mimari
  ✓ Audit log · REST API · Quota yönetimi

████████████████████████████████░░░░░░  Q3 2026
  → IDE Eklentisi: IntelliJ IDEA + VS Code
    Satır bazlı review · Inline öneri · Canlı soru

████████████████████████████████████░░  Q4 2026
  → Kurumsal lisans sistemi · İsteğe bağlı SaaS modu

██████████████████████████████████████  2027
  → Mobil dashboard · Çoklu LLM desteği
```

---

# Geliştiriciler ne diyor?

> *"PR review'larımızda standart ihlallerini zaten tartışmıyoruz artık — Archon bulmuş, yazmış. Biz mimari tartışmaya zaman ayırıyoruz."*
>
> — **Tarık Y.**, Kıdemli Yazılım Mimarı · İstanbul

---

> *"Yeni gelen arkadaşa 'Git Archon'a sor' diyebiliyorum. Sorularının %80'ini kendisi hallediyor. Bu, benim için haftalık 5 saatin geri dönüşü."*
>
> — **Gözde A.**, Tech Lead · Ankara

---

> *"Air-gapped gereksinimlerimiz vardı. Hiçbir bulut aracı masaya oturtulamıyordu. Archon ilk günden çalıştı."*
>
> — **Erdem K.**, Yazılım Müdürü · Savunma Sektörü

---

<!-- _class: lead -->

# Archon'u canlı görün.

### Projenizi anlatın — size özel bir demo hazırlayalım.

**ganigurgah@gmail.com**

*Veri kurumunuzda kalır. Bilgi birikir. Kalite artar.*

⬡ **Archon** · 2026
