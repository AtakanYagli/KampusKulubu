# AI Çalışma Notları

## 1. Yapay zekâ desteği

Bu çalışmada GitHub Copilot kullanıldı. HTML yapısı ve özellikle `etkinlikler.html` dosyasındaki JavaScript kodu incelendi. Değişiklikleri planlarken ve kodun nasıl çalıştığını anlamaya çalışırken Copilot'tan yardım alındı.

### AI çalışma kayıtları

- Birinci istek: `index.html` içindeki `nav` bölümünün satır satır açıklanması ve `href` ile `aria-current` terimlerinin anlatılması.
- İkinci istek: Mevcut `article` yapısı korunarak GitHub Atölyesi etkinliğinin eklenmesi.
- Üçüncü istek: Etkinlikler sayfasına çalışan harf/boşluk araması ve tarih filtresi eklenmesi.
- Öneri değerlendirmesi: Yeni etkinlik kartı eklenirken tarih, saat, başlık ve yer bilgilerinin mevcut `article` yapısıyla uyumlu olup olmadığı kontrol edildi; daha sonra beşinci kartın tarih seçeneğiyle eşleştiği ayrıca doğrulandı.
- Birinci kod açıklaması: `nav`, `href` ve `aria-current` görevleri incelendi.
- İkinci kod açıklaması: `filterEvents`, `matchesText`, `matchesDate`, `card.hidden` ve sonuç sayacının nasıl çalıştığı incelendi.

## 2. Yapılan değişiklikler

- Etkinlikler sayfasına etkinlik aramak için bir arama alanı ve `Ara` butonu eklendi.
- Arama, yalnızca tam kelime eşleşmesine bağlı değil. Girilen harf dizisi etkinlik kartının başlığında, açıklamasında veya yer bilgisinde geçiyorsa kart gösteriliyor.
- Arama kodu Türkçe karakterleri küçük harfe çevirip normalleştiriyor. Böylece büyük-küçük harf farkı aramayı engellemiyor.
- Arama metnindeki birden fazla boşluk tek boşluğa indiriliyor; arama yazılırken de sonuçlar güncelleniyor.
- Etkinlikleri tarihe göre filtrelemek için bir tarih seçme alanı eklendi.
- Tarih seçenekleri kartlardaki `data-date` değerleriyle eşleştiriliyor. Seçilen tarihle eşleşmeyen kartlar gizleniyor.
- Arama ve tarih filtresi birlikte çalışıyor. Bir kartın gösterilmesi için hem arama metniyle hem de seçilen tarihle eşleşmesi gerekiyor.
- Sonuç sayacı güncelleniyor. Hiç eşleşme bulunmazsa kullanıcıya bilgi veriliyor.
- `Temizle` butonu arama metnini ve tarih seçimini sıfırlayıp tüm etkinlikleri yeniden gösteriyor.
- Etkinlik listesi on özgün etkinlik içerecek şekilde tamamlandı.
- Mevcut etkinlik kartlarının ve genel HTML yapısının korunmasına dikkat edildi. Yeni etkinlik kartları aynı `article` yapısında bırakıldı.
- Mevcut kod incelendiğinde yeni bir paket veya kütüphane eklenmediği görüldü. Projede paket yöneticisi dosyası bulunmuyor; JavaScript doğrudan `etkinlikler.html` içinde kullanılıyor ve sayfa yalnızca mevcut `style.css` dosyasını bağlıyor.
- `index.html` ve `hakkimizda.html` dosyalarının mevcut yapısı değiştirilmedi. Bu sayfalarda ana menü bağlantıları ve ortak `style.css` bağlantısı korunuyor.

## 3. Test süreci

### Kod incelenerek doğrulanan davranışlar

- **Arama alanına bir kelime girildiğinde:** `filterEvents`, kartların `textContent` değerinde normalize edilmiş metni `includes` ile arıyor. Bu nedenle başlık, açıklama veya yer bilgisinde eşleşen kartlar gösteriliyor.
- **Arama alanı temizlendiğinde:** Boş arama metni bütün kartlarla eşleşiyor; tarih seçimi de `Tüm tarihler` durumundaysa beş etkinlik yeniden gösteriliyor.
- **Tarih filtresi seçildiğinde:** `change` olayı çalışıyor ve yalnızca `data-date` değeri seçilen tarihle aynı olan kart görünür kalıyor.
- **Arama ve tarih filtresi birlikte kullanıldığında:** `matchesText && matchesDate` koşulu iki filtrenin birlikte çalışmasını sağlıyor.
- **Temizle butonu:** Formu sıfırlıyor, tüm kartları tekrar gösteriyor ve arama alanına odağı geri veriyor.
- **Ana sayfa ve hakkımızda sayfası:** Üç sayfanın menü bağlantıları korunuyor.

### Yapılan teknik kontroller

- `etkinlikler.html` içindeki JavaScript kodu sözdizimi açısından kontrol edildi.
- On etkinlik kartının tarih değerlerinin tarih filtresindeki seçeneklerle eşleştiği kontrol edildi.
- Editör kontrolünde `etkinlikler.html` ve `style.css` için hata bulunmadı.
- Sahte DOM üzerinde arama, çoklu boşluk, `Temizle`, tarih filtresi, birleşik filtre ve boş sonuç senaryoları çalıştırıldı; hepsi başarılı oldu.
- Geçici yerel HTTP sunucusunda `index.html`, `etkinlikler.html` ve `hakkimizda.html` için `200` yanıtı alındı.

### Tarayıcıda henüz doğrulanmayanlar

Tarayıcıda manuel olarak tıklayıp görsel kontrol yapılmadı. Bu nedenle aşağıdaki noktalar gerçek tarayıcı testi değil, kod ve otomatik senaryo testlerinden sonra yapılması gereken kontrollerdir:

- Arama ve `Temizle` butonlarının gerçek tarayıcı görünümündeki davranışı.
- Tarih seçiminin kartları görsel olarak doğru gizlemesi.
- Mobil ekranda filtre alanının taşmadan görünmesi.
- Ana sayfa ve hakkımızda sayfası bağlantılarının tarayıcıda açılması.

Ayrıntılı senaryo sonuçları [TEST_NOTLARI.md](TEST_NOTLARI.md) dosyasına yazıldı.
