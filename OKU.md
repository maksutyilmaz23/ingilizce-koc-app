# İngilizce Koç — APK Otomatik Derleme Projesi

## Bu zip ne içeriyor?
"ingilizce-koc.html" dosyan zaten `app/src/main/assets/index.html` olarak
projeye gömüldü. Ekstra bir dosya kopyalamana gerek yok.

## Önemli: Mikrofon izni
Bu uygulama sesli konuşma modu (SpeechRecognition) kullandığı için:
- `AndroidManifest.xml`'e `RECORD_AUDIO` izni eklendi
- `MainActivity.kt`'ye WebView'in mikrofon iznini otomatik onaylaması için kod eklendi
- Uygulama ilk açıldığında Android sistem izni (mikrofon) kullanıcıya sorulacak

Not: Gemini API çağrıları (`fetch`) ve `localStorage` kullanımı normal WebView
ayarlarıyla (JavaScript + DOM Storage açık) sorunsuz çalışır, ekstra ayar gerekmiyor.

## Kurulum adımları

1. **(Atla)** — HTML zaten gömülü.

2. **Uygulama adını değiştir (isteğe bağlı)**
   `app/src/main/res/values/strings.xml` içindeki `app_name` değerini değiştir (şu an: "İngilizce Koç").

3. **İkon değiştir (isteğe bağlı)**
   `app/src/main/res/mipmap-hdpi/ic_launcher.png` dosyasının üzerine kendi 192x192 ikonunu koy.

4. **GitHub'a yükle**
   - GitHub'da yeni bir repo oluştur (public veya private, farketmez)
   - Bu klasördeki tüm dosyaları o repoya push et:
     ```
     git init
     git add .
     git commit -m "ilk commit"
     git branch -M main
     git remote add origin https://github.com/KULLANICI_ADIN/REPO_ADIN.git
     git push -u origin main
     ```

5. **APK'yı indir**
   - GitHub reponda **Actions** sekmesine git
   - "Build APK" workflow'unun tamamlanmasını bekle (yaklaşık 2-3 dakika)
   - Tamamlanan workflow'a tıkla, en altta **Artifacts** bölümünden
     `app-debug-apk` dosyasını indir — içinde `app-debug.apk` var.
   - Bu APK'yı telefonuna kopyalayıp kurabilirsin (bilinmeyen kaynaklara izin vermen gerekebilir).

## Notlar
- Bu şablon **debug APK** üretir (imzasız, test amaçlı — kendi telefonuna kurmak için sorun değil).
- Play Store'a yüklemek istersen "release" imzalı APK/AAB gerekir, bu ayrı bir adım — istersen onu da ekleyebilirim.
- HTML dosyan kamera, dosya sistemi, konum gibi izinler istiyorsa `AndroidManifest.xml`
  içine ilgili `<uses-permission>` satırlarını eklemen gerekebilir.
- Paket adını (`com.mesut.webviewapp`) değiştirmek istersen hem `app/build.gradle`
  içindeki `applicationId` ve `namespace`, hem de klasör yapısını
  (`app/src/main/java/com/mesut/webviewapp/`) güncellemen gerekir.
