# ERP 2026

Medikal cihaz üreticisi için sıfırdan tasarlanan **modüler, yamalanabilir ve API öncelikli** web tabanlı ERP platformu.

> Bu depo bir proje vitrinidir. Kaynak kod ticari olduğu için paylaşılmamaktadır.

## Tasarım hedefleri

- **Modüler çekirdek:** İş modülleri `module.json` manifestiyle tanımlanır. Bağımlılıkları kontrol edilir, çalışırken açılıp kapatılabilir.
- **Yamalanabilirlik:** Müşteriye özel geliştirmeler ayrı bir `custom/` katmanında durur. Çekirdek güncellemeleri bu katmana asla dokunmaz. Yamalar imzalı paketlerle dağıtılır.
- **API öncelikli:** Tüm işlevler sürümlü bir REST API (`/api/v1`) üzerinden sunulur. Arayüz de bu API'yi kullanır.
- **Gözlemlenebilirlik:** Liveness/readiness uçları, kuyruk paneli ve yapılandırılmış loglar.
- **Regülasyon uyumu:** Lot ve seri takibi, izlenebilirlik ve denetim kaydı (audit trail) temel gereksinim olarak ele alındı.

## Mimari

```
frontend/  Vue 3 + TypeScript SPA
   │  REST (Sanctum token)
   ▼
core/      Platform çekirdeği: modül yükleyici, API, yetkilendirme, olaylar
modules/   İş modülleri (her biri module.json ile)
custom/    Müşteri uzantıları (yamalardan etkilenmez)
   │
   ▼
PostgreSQL · Redis · Horizon kuyrukları
```

## Geliştirme süreci

- Gereksinim (SPEC), mimari (ARCHITECTURE) ve karar kayıtları (ADR) dokümanlarıyla yönetilen geliştirme
- Tek komutla Docker geliştirme ortamı (migrasyon ve seed dahil)
- CI betiği: statik analiz, kod biçimi (Pint), birim testleri, frontend kontrolleri
- Playwright ile uçtan uca (E2E) testler

## Teknolojiler

`PHP 8.4` · `Laravel` · `Sanctum` · `Horizon` · `Vue 3` · `TypeScript` · `Vite` · `PostgreSQL` · `Redis` · `Docker` · `nginx` · `Playwright`
