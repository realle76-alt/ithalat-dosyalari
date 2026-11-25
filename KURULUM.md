# Bağlantı denemesi: kurulum

Amaç: Google girişi ve Drive'a yazmanın üç ortamda çalıştığını görmek. Toplam süre yaklaşık 20-30 dakika. Menü adları Google ve GitHub tarafında küçük farklarla değişebilir, bir adımı bulamazsanız ekran görüntüsü gönderin.

Depo adını `ithalat-dosyalari` seçerseniz adresiniz şu olur:

- Uygulama adresi: `https://realle76-alt.github.io/ithalat-dosyalari/`
- JavaScript kaynağı: `https://realle76-alt.github.io`

Farklı bir ad seçerseniz aşağıdaki adresleri ona göre değiştirin. Sayfanın "Ortam" kutusu doğru değerleri zaten gösterir.

## A. GitHub'a yükleme

1. github.com'da yeni bir depo açın: ad `ithalat-dosyalari`, görünürlük **Public**. (Ücretsiz hesapta GitHub Pages yalnızca herkese açık depoda çalışır. Depoda gizli bilgi yok, yalnızca uygulama kodu var.)
2. "uploading an existing file" bağlantısıyla zip'in içindeki 7 dosyayı sürükleyip bırakın: `index.html`, `config.js`, `manifest.webmanifest`, `apple-touch-icon.png`, `icon-192.png`, `icon-512.png`, `KURULUM.md`. "Commit changes" deyin.
3. Depoda **Settings > Pages** bölümüne girin. "Source" olarak **Deploy from a branch**, dal olarak **main** ve klasör olarak **/ (root)** seçip kaydedin.
4. Bir iki dakika sonra uygulama adresini açın. "Bağlantı denemesi" sayfası gelmeli ve "İstemci kimliği: Eksik" yazmalı. Bu aşamada bu doğru.

## B. Google Cloud ayarları

1. console.cloud.google.com adresinde kendi Google hesabınızla yeni bir proje açın (ad: İthalat Dosyaları). Ücretsizdir, kart bilgisi istenmez.
2. **APIs & Services > Library** içinde "Google Drive API" aratıp **Enable** deyin.
3. **Google Auth Platform** bölümünü açın (eski adıyla OAuth consent screen). İlk kurulumda:
   - Uygulama adı: İthalat Dosyaları
   - Destek e-postası: kendi adresiniz
   - Kullanıcı türü (Audience): **External**
4. **Audience** sayfasında yayın durumu **Testing** kalsın. "Test users" kısmına kendi Gmail adresinizi ve toptancının Gmail adresini ekleyin. Listede olmayan hesaplar giriş yapamaz.
5. **Data Access** sayfasında kapsam olarak yalnızca şunu ekleyin: `https://www.googleapis.com/auth/drive.file`
   Bu kapsam uygulamaya yalnızca kendi oluşturduğu dosyaları gösterir. Drive'daki diğer dosyalara erişim vermez.
6. **Clients > Create client** deyin, tür olarak **Web application** seçin:
   - Authorized JavaScript origins: `https://realle76-alt.github.io`
   - Authorized redirect URIs: `https://realle76-alt.github.io/ithalat-dosyalari/`
   (Sondaki eğik çizgi dahil, harfi harfine aynı olmalı.)
7. Oluşan **Client ID** değerini kopyalayın. "Client secret" değerine ihtiyacımız yok, hiçbir yere yapıştırmayın.
8. GitHub'da `config.js` dosyasını açıp kalem simgesiyle düzenleyin, `BURAYA_CLIENT_ID_YAPISTIRIN` yerine Client ID'yi yapıştırıp kaydedin. Bir iki dakika sonra sayfayı yenileyin: "İstemci kimliği: Tanımlı" yazmalı.

## C. Deneme

Aşağıdaki üç ortamın her birinde 1'den 4'e kadar adımları sırayla çalıştırın. Giriş için **iki yöntemi de** deneyin (biri çalışınca Çıkış deyip diğerini deneyin). Her ortamın sonunda "Günlüğü kopyala" deyip metni bana gönderin.

| Ortam | Nasıl açılır |
|---|---|
| 1. Bilgisayar | Chrome ya da Edge'de uygulama adresi |
| 2. iPhone, Safari sekmesi | Safari'de uygulama adresi |
| 3. iPhone, ana ekran uygulaması | Safari'de Paylaş > Ana Ekrana Ekle, sonra ana ekrandaki simgeden açın |

Girişte "Google bu uygulamayı doğrulamadı" benzeri bir uyarı çıkacak. Test modunda bu beklenen bir durumdur, "Devam" diyerek geçin.

En önemli sonuç 3 numaralı ortamdır. Orada giriş çalışmazsa mimariyi buna göre değiştireceğiz, o yüzden çalışmasa bile günlüğü gönderin.

## Deneme sonrası

Drive'ınızda `İthalat Arşivi / 2026 / DENEME-001 Bağlantı testi` klasörü oluşur. İçindeki dosyaları kontrol ettikten sonra silebilirsiniz.
