# AI Çalışma Notları

## 1. Yapay zekâ desteği

Bu çalışmada GitHub Copilot kullanıldı. HTML yapısı ve özellikle `etkinlikler.html` dosyasındaki JavaScript kodu incelendi. Değişiklikleri planlarken ve kodun nasıl çalıştığını anlamaya çalışırken Copilot'tan yardım alındı.

## 2. Yapılan değişiklikler

- Etkinlikler sayfasına etkinlik aramak için bir arama alanı ve `Ara` butonu eklendi.
- Arama, yalnızca tam kelime eşleşmesine bağlı değil. Girilen harf dizisi etkinlik kartının başlığında, açıklamasında veya yer bilgisinde geçiyorsa kart gösteriliyor.
- Arama kodu Türkçe karakterleri küçük harfe çevirip normalleştiriyor. Böylece büyük-küçük harf farkı aramayı engellemiyor.
- Etkinlikleri tarihe göre filtrelemek için bir tarih seçme alanı eklendi.
- Tarih seçenekleri kartlardaki `data-date` değerleriyle eşleştiriliyor. Seçilen tarihle eşleşmeyen kartlar gizleniyor.
- Arama ve tarih filtresi birlikte çalışıyor. Bir kartın gösterilmesi için hem arama metniyle hem de seçilen tarihle eşleşmesi gerekiyor.
- Sonuç sayısı güncelleniyor. Hiç eşleşme bulunmazsa kullanıcıya bilgi veriliyor.
- Mevcut etkinlik kartlarının ve genel HTML yapısının korunmasına dikkat edildi. Yeni etkinlik kartları aynı `article` yapısında bırakıldı.
- Mevcut kod incelendiğinde yeni bir paket veya kütüphane eklenmediği görüldü. Projede paket yöneticisi dosyası bulunmuyor; JavaScript doğrudan `etkinlikler.html` içinde kullanılıyor ve sayfa yalnızca mevcut `style.css` dosyasını bağlıyor.
- `index.html` ve `hakkimizda.html` dosyalarının mevcut yapısı değiştirilmedi. Bu sayfalarda ana menü bağlantıları ve ortak `style.css` bağlantısı korunuyor.

## 3. Test süreci

### Kod incelenerek kontrol edilen davranışlar

- **Arama alanına bir kelime girildiğinde:** Form gönderildiğinde `filterEvents` çalışıyor. Girilen metin, her `article` kartının `textContent` değeri içinde `includes` ile aranıyor. Eşleşen etkinliklerin görünür kalması bekleniyor.
- **Arama alanı temizlendiğinde:** Arama metni boş oluyor. Boş metin her metnin içinde bulunduğu için, seçili bir tarih yoksa dört etkinliğin yeniden görünmesi bekleniyor.
- **Tarih filtresi seçildiğinde:** `change` olayı `filterEvents` fonksiyonunu çalıştırıyor. Kartın `data-date` değeri seçilen değerle aynıysa kart gösteriliyor, değilse gizleniyor.
- **Arama ve tarih filtresi birlikte kullanıldığında:** Kod `matchesText && matchesDate` koşulunu kullanıyor. Bu nedenle yalnızca iki koşulu da sağlayan etkinlikler gösteriliyor.
- **Ana sayfa ve hakkımızda sayfası:** Etkinlik sayfasındaki menüde `index.html` ve `hakkimizda.html` bağlantıları hâlâ bulunuyor. Bu dosyaların mevcut HTML yapısı korunuyor.

### Yapılan teknik kontroller

- `etkinlikler.html` içindeki JavaScript kodu sözdizimi açısından kontrol edildi.
- Dört etkinlik kartının tarih değerlerinin tarih filtresindeki seçeneklerle eşleştiği kontrol edildi.
- Editör kontrolünde `etkinlikler.html` ve `style.css` için hata bulunmadı.

### Tarayıcıda henüz doğrulanmayanlar

Bu çalışma sırasında tarayıcıda tıklayarak manuel test yapılmadı. Bu nedenle aşağıdaki davranışlar kod incelenerek beklenen sonuç olarak yazılmıştır; tarayıcıda gerçekten doğrulanmış test sonucu değildir:

- Arama butonuna tıklanınca kartların ekranda doğru biçimde gizlenip gösterilmesi.
- Arama alanının temizlenmesinden sonra kartların görsel olarak yeniden görünmesi.
- Tarih seçiminin tarayıcıdaki gerçek görünümü ve kartların doğru gizlenmesi.
- Arama ve tarih filtresinin aynı anda kullanıldığında ekrandaki sonucu.
- Ana sayfa ve hakkımızda sayfası bağlantılarının tarayıcıda açılması.

Tarayıcı doğrulaması yapmak için `etkinlikler.html` dosyası açılmalı; bir arama metni girilip `Ara` butonuna basılmalı, ardından farklı tarihler seçilmeli ve sonuçlar gözle kontrol edilmelidir. Sonrasında menüdeki `Ana Sayfa` ve `Hakkımızda` bağlantıları denenmelidir.
