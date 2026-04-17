# ⚙ ClampForce v1.0

Basınçlı tanklar ve boru flanşlarındaki cıvata bağlantılarını **VDI 2230** ve **EN 1591** standartlarına göre analiz eden, tarayıcıda çalışan ön-mühendislik hesap aracı.

> Kurulum yok. İnternet bağlantısı yok. Tek `.html` dosyası — çift tıkla, çalıştır.

---

## 🚀 Kullanım

`ClampForce v1.0.html` dosyasını indirin ve tarayıcıda açın. Hepsi bu.

---

## 🔍 Ne Yapar?

| Kontrol | Açıklama |
|---|---|
| **[1] Gerilme** | σ = F_bolt / A_s ≤ proof / SF |
| **[2] Ayırma** | n × F_pre > SF × F_p |
| **[3] Sızdırmazlık** | p_gasket ≥ p_min (opsiyonel) |
| **[4] Cıvata Aralığı** | Aralık ≥ faktör × d (DESIGN modu) |

---

## ⚡ İki Çalışma Modu

**CHECK** — Mevcut tasarımı doğrula. Cıvata sayısını sen girersin, araç kontrolleri yapar.

**DESIGN** — Yeni tasarım. BCD (Bolt Circle çapı) gir, araç gerekli minimum cıvata sayısını hesaplar.

---

## 📐 Giriş Parametreleri

### Basınç & Geometri
- İç basınç (MPa), conta iç/dış çapı (mm)
- CHECK: cıvata sayısı n — DESIGN: BCD (mm)

### Cıvata
- Boyut: M6 – M20 | Sınıf: 4.6 / 5.8 / 8.8 / 10.9 / 12.9
- Ön yük faktörü k ve preload kayıp faktörü

### Güvenlik Faktörleri
- SF_ayırma (varsayılan 1.5), SF_gerilme (varsayılan 1.2)

### Opsiyonel Modüller (Toggle)
| Modül | Gereksinim | Ekstra Parametreler |
|---|---|---|
| VDI φ Rijitlik | — | E_bolt, E_joint, L_eff |
| Termal Etki | VDI φ açık olmalı | ΔT, L_joint, α_bolt, α_joint |
| Sızdırmazlık | — | Min. conta gerilmesi (MPa) |

---

## 📊 Sonuçlar

Analiz çalıştırıldığında sağ panelde şunlar belirir:

- ✅ / ❌ Genel kabul durumu
- 6 metrik kart: A_eff, F_p, F_pre, F_bolt, rijitlik faktörü, cıvata sayısı
- Her kontrol için OK / NOK rozeti ve detay değerler
- Gerilme kontrolünde görsel doluluk çubuğu (yeşil < 65% · turuncu 65–85% · kırmızı > 85%)

---

## 🔩 Yerleşik Veri Tabanı

| Boyut | A_s (mm²) | | Sınıf | Proof (MPa) | Re (MPa) | Rm (MPa) |
|---|---|---|---|---|---|---|
| M6 | 20.1 | | 4.6 | 225 | 240 | 400 |
| M8 | 36.6 | | 5.8 | 380 | 400 | 500 |
| M10 | 58.0 | | 8.8 | 580 | 640 | 800 |
| M12 | 84.3 | | 10.9 | 830 | 900 | 1000 |
| M14 | 115.0 | | 12.9 | 970 | 1080 | 1200 |
| M16 | 157.0 | | | | | |
| M18 | 192.0 | | | | | |
| M20 | 245.0 | | | | | |

---

## 📋 Detaylı Kullanıcı Kılavuzu

Tam açıklamalar, örnek senaryo ve formüller için `ClampForce v1.0 Kullanıcı Kılavuzu.docx` dosyasına bakın.

---

## ⚠ Sınırlamalar

- Desteklenen aralık: M6–M20, silindirik simetri varsayımı
- Termal analiz yalnızca VDI φ modu aktifken çalışır
- Rijitlik modeli basitleştirilmiş VDI 2230; karmaşık geometriler için FEM önerilir

---

*VDI 2230 · EN 1591 · v1.0*
