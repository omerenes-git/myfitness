# Formda — Antrenman & Kalori (PWA)

Tek dosyalık kişisel uygulama: **hipertrofi antrenman takibi** (mezosiklüs, çift progresyon, RIR rampası, deload) + **kalori defisit takibi** (ölçülen TDEE, trend kilo, projeksiyon, bel çevresi). Veriler yalnızca telefonundaki tarayıcı depolamasında tutulur; hiçbir sunucuya gönderilmez.

---

## Canlı uygulama

Bu depo GitHub Pages üzerinden otomatik yayınlanır (`main` dalına her push'ta `.github/workflows/deploy-pages.yml` iş akışı devreye girer).

1. Depoda **Settings → Pages → Build and deployment → Source** kısmını **GitHub Actions** olarak ayarla (ilk kurulumda tek seferlik).
2. Yayın adresin: `https://<KULLANICI_ADIN>.github.io/myfitness/`
3. Telefonda **Chrome** ile bu adresi aç → menü (⋮) → **"Ana ekrana ekle" / "Uygulamayı yükle"**.

Artık ana ekranda normal bir uygulama gibi: tam ekran açılır, çevrimdışı çalışır.

## Eski Kalori Defisit (v1) verilerini taşıma

Bu uygulama eski **Kalori Defisit (v1)** uygulamasının devamıdır ve verilerini **otomatik taşır** — tek şart dosyaların aynı adreste (aynı GitHub Pages deposu) yayınlanması. Farklı bir adrese taşırsan: eski uygulamada **Ayarlar → Yedeği indir (JSON)**, yeni uygulamada **Ayarlar → Yedekten geri yükle**.

## Güncelleme

Yeni değişiklikler `main` dalına merge edildiğinde iş akışı otomatik yeniden yayınlar. Uygulama açıkken "Yeni sürüm hazır" çubuğu çıkar; **Yenile**'ye dokun. Verilerin her zaman korunur (veriler dosyalarda değil, cihazında durur).

## Veri güvenliği

- **Haftada bir:** Ayarlar → **Yedeği indir (JSON)**. Bu dosya her şeyi içerir (kalori + antrenman + arşivler).
- Telefon değişiminde veya tarayıcı verisi silinirse: **Yedekten geri yükle** ile saniyeler içinde dönersin.
- Eski v1 (Kalori Defisit) JSON yedekleri de içe aktarılabilir — antrenman verilerine dokunmadan yalnızca kalori kısmını değiştirir.
- CSV dışa aktarım (kalori + antrenman ayrı ayrı) Türkçe Excel ile uyumludur (noktalı virgül, virgüllü ondalık).

## Kullanım özeti

**Antrenman:** İlk açılışta "Mezosiklüs kur" → hazır **Üst/Alt ×4 şablonu**nu yükle veya kendi programını gir (egzersiz, set, tekrar aralığı, kilo artışı). İlk hafta kiloları sen belirlersin; sonrasında her set için **kilo × hedef tekrar** uygulamadan gelir:

- Tüm setlerde üst tekrar sınırına ulaştıysan → **kilo artar**, tekrar hedefi alta döner.
- Aralıktaysan → aynı kilo, **+1 tekrar** hedefi.
- Aralığın altındaysan → kilo korunur; "Zor" işaretlediysen hafif düşürülür.
- "Kolay/Zor" geri bildirimi sonraki haftanın **set sayısını** ayarlar (RP tarzı otoregülasyon).
- RIR rampası otomatik (H1: RIR 3 → son hafta: RIR 0), deload haftasında setler yarıya, kilolar ~%90'a iner.

**Kalori:** Sabah kilonu + gün sonunda yediğin kaloriyi gir; açığı ve TDEE'yi uygulama hesaplar. Yeterli veri birikince TDEE formülden değil **kendi tartım/alım verinden ölçülür**. Bel çevresini haftada bir gir — grafikte izlenir.

**Grafikler:** kilo + projeksiyon, egzersiz bazlı tahmini 1RM (Epley), bel çevresi, 28 günlük enerji dengesi.

## Dosyalar

| Dosya | Görev |
|---|---|
| `index.html` | Uygulamanın tamamı (arayüz + motorlar) |
| `sw.js` | Çevrimdışı çalışma + güncelleme (service worker) |
| `manifest.webmanifest` | Uygulama kimliği (ad, ikon, tam ekran) |
| `icon-192.png`, `icon-512.png` | Uygulama ikonları |
| `.github/workflows/deploy-pages.yml` | GitHub Pages otomatik yayın iş akışı |
| `README.md` | Bu rehber |
