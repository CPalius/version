# CPalius CMF — Güncel Sürüm

> **1.0.0** · 2026-09-14 · kanal: `stable`

Bu dosya **insanlar içindir**. CPalius kurulumları sürüm kontrolünü
[`latest.json`](latest.json) üzerinden yapar — sürüm numarasını değiştirirken
**her iki dosyayı da** güncelleyin.

---

## Bu sürümde ne var

İlk kararlı sürüm. Tam liste: [releases/1.0.0.md](releases/1.0.0.md)

**Öne çıkanlar**

- Modül sistemi, rol/yetenek tabanlı yetkilendirme, bildirim ve global arama altyapısı
- 10 modül: Forum, Blog, Pages, Media, Menu, Seo, Roadmap, Whitepaper, Widget, Importer
- Forum: bölüm hiyerarşisi, anket, ek dosya, taslak, konu bölme/birleştirme, ban/susturma, izin matrisi
- Importer: WordPress, Joomla, MyBB, XenForo ve CSV içe aktarımı
- Seo: JSON-LD şema grafiği, kaynak bazlı sitemap
- Çok dilli içerik ve arayüz
- AACP yönetim paneli, `cp:doctor` tanılama komutu
- Sürüm etiketli güncelleme kancaları

---

## Sürüm geçmişi

| Sürüm | Tarih | Kanal | Notlar |
|---|---|---|---|
| 1.0.0 | 2026-09-14 | stable | [releases/1.0.0.md](releases/1.0.0.md) |

---

## Sürüm numaralandırma

```
MAJOR . MINOR . PATCH [ . HOTFIX ]
  1   .   2   .   3   .    1
```

| Segment | Ne zaman artar |
|---|---|
| **MAJOR** | Geriye dönük uyumsuz değişiklik — modül API'si kırılır, elle müdahale gerektiren şema değişikliği olur |
| **MINOR** | Yeni özellik, geriye dönük uyumlu |
| **PATCH** | Yalnızca hata düzeltmesi |
| **HOTFIX** | Yalnızca acil güvenlik yaması. Normal sürümlerde yazılmaz (`1.2.3`, `1.2.3.0` değil) |

Tüm numaralar PHP `version_compare()` ile karşılaştırılabilir olmalıdır —
güncelleme kancaları sürümleri bu fonksiyonla sıralar.
