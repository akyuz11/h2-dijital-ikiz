# Güneş–Hidrojen Dijital İkizi (H₂ Üreteç Uzak Deney Seti)

Heliocentris **Dr FuelCell® Professional** deney setinin web tabanlı dijital ikizi.
Zincir: **Işık → PV panel → PEM elektrolizör (H₂/O₂) → gaz depoları → yakıt hücresi → motor + pervane**

🔗 **Canlı uygulama:** https://akyuz11.github.io/h2-dijital-ikiz/

## Hızlı başlangıç
- Tarayıcıda açmak için: yukarıdaki link, ya da `index.html` dosyasına çift tıklayın.
- Kurulum gerekmez. Tek dosyalık HTML/CSS/JS uygulaması (Chart.js CDN üzerinden yüklenir).
- Yerel sunucuyla çalıştırmak isterseniz: `python -m http.server 8000` → http://localhost:8000

## Dosyalar
| Dosya | Açıklama |
|---|---|
| `index.html` | Uygulamanın tamamı (SVG sahne, model, grafikler, TR/EN, açık/koyu tema) |
| `data/deney_verileri.json` | Laboratuvar Excel ölçümleri ve üretici teknik değerleri |
| `H2_Dijital_Ikiz_Tanitim_uyumlu.mp4` | 61 sn tanıtım videosu |
| `docs/Gelistirme_Notlari.md` | Tasarım planı, model açıklaması, geliştirme yazışmaları |

## Model özeti
- **Işık:** 0–8 kademe; kademe 1–8 laboratuvar deney gruplarına (0,5…1,2 A) karşılık gelir.
- **PV:** Tek diyot modeli; elektrolizör I–V eğrisiyle kesişimi ölçülen akımı verecek şekilde kalibre.
- **Elektrolizör:** Isınma geçişli gerilim (≈2,8 V → 2,4 V); H₂ debisi ölçüm tablosundan interpolasyon, Faraday teorik değeriyle karşılaştırma.
- **Yakıt hücresi:** Seri bağlı çift hücre, üretici değerlerine (0,8–1,8 V, ≤1,7 W) kalibre.
- **Motor/pervane:** ≤3 V, ≤130 mA; birinci dereceden atalet.
- Ayrıntılar: uygulamadaki **Model notları** sekmesi ve `docs/Gelistirme_Notlari.md`.

## Bilinen notlar
- 0,5 / 0,8 / 0,9 A gruplarında ölçülen hacim Faraday sınırını aşıyor (%109, %112, %103) — derste tartışma konusu.
- 0,6 A için 20 dk değeri yok; 92 mL interpolasyonla bulundu.
- Adres sonuna `?record` eklenirse video kaydı için kare kare kayıt modu açılır.

## Öğrenciler için: nasıl katkı yaparım?
1. Sağ üstten **Fork** edin (kendi hesabınıza kopya).
2. Kendi kopyanızda değişiklik yapın (`index.html` içinde fizik modeli `model`, metinler `i18n` sözlüğünde).
3. Fork'unuzda **Settings → Pages → Branch: main** ile kendi canlı sürümünüzü yayınlayın.
4. Ana projeye eklenmesini istediğiniz değişiklik için **Pull Request** açın.

### Geliştirme fikirleri
- [ ] İngilizce altyazılı / 30 sn kısa tanıtım videosu
- [ ] Yük direnci seçimi (0,3–100 Ω) ve yakıt hücresi I–V / güç eğrisi deneyi
- [ ] Paralel/seri yakıt hücresi bağlantı seçeneği
- [ ] Gerçek PV paneli (4 hücre, Voc 2,3 V) ile karşılaştırma modu
- [ ] Ölçüm verisinin `data/deney_verileri.json` dosyasından dinamik yüklenmesi
- [ ] Öğrenci deney föyü / quiz modu
