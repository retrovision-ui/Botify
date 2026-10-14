<p align="center">
  <img src="https://github.com/retrovision-ui/Botify/blob/main/assets/luve1.png" alt="Botify — API Marketplace" width="250">
</p>

<h1 align="center">Botify</h1>
<p align="center"><strong>API Pazarı</strong></p>
<p align="center"><em>Daha fazlasını keşfet. Daha hızlı entegre et.</em></p>

<p align="center">
  <a href="https://viosrio.serv00.net/public/">
    <img src="https://img.shields.io/badge/Canl%C4%B1_Site-%C4%B0ncele-ff2d72?style=for-the-badge" alt="Canlı site">
  </a>
  <a href="https://github.com/retrovision-ui/Botify/">
    <img src="https://img.shields.io/badge/S%C3%BCr%C3%BCm-V8.0-8b5cf6?style=for-the-badge" alt="Sürüm 8.0">
  </a>
  <img src="https://img.shields.io/badge/Altyap%C4%B1-PHP%20%7C%20MySQL-7c3aed?style=for-the-badge" alt="PHP ve MySQL">
</p>

---

## Botify Nedir?

Botify, API'lerin keşfedilmesini, yayımlanmasını, değerlendirilmesini ve kullanılmasını tek bir platformda bir araya getirmeyi amaçlayan bir API pazarı projesidir.

Geliştiriciler API'lerini listeleyebilir; kullanıcılar kategoriler ve arama üzerinden ihtiyaçlarına uygun servisleri keşfedebilir. Satın alma, API anahtarı yönetimi ve kullanım takibi gibi iş akışları, platformun mevcut özellikleri kapsamında sunulur.

Kısacası: Her entegrasyon için ayrı bir dijital dedektiflik bürosu açmak zorunda kalmadan, API dünyasında daha düzenli hareket etmek için tasarlanmıştır.

## Neden Botify?

### Platform bağımlılığına karşı küçük bir özgürlük bildirgesi

Her servis başka bir panelde, her API başka bir belgede, her entegrasyon başka bir sürprizde... Dijital dünyada ürün geliştirmek bazen yazılım yazmaktan çok engelli parkurda yarışmaya benzer.

Botify, API keşfi ve entegrasyon süreçlerini daha anlaşılır bir akışta toplamayı hedefler. Amaç, geliştiricinin vaktini karmaşık süreçlere değil, gerçekten geliştirmek istediği ürüne ayırabilmesidir.

### Teknik engeller mi? Hepsini sihirli değnekle yok ettiğimizi söylemeyeceğiz.

Botify, API'leri keşfetmek ve yayımlamak için ortak bir alan sunar. Bununla birlikte, bir servisin kendi kimlik doğrulaması, kullanım sınırları, ücretleri ve teknik gereksinimleri olabilir. Platform işleri kolaylaştırabilir; ancak kötü belgelenmiş bir API ile aranızdaki diplomatik krizi her zaman tek başına çözemez.

### Bir pazar yeri, tek bir bakış açısı değil

API sağlayıcıları servislerini tanıtabilir; kullanıcılar ise açıklama, kategori, fiyat ve değerlendirmeler üzerinden seçenekleri inceleyebilir. Platformun hedefi, servisleri görünür kılarken keşif ve kullanım sürecini daha düzenli hale getirmektir.

## Öne Çıkan Özellikler

- **API pazarı:** Yayımlanmış API'leri listeleme, arama ve kategoriye göre keşfetme.
- **Sıralama ve değerlendirmeler:** Mevcut sıralama seçenekleri ve kullanıcı puanlarıyla servisleri inceleme.
- **Kullanıcı hesabı:** Kayıt, giriş, profil ve hesap ayarları.
- **API yayımlama ve yönetimi:** API bilgilerini platformda sunmaya yönelik iş akışları.
- **Satın alma ve kullanım akışları:** Projede bulunan satın alma, satın alınan API'ler ve kullanım takibi ekranları.
- **Harici API çağrısı:** API anahtarıyla çalışan `api/v1/invoke.php` uç noktası.
- **Kullanım ve hız sınırı kontrolleri:** API çağrılarında kullanım kaydı ve hız sınırı mekanizmaları.
- **Mesajlaşma ve bildirim ayarları:** Kaynak kodda bulunan ilgili kullanıcı özellikleri.
- **Yönetici alanı:** Yönetim, raporlama ve güvenlik kontrolleri için ayrı yönetici arayüzü.
- **Ödeme sağlayıcısı ayarları:** Stripe, PayPal, Shopify ve Shopier için sağlayıcı bilgilerini yapılandırmaya yönelik alanlar.

Özelliklerin kullanılabilirliği yapılandırmaya, veritabanı şemasına ve ilgili dış servislerin etkinleştirilmesine bağlı olabilir. Ödeme sağlayıcılarının listelenmesi, tüm sağlayıcılar için otomatik OAuth veya canlı ödeme işlemlerinin kurulu olduğu anlamına gelmez.

## Teknoloji Altyapısı

- PHP 8.1 veya üzeri önerilir.
- MySQL uyumlu veritabanı.
- PDO ve PDO MySQL sürücüsü.
- HTML, CSS ve JavaScript.
- PHP oturumları ve sunucu taraflı veritabanı işlemleri.

Harici servisler için SMTP, ödeme sağlayıcısı bilgileri ve ilgili API kimlik bilgileri ayrıca yapılandırılmalıdır. Sunucu gereksinimleri, etkinleştirilen özelliklere göre değişebilir.

## Kurulum

Aşağıdaki adımlar, projeyi kendi sunucusunda kurmak isteyenler için genel kurulum akışıdır. Canlıya geçmeden önce mutlaka temiz bir test ortamında doğrulayın.

### 1. Projeyi indirin

Depoyu Git ile klonlayın:

```bash
git clone https://github.com/retrovision-ui/Botify.git
cd Botify
```

Alternatif olarak GitHub sayfasından kaynak kod arşivini indirebilirsiniz.

### 2. Sunucu ortamını hazırlayın

PHP 8.1 veya üzeri, MySQL uyumlu bir veritabanı ve PDO MySQL sürücüsü bulunan bir barındırma ortamı hazırlayın. Kullanılan özelliklere göre cURL ve SMTP bağlantısı gibi ek gereksinimler de olabilir.

### 3. Dosyaları sunucuya yükleyin

Arşivdeki `public_html` dizininin **içeriğini**, alan adınızın web kök dizinine yükleyin. Barındırma sağlayıcınız farklı bir belge kökü kullanıyorsa, dosyaları o yapıya göre yerleştirin.

`app/` dizini ve veritabanı yapılandırması doğrudan internetten erişilebilir bir konumda bırakılmamalıdır. Mevcut `.htaccess` kurallarını tek başına yeterli güvenlik önlemi kabul etmeyin; barındırma ortamınızın erişim kurallarını da kontrol edin.

### 4. Veritabanını oluşturun

Barındırma panelinizden yeni bir MySQL veritabanı ve ona erişebilen ayrı bir kullanıcı oluşturun. Mümkün olan en düşük veritabanı izinlerini verin.

Projede `m6754_pluss.sql` isimli bir SQL dökümü yer almaktadır. Bu dosya örnek kurulum için doğrudan kullanılmadan önce dikkatle incelenmelidir: geliştirme veya canlı ortamdan alınmış kullanıcı kayıtları, hash'ler, API bilgileri ya da başka özel veriler içerebilir. **Depoda bulunan dökümü olduğu gibi içe aktarmayın.** Temiz ve güvenli bir kurulum dökümü hazırlayın veya proje şemasını inceleyerek yeni bir veritabanı oluşturun.

### 5. Yapılandırmayı ayarlayın

`app/config.example.php` ve `app/config.php` dosyalarını inceleyin. Veritabanı bağlantısı, uygulama adresi, oturum adı, SMTP ve şifreleme anahtarı gibi ayarları kendi ortamınıza göre düzenleyin.

Güvenli kurulum için:

- Gerçek sırları Git deposuna koymayın.
- Üretim ayarlarını sürüm kontrolü dışında tutun.
- `config.example.php` dosyasında yalnızca örnek veya boş değerler bulundurun.
- Veritabanı parolasını, SMTP parolasını ve şifreleme anahtarını kaynak kodda yayımlamayın.
- Daha önce paylaşılmış gerçek bilgileri yalnızca dosyadan silmekle yetinmeyin; ilgili servislerden yenileyin.
- Şifreleme anahtarını güvenli bir yerde yedekleyin. Bu anahtarla şifrelenmiş veriler varsa anahtarı değiştirmek, eski verilerin çözülememesine neden olabilir.

Örnek yapılandırma değerleri:

```php
define('APP_NAME', 'Botify');
define('APP_URL', 'https://example.com');
define('DB_HOST', 'localhost');
define('DB_NAME', 'your_database');
define('DB_USER', 'your_database_user');
define('DB_PASS', 'replace_with_a_secret');
define('DB_CHARSET', 'utf8mb4');
```

Bu örnek, tüm yapılandırma dosyasının yerine geçmez. Projenin ihtiyaç duyduğu diğer sabitleri de güvenli şekilde tanımlayın.

### 6. E-posta ve dış servisleri yapılandırın

Şifre sıfırlama ve yönetici doğrulaması gibi e-posta kullanan özellikler için SMTP ayarlarını yapılandırın. Ödeme sağlayıcıları veya başka harici servisler kullanılacaksa, her birinin resmî panelinden gerekli kimlik bilgilerini edinin ve bunları sunucu tarafında saklayın.

Sağlayıcı ayarlarının arayüzde bulunması, sağlayıcıyla gerçek bir OAuth bağlantısının veya canlı ödeme işleminin otomatik olarak tamamlandığını garanti etmez. Canlı kullanımdan önce her sağlayıcının bağlantısını ayrı ayrı test edin.

### 7. İlk çalıştırmayı test edin

Kurulum tamamlandıktan sonra şu kontrolleri yapın:

1. Ana sayfanın açıldığını doğrulayın.
2. Kayıt ve giriş akışlarını test edin.
3. Veritabanı bağlantısını ve gerekli tabloları kontrol edin.
4. API listeleme, arama ve kategori filtrelerini deneyin.
5. API yayımlama ve API anahtarıyla çağrı akışlarını test ortamında doğrulayın.
6. E-posta, ödeme ve yönetici özelliklerini ayrı ayrı test edin.
7. PHP hata günlüklerini ve sunucu erişim kayıtlarını inceleyin.

Canlıya geçmeden önce yedek alın, test hesaplarını ve örnek sırları kaldırın, hata gösterimini üretim ortamında kapatın ve erişim izinlerini gözden geçirin.

## API Anahtarıyla Çağrı

Projede harici API çağrıları için `api/v1/invoke.php` uç noktası bulunur. Kaynak koda göre API anahtarı `Authorization: Bearer ...` başlığıyla veya `X-API-Key` başlığıyla gönderilebilir.

Örnek istek biçimi:

```bash
curl -X GET "https://example.com/api/v1/invoke.php?param=value" \
  -H "Authorization: Bearer YOUR_BOTIFY_API_KEY"
```

`YOUR_BOTIFY_API_KEY` yerine kendi hesabınızdan alınmış geçerli anahtarı kullanın. Gerçek anahtarları kaynak koda, ekran görüntülerine, herkese açık hata kayıtlarına veya Git commit geçmişine eklemeyin. Uç noktanın çalışması, ilgili API'nin geçerli bir üst uç adresine ve uygun yapılandırmaya sahip olmasına bağlıdır.

## Proje Yapısı

```text
public_html/
├── public/        # Kullanıcı arayüzü ve sayfalar
├── app/           # Yapılandırma, veritabanı, kimlik doğrulama ve yardımcı işlevler
├── api/
│   ├── v1/        # API uç noktaları
│   └── middleware/ # Kimlik doğrulama, hız sınırı ve üst uç yardımcıları
├── assets/
│   ├── CSS/       # Stil dosyaları
│   └── JS/        # İstemci tarafı JavaScript
├── migrations/    # Veritabanı geçişleri için dizin
└── storage/       # Önbellek ve çalışma zamanı dosyaları
```

Dosya ve dizinlerin içeriği sürüme göre değişebilir. Bu görünüm, mevcut V8 kaynak arşivinin genel yapısını özetler.

## Güvenlik

Botify'yi internete açık bir ortamda çalıştırırken:

- Üretim sırlarını GitHub'a yüklemeyin.
- Gerçek veritabanı dökümlerini ve kullanıcı verilerini depodan çıkarın.
- Veritabanı kullanıcısına yalnızca gerekli izinleri verin.
- HTTPS kullanın ve oturum çerezlerini üretim ortamında güvenli yapılandırın.
- Yönetici hesabını ve çok faktörlü doğrulamayı dikkatle yapılandırın.
- Yedekleri erişimi kısıtlanmış bir yerde saklayın.
- Günlüklerde API anahtarı, parola veya hassas müşteri verisi tutulmadığını kontrol edin.
- Canlıya geçmeden önce kimlik doğrulama, erişim denetimi, hız sınırı ve dış URL doğrulama davranışlarını test edin.

Kaynak arşivinde gerçek erişim bilgileri bulunmuşsa, bunların herkese açık depodan kaldırılması yeterli değildir. İlgili parolaları ve anahtarları yenileyin; gerekirse eski Git geçmişindeki hassas verileri de temizleyin.

## Sık Sorulan Sorular

### Botify tüm API sağlayıcılarının yerine mi geçer?

Hayır. Botify bir keşif ve entegrasyon katmanı sunmayı amaçlar. Harici API'lerin kendi koşulları, limitleri, fiyatları ve kimlik doğrulama gereksinimleri devam eder.

### Kurulum için ileri düzey yazılım bilgisi gerekir mi?

Temel PHP barındırma, veritabanı ve yapılandırma bilgisi gerekir. Kurulum adımları takip edilebilir olsa da üretim ortamına geçmeden önce teknik kontrollerin yapılması önemlidir.

### Ödeme sistemleri kurulumla birlikte hazır mı?

Hayır, bunu varsaymayın. Sağlayıcı yapılandırması, kimlik bilgileri, geri dönüş adresleri ve gerçek ödeme testleri ayrıca doğrulanmalıdır.

### Projeyi yerel ortamda çalıştırabilir miyim?

PHP ve MySQL destekleyen yerel bir ortamda, yapılandırmayı buna göre düzenleyerek test edebilirsiniz. Canlı sunucuya özgü SMTP, ödeme ve URL ayarları yerel ortamda ayrıca ele alınmalıdır.

## Katkı

Botify'yi geliştirmek, hata bildirmek veya iyileştirme önermek istiyorsanız GitHub deposunu inceleyin. Değişiklik önermeden önce mevcut kodun davranışını test edin; özellikle kimlik doğrulama, ödeme, veritabanı ve API çağrısı akışlarında geriye dönük uyumluluğu gözetin.

- Depo: https://github.com/retrovision-ui/Botify/
- Canlı site: https://viosrio.serv00.net/public/

## Lisans

Bu depoda bir lisans dosyası bulunup bulunmadığını kontrol edin ve dağıtım koşullarını netleştirin. Açık bir lisans belirtilmemişse, kodun otomatik olarak yeniden kullanım veya yeniden dağıtım izni verdiğini varsaymayın.

---

<p align="center">
  <strong>Botify — API keşfi için daha düzenli bir başlangıç noktası.</strong><br>
  <sub>Powered by OpenAI</sub>
</p>
