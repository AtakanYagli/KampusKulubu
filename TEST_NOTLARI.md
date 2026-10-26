# Test Notları

## Amaç

Bu notlar, etkinlikler sayfasındaki arama ve tarih filtreleme özelliklerinin yanı sıra üç sayfalı sitenin temel erişimini kontrol etmek için hazırlandı. Testler kodu inceleyerek ve JavaScript'i sahte bir DOM üzerinde çalıştırarak yapıldı.

## Kod tabanlı senaryo testleri

| Senaryo | Kontrol | Sonuç |
| --- | --- | --- |
| Arama alanına kelime girme | `bilgisayar laboratuvarı` aramasıyla yer bilgisi bulunan dört etkinlik kontrol edildi. | Başarılı |
| Harf ve boşluk işleme | Birden fazla boşluk içeren arama metni normalize edilerek eşleşme kontrol edildi. | Başarılı |
| Arama alanını temizleme | `Temizle` butonu çalıştırıldı; arama ve tarih seçimi sıfırlandı, on kart yeniden görünür oldu. | Başarılı |
| Tarih filtresi | `03-aralik` seçildiğinde yalnızca GitHub Atölyesi kartının görünür kaldığı kontrol edildi. | Başarılı |
| Arama ve tarih filtresini birlikte kullanma | 3 Aralık filtresi açıkken `github` araması yapıldı; tek eşleşme korundu. | Başarılı |
| Boş sonuç | Eşleşmeyecek bir arama metni girildiğinde kart sayısı sıfırlandı ve boş sonuç mesajı oluştu. | Başarılı |
| Etkinlik ve tarih sayısı | On `article` kartı ile on tarih seçeneğinin eşleştiği kontrol edildi. | Başarılı |

## Teknik kontroller

- `etkinlikler.html` JavaScript kodu sözdizimi açısından kontrol edildi.
- `etkinlikler.html` ve `style.css` editör hata kontrolünden geçirildi; hata bulunmadı.
- JavaScript, sahte DOM üzerinde çalıştırıldı. Bu test gerçek tarayıcı açmadığı için DOM olaylarının kod mantığı ve sonuçları kontrol edildi.
- Geçici yerel HTTP sunucusu kullanılarak aşağıdaki sayfalardan `200` yanıtı alındı:
  - `index.html`
  - `etkinlikler.html`
  - `hakkimizda.html`

## Rubrik kontrolü

- Üç HTML sayfası mevcut ve menü bağlantıları korunuyor.
- Etkinlikler sayfasında on özgün etkinlik kartı bulunuyor.
- Arama alanı, `Ara` ve `Temizle` butonları, sonuç sayacı ve boş sonuç mesajı bulunuyor.
- Tarih filtresi on etkinliğin tarihiyle eşleşiyor.
- Ortak CSS yapısı korunuyor ve filtre alanı küçük ekranlarda satır kırabiliyor.
- Yeni paket veya kütüphane eklenmedi; JavaScript sayfanın içinde ve mevcut dosya yapısı kullanılıyor.

## Tarayıcıda yapılması gereken manuel kontroller

Aşağıdaki kontroller bu çalışma sırasında gerçek tarayıcıda yapılmadı ve başarılıymış gibi yazılmamalıdır:

- Arama, tarih ve `Temizle` kontrollerinin görsel olarak doğru çalışması.
- Arama sonuçlarının kartları ekranda doğru biçimde gizleyip göstermesi.
- Mobil görünümde filtre alanının taşmaması ve butonların kullanılabilir olması.
- Menüden ana sayfa ve hakkımızda sayfasına tıklayarak geçiş yapılması.

Bu kontroller için yerel sunucu çalıştırılıp `etkinlikler.html` tarayıcıda açılmalı; arama, tarih ve temizleme senaryoları gözle denenmelidir.
