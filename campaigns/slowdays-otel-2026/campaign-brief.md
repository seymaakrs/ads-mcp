# slowdays — Otel & Konaklama Meta Ads Kampanyası 2026

## Hesap Bilgileri

| Alan | Değer |
|------|-------|
| **Business ID** | `1503739050741876` |
| **Asset ID (Instagram)** | `948197981703583` |
| **Meta Pixel ID** | `842581988871357` |
| **Landing Page** | `https://slowdaysai.com/sektorel/otel` |
| **İletişim** | hello@slowdaysai.com |

## Kampanya Hedefleri

### Kampanya 1 — Marka Bilinirliği
- **Objective:** Brand Awareness / Reach
- **Format:** Video (Reels öncelikli) + Static
- **Günlük Bütçe:** 200–300 ₺

### Kampanya 2 — Lead Generation (Otel Paketi)
- **Objective:** Lead Generation → `/api/contact` (Instant Form yerine)
- **Conversion Event:** Lead (Pixel + CAPI dedup)
- **Günlük Bütçe:** 500–700 ₺ (tüm ad set'ler toplamı)

## Ad Set Yapısı

### Ad Set 1 — Retargeting: Web Ziyaretçileri
- **Kitle:** Pixel Custom Audience — `/sektorel/otel` ziyaretçileri (30 gün)
- **Bütçe:** 100–150 ₺/gün

### Ad Set 2 — Retargeting: Sosyal Etkileşim
- **Kitle:** Page/Profile engagement (90 gün)
- **Bütçe:** 100 ₺/gün

### Ad Set 3 — Lookalike %1
- **Kitle:** Mevcut müşteri listesi → %1 LAL (TR)
- **Bütçe:** 200 ₺/gün

### Ad Set 4 — Cold: Sektör + Bölge
- **Coğrafya:** Bodrum, Marmaris, Fethiye, Göcek (30km radius)
- **Yaş:** 30–60
- **İlgi:** Otel yönetimi, Turizm işletmeciliği, Küçük işletme sahibi
- **Davranış:** Facebook Page Admin, Small business owners
- **Bütçe:** 200–300 ₺/gün

## UTM Parametreleri

Tüm reklam URL'lerine eklenecek:

```
https://slowdaysai.com/sektorel/otel
  ?utm_source=facebook
  &utm_medium=paid_social
  &utm_campaign=otel-sezon-2026
  &utm_content={{ad.name}}
  &utm_term={{adset.name}}
```

Meta Dynamic parametresi olarak:
```
&fbclid={{fbclid}}
```

## Ad Copy Slotları

### Slot A — Ana Hook (Video/Reels)
```
Hook (0–3 sn):   "Büyük oteller kapandı. Siz öne çıkın."
Body (3–15 sn):  Turistler dijitalde görünür olan oteli buluyor.
CTA (15–25 sn):  "Bu hafta başlayanlara ilk ay %20 indirim →"
```

### Slot B — Static / Carousel
```
Kart 1: "22 Mayıs'tan itibaren turistler Bodrum'a akıyor."
Kart 2: "Dijitalde görünür olan otel, dolu sezona giriyor."
Kart 3: "İlk ay %20 indirim · Sınırlı kontenjan"
Kart 4: CTA → slowdaysai.com/sektorel/otel
```

### Slot C — FOMO / Aciliyet
```
Başlık: "Bu hafta karar ver. Bayram gelince geç."
Alt:    Kurban Bayramı 26 Mayıs. Reklamın etkisi 3–6 hafta.
CTA:    "Ücretsiz görüşme al"
```

## Dönüşüm Takibi

- **Pixel Event:** `Lead` (browser-side via `fbq('track','Lead')`)
- **CAPI Event:** `Lead` (server-side via `/api/meta-capi` + hashed PII)
- **Deduplication:** `eventID` ile browser + server eşleşmesi
- **Attribution:** `fbclid` → `_fbc` cookie (90 gün) + sessionStorage UTM

## Optimizasyon Takvimi

| Gün | Aksiyon |
|-----|---------|
| 1–7 | Learning phase — müdahale etme |
| 7 | En düşük CPL'li ad set'e bütçe kaydır |
| 14 | Kazanan creative → scale up |
| 21 | Lookalike'ı %2'ye genişlet |

## Hedef KPI'lar

| Metrik | Hedef |
|--------|-------|
| CPL (Cost per Lead) | < 500 ₺ |
| CTR | > %1.5 |
| Frequency (awareness) | 2–4x / hafta |
| Lead → Görüşme | > %40 |
