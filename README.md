# CPalius Version

CPalius CMF sürüm bilgisinin **tek gerçek kaynağı**. Kurulumlar bu repoyu günde
bir kez kontrol eder ve yeni sürüm çıktığında yönetim panelinde bildirir.

Burada kod yoktur — yalnızca sürüm üstverisi ve sürüm notları.

---

## Dosyalar

| Dosya | Kim okur | Amaç |
|---|---|---|
| [`latest.json`](latest.json) | **Kod** | Güncel sürüm işaretçisi. CPalius yalnızca bunu okur. |
| [`versions.json`](versions.json) | **Kod** | Tüm sürümlerin dizini. Yükseltme yolu ve geçmiş için. |
| [`version.md`](version.md) | İnsan | Güncel sürümün özeti ve numaralandırma kuralları. |
| [`releases/<sürüm>.md`](releases/) | İnsan | Her sürümün tam notu: yenilikler, düzeltmeler, kırılmalar. |

### Neden hem `.json` hem `.md`?

Markdown başlığından sürüm numarası ayıklamak kırılgandır — bir başlığı yeniden
yazmak tüm kurulumların güncelleme kontrolünü bozar. `latest.json` sekiz satırdır
ve asla belirsiz değildir. `version.md` ise insanların okuduğu belgedir.

---

## Yeni sürüm yayınlama

Üç dosya değişir, sırası önemlidir:

**1. Sürüm notunu yazın**

`releases/<yeni-sürüm>.md` oluşturun. Şablon: [releases/1.0.0.md](releases/1.0.0.md)

Şu başlıkları taşımalıdır: *Yenilikler* · *Düzeltmeler* · *Kırılmalar (varsa)* ·
*Yükseltme notları (varsa)* · *Bilinen kısıtlar*

**2. `versions.json` dizinine ekleyin**

Yeni girdi **listenin başına** eklenir.

**3. En son `latest.json`'u güncelleyin**

Bu dosya değiştiği anda tüm kurulumlar yeni sürümü görmeye başlar — bu yüzden
**en son** güncellenir. Notlar henüz yayında değilken işaretçiyi ileri almak,
kullanıcıları var olmayan bir sürüm notuna yönlendirir.

```jsonc
{
  "schema": 1,
  "channel": "stable",
  "version": "1.1.0",           // version_compare() uyumlu olmalı
  "released_at": "2026-10-01",
  "critical": false,            // true ise panel uyarıyı kapatılamaz gösterir
  "requires": {
    "php": ">=8.4",
    "upgrade_from": ">=1.0.0"   // bundan eski sürümler önce ara sürüme çıkmalı
  },
  "notes": {
    "url": "https://github.com/CPalius/version/blob/main/releases/1.1.0.md",
    "raw": "https://raw.githubusercontent.com/CPalius/version/main/releases/1.1.0.md"
  },
  "download": {                 // çevrimiçi güncelleme açıldığında doldurulur
    "zip": null,
    "sha256": null
  }
}
```

---

## Sürüm numaralandırma

```
MAJOR . MINOR . PATCH [ . HOTFIX ]
```

- **MAJOR** — geriye dönük uyumsuz değişiklik
- **MINOR** — yeni özellik, uyumlu
- **PATCH** — yalnızca hata düzeltmesi
- **HOTFIX** — yalnızca acil güvenlik yaması; normal sürümlerde yazılmaz

Tüm numaralar PHP `version_compare()` ile sıralanabilir olmalıdır.

---

## Kurulumlar bunu nasıl okur

```
CPalius (cron, günde 1 kez)
  → GET https://raw.githubusercontent.com/CPalius/version/main/latest.json
  → version_compare(latest, kurulu)
  → sonuç cp_settings içine yazılır
  → AACP paneli ve site altbilgisi bu kaydı okur
```

Ağ çağrısı **yalnızca cron sırasında** yapılır. Sayfa isteği hiçbir zaman
GitHub'a bağlanmaz — ağ kesintisi siteyi yavaşlatmaz veya düşürmez.

`download.zip` alanı doldurulduğunda aynı işaretçi çevrimiçi güncelleme için de
kullanılacaktır; `sha256` indirilen arşivin doğrulanması içindir.

---

## Lisans

[LICENSE](LICENSE)
