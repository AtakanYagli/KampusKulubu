# Kampüs Kulübü — Üç sayfalık statik site

BPR201 - İnternet Tabanlı Programlama
Dr. Öğr. Üyesi Serkan AKSU
http://www.serkanaksu.net
aksu@bartin.edu.tr

## İlk kez çalıştırma
1. GitHub hesabında `kampus-kulubu` adlı repository oluştur. Add README seçeneğini aç.
2. ZIP'i aç. `index.html`, `etkinlikler.html`, `hakkimizda.html`, `style.css` ve `README.md` dosyalarını repository köküne yükle (Add file / Upload files). ZIP dosyasının kendisini yükleme.
3. Commit changes ile kaydet.
4. Code / Codespaces / Create codespace on main seç. Kurulumun bitmesini bekle.
5. Terminal / New Terminal aç. Aşağıdaki komutu çalıştır:

```bash
python3 -m http.server 8000 --bind 0.0.0.0
```

6. Ports panelinde 8000 portunu bul. Gerekirse Forward a Port ile 8000 ekle. Open in Browser seç. Port Private kalabilir.
7. Ana Sayfa, Etkinlikler ve Hakkımızda bağlantılarını dene.
8. HTML/CSS değişikliğinden sonra dosyayı kaydet (Ctrl+S veya Mac'te Cmd+S), browser sayfasını yenile.

Codespaces varsayılan ortamında Python bulunur. `python3 --version` ile kontrol et. Bu projede npm, framework, database veya uygulama kurulumu gerekmez. Python yalnızca hazır dosyaları sunar. Yerel bilgisayarda HTML dosyalarını çift tıklayarak da açabilirsin.

## Dosyalar
- index.html: Ana Sayfa
- etkinlikler.html: Üç örnek etkinlik
- hakkimizda.html: Proje tanıtımı
- style.css: Ortak renkler, sayfa düzeni ve mobil görünüm

## Copilot alıştırması
Önce dosyayı aç. Chat içinde şunu sor:

> HTML öğrenmeye yeni başladım. index.html içindeki nav bölümünü satır satır Türkçe açıkla. Kodu değiştirme. href ve aria-current terimlerinin görevini anlat.

Sonra şu küçük değişikliği iste:

> Yalnızca etkinlikler.html dosyasına mevcut article yapısını kullanarak bir GitHub Atölyesi ekle. Tarihi 3 Aralık, saati 14.00 ve yeri Bilgisayar Laboratuvarı olsun. Yeni paket veya JavaScript ekleme. Değişen satırları açıkla.

Öneriyi oku. Dört etkinliğin göründüğünü ve diğer sayfaların açıldığını kontrol et. AI_NOTLARI.md dosyasına hangi yardımı aldığını ve nasıl test ettiğini yaz. Copilot erişimin yoksa bir article bloğunu kendin çoğalt.

## Kaydet ve GitHub'a gönder
Source Control bölümünde diff'i incele. İlgili dosyaları + ile stage et. Anlamlı mesajla Commit yap. Ardından Sync Changes veya Push seç. GitHub repository sayfasında yeni commit'i doğrula.

## Dersi bitirme
Terminalde Ctrl+C ile web server'ı durdur. https://github.com/codespaces sayfasında ortamın ... menüsünden Stop codespace seç. Sekmeyi kapatmak yeterli değildir. Stop depolamayı silmez. Delete öncesinde dosyaların GitHub'a push edildiğini kontrol et.

## Sık sorunlar
- Directory listing: index.html yanlış klasörde. Dosyaları repository köküne taşı veya doğru klasörde server'ı başlat.
- Address already in use: Önce çalışan server'ı Ctrl+C ile kapat. Gerekirse 8001 kullan ve Ports'ta 8001 aç.
- CSS görünmüyor: Dosya adı style.css ve link yolu aynı olmalı. Büyük/küçük harfe dikkat et.
- Copilot yanıt vermiyor: Hesabı, planı ve kotayı kontrol et. Proje AI olmadan da çalışır.

## Kaynaklar
https://github.com/signup
https://github.com/settings/education/benefits
https://docs.github.com/en/codespaces/quickstart
https://docs.github.com/en/codespaces/reference/using-github-copilot-in-github-codespaces

Bu proje eğitim örneğidir. Tarihler ve etkinlikler kurgudur. Kullanıcı girişi, form gönderimi ve database içermez.
