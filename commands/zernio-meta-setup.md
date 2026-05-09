---
description: slowdaysai (Zernio) için Meta Ads kampanya workspace'ini kur ve ilk kampanyaları hazırla
---

IMPORTANT: Bu komut slowdaysai ajansının **kendi** Meta Ads kampanyalarını kurmak içindir (müşteri hesabı değil). Pixel ID: `842581988871357`. CAPI endpoint: `https://slowdaysai.com/api/meta-capi`.

Aşağıdaki adımları sırayla çalıştır:

## 1. Bağlantı Kontrolü

`get_connections_status` aracını çağır.
- Bağlantı yoksa kullanıcıya şunu söyle: "`/mcp` çalıştır, Adspirer sunucusunu bul ve Meta Ads hesabını bağla. Sonra `/adspirer:zernio-meta-setup` komutunu tekrar çalıştır."
- Meta Ads bağlıysa 2. adıma geç.

## 2. Workspace Dosyalarını Oku

Proje kökündeki bu dosyaları oku (varsa):
- `META-ADS.md` — marka bağlamı, kitleler, kampanya yapısı, KPI hedefleri
- `STRATEGY.md` — aktif strateji direktifleri
- `BRAND.md` — görsel kimlik ve renk kuralları

Bu dosyalar bulunmazsa kullanıcıyı uyar: "slowdaysai-web reposundan `META-ADS.md` ve `STRATEGY.md` dosyalarını bu klasöre kopyala, sonra komutu tekrar çalıştır."

## 3. Mevcut Meta Verilerini Çek

Bu araçları paralel olarak çağır:
- `get_meta_campaign_performance` (lookback_days: 30)
- `list_campaigns` (platform: meta)
- `get_business_profile`
- `get_benchmark_context`

Hata alınan araçları atla ve kullanıcıya hangi verilerin eksik olduğunu belirt.

## 4. Kampanya Yapısını Onayla

`META-ADS.md` dosyasındaki 3 kampanya katmanını kullanıcıya özetle:

| # | Kampanya | Hedef | Bütçe Oranı |
|---|---|---|---|
| 1 | Farkındalık | Reach/Brand Awareness | %20 |
| 2 | Lead Yakalama | Lead Generation | %50 |
| 3 | Retargeting | Conversions/Messages | %30 |

Kullanıcıya aylık toplam bütçeyi sor (eğer `META-ADS.md`'de belirtilmemişse).

Onay olmadan kampanya oluşturma.

## 5. Kampanyaları Oluştur (Onay Sonrası)

Kullanıcı onayladıktan sonra her kampanya için:

### Kampanya 1 — Farkındalık
```
Objective: BRAND_AWARENESS veya REACH
Status: PAUSED
Budget: toplam_bütçe × 0.20
Ad Sets:
  - Türkiye | 25-55 yaş | Pazarlama, Girişimcilik ilgisi
Ad Formatı: Video (15 sn) + Statik görsel
```

### Kampanya 2 — Lead Yakalama
```
Objective: LEAD_GENERATION
Status: PAUSED
Budget: toplam_bütçe × 0.50
Ad Sets (ayrı ayrı):
  - KOBİ Sahibi: 28-50 yaş, girişimcilik/pazarlama ilgisi
  - Otel/Turizm: 30-55 yaş, otelcilik/turizm ilgisi  
  - Emlak: 32-60 yaş, gayrimenkul/yatırım ilgisi
Ad Formatı: Single Image + Carousel
Lead Form: Ad, Soyad, Telefon, Sektör alanları
```

### Kampanya 3 — Retargeting
```
Objective: CONVERSIONS veya MESSAGES
Status: PAUSED
Budget: toplam_bütçe × 0.30
Ad Sets:
  - Web ziyaretçileri — son 30 gün (Pixel: 842581988871357)
  - Lookalike %1 Türkiye (kaynak: form dolduranlar)
Ad Formatı: Video testimonial + Dynamic
```

Tüm kampanyaları **PAUSED** statüsünde oluştur. Aktif etmeden önce kullanıcıdan tekrar onay al.

## 6. Dönüşüm Takibini Doğrula

Meta Events Manager'da şu event'lerin geldiğini kontrol et:
- `PageView` ✓ (site genelinde)
- `Lead` ✓ (iletişim formu)
- `Contact` (varsa)

CAPI çalışıyor mu kontrol et: `https://slowdaysai.com/api/meta-capi` endpoint'ini test et.

Eksik event varsa kullanıcıya `META-ADS.md > Dönüşüm Takibi` bölümünü işaret et.

## 7. Özet Sun

Kullanıcıya şunları söyle:
- Kaç kampanya oluşturuldu ve toplam bütçe
- Her kampanya için beklenen haftalık lead hedefi
- Sonraki adımlar:
  1. Reklam görsellerini yükle (marka kuralları: `META-ADS.md > Reklam Görseli Kuralları`)
  2. Lead formlarını tamamla
  3. Kampanyaları ACTIVE durumuna al
  4. İlk 7 gün sonunda `/adspirer:performance-review` çalıştır

"Workspace hazır! `META-ADS.md` ve `STRATEGY.md` dosyaları proje klasöründe. Görsel yükleme veya lead form içeriği için `/adspirer:write-ad-copy` komutunu kullanabilirsin."
