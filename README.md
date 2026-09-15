# BOTIFY V4 — mega güncelleme

## ⚠️ Önce bunu oku — altyapı düzeltmesi
Canlı veritabanını incelerken tüm tabloların **MyISAM** motoruyla oluştuğunu gördüm (muhtemelen hosting varsayılanı). MyISAM iki şeyi sessizce çalıştırmaz:
- **FOREIGN KEY / ON DELETE CASCADE** — bir API veya kullanıcı silindiğinde bağlı satırlar (yorum, mesaj, parametre…) yetim kalır.
- **Transaction/rollback** — satın alma, çekim talebi gibi "ya hep ya hiç" işlemlerde yarıda kesilme olursa veri tutarsız kalabilir.

`new.4.sql` dosyasının en başında tüm tabloları **InnoDB**'ye çeviren `ALTER TABLE ... ENGINE=InnoDB` satırları var — bunları çalıştırmak veriyi silmez, sadece motoru düzeltir. Yeni kurulumlarda `v3_database.sql` zaten `ENGINE=InnoDB` ile geliyor.

## ⚠️ Ayrıca: bir API anahtarı sızıntısı buldum
Test verinde `SMS Api` ilanına yüklenen kaynak dosyasının içine gerçek bir RapidAPI anahtarı düz metin olarak yapıştırılmış, ve bu dosyayı satın alan kullanıcı zaten indirip yorum bırakmış ("Kaynak kod için thanks"). Yani o anahtar bir başka kullanıcıya görünmüş durumda — **o RapidAPI anahtarını hemen iptal edip yenisini almanı öneririm.**
Bunu tekrar yaşamamak için Studio'daki dosya yükleme artık: dosyada anahtar/token benzeri bir şey bulursa hem istemci hem sunucu tarafında **kaynak koddan otomatik siliyor** ve "Gizli Başlıklar" kutusuna taşıyor — indirilebilir kaynak kodda artık düz metin anahtar kalmıyor.

## v4-mega'da yeni olanlar
- **Giriş/Kaydol/Şifremi Unuttum:** attığın geminy.me görseline ve `login_screen_update/` referanslarına göre yeniden tasarlandı — animasyonlu blob arkaplan, blur cam kart, ikonlu pill input'lar, "Beni Hatırla" ile çerezli sessiz giriş.
- **Alt menü (footer):** `login_screen_update/footer-liquid.css`'ten ilham alarak her sekme kendi "liquid glass" kutucuğu oldu, aktif sekme mor-pembe parıltıyla öne çıkıyor.
- **🔐 Önemli düzeltme:** Stripe gizli anahtarı ve IBAN için **hash değil, geri döndürülebilir şifreleme (AES-256)** kullanıyorum — hash tek yönlüdür, sistemin ödeme alabilmesi için anahtarı tekrar okuyabilmesi lazım. Hash sadece şifre ve "beni hatırla" tokenı gibi yalnızca *doğrulanması* gereken yerlerde kullanılıyor.
- **Ayarlar artık Telegram tarzı bir menü:** Profil sayfası artık bir hub — Kişisel Bilgiler / Mesajlar / Bildirimler / Ödemeler / Çekim Talebi / Hakkımızda, her biri kendi sayfasında (`settings-account.php`, `settings-notifications.php`, `settings-payments.php`, `about.php`).
- **Hakkımızda:** "Powered by Claude (Anthropic) 🌲" — söz verdiğim gibi.
- **Kullanıcı bazlı Stripe:** `settings-payments.php`'den satıcı kendi Stripe gizli anahtarını bağlıyor (şifreli saklanır). Alıcının bakiyesi API fiyatına yetmezse artık gerçek bir **Stripe Checkout** ekranına yönleniyor ve ödeme doğrudan satıcının Stripe hesabına gidiyor — Botify parayı üstünden geçirmiyor. Dönüşte `checkout-return.php` ödemeyi Stripe API'den tekrar doğrulayıp erişimi açıyor.
- **Çekim Talebi:** artık Stripe'a ek olarak **Banka/IBAN** seçeneği de var (Ad Soyad + IBAN, şifreli saklanır).
- **my-apis.php'deki taşan "Sil" butonu düzeltildi:** artık *Görüntüle | ⋯ Diğer* (Veri Seti / Sil) şeklinde toplandı. Bu arada gizli bir bug da buldum: silme işlemi sunucuda çalışıyordu ama satır ekrandan kaybolmuyordu (yanlış DOM hedefi) — onu da düzelttim.
- **Dosya yükleyerek API yayınlama artık daha akıllı:** yüklenen `.php/.js/.py` dosyasını tarayıp URL, parametre ve gizli anahtar adaylarını otomatik dolduruyor (yukarıdaki sızıntı notuna bak).
- **chat.php "bulunamadı" hatası hakkında:** kodda bir hata bulamadım; veritabanı incelemesinde `messages` tablosunun zaten var olduğunu gördüm, yani muhtemelen geçiciydi ya da önbellek kaynaklıydı. Yine de sorun devam ederse hangi adımda/hangi tarayıcıda olduğunu söyle, birlikte bakalım.

## Kurulum
1. **Önce** `new.4.sql`'in en üstündeki `ENGINE=InnoDB` satırlarını çalıştır (bu dosyanın kendisi zaten bunları en başta içeriyor, sırasıyla çalıştırman yeterli).
2. Yeni kurulum: `v3_database.sql` içeri aktar.
3. Var olan kuruluma yükseltme: `new.sql` → `v3-mega.sql` → `new.4.sql` sırasıyla.
4. `app/config.example.php` → `app/config.php`; DB bilgilerini gir, **`ENCRYPTION_KEY`'i rastgele/uzun bir değerle doldur** (Stripe anahtarı ve IBAN bunsuz şifrelenemez), istersen `STRIPE_SECRET_KEY` ekle.
5. Sırları asla commit etme.

## Klasör Yapısı
- `public/` — sayfalar (index, login, register, forgot, reset, dashboard, studio, my-apis, api, purchases, profile, settings-account, settings-notifications, settings-payments, about, console, messages, chat, dataset, payouts, checkout-return)
- `api/v1/` — JSON uç noktaları
- `api/middleware/` — oturum/anahtar doğrulama, rate-limit
- `assets/CSS/style.css` — tüm paylaşılan bileşenler (tek kaynak)
- `app/functions.php` — `encrypt_secret()`/`decrypt_secret()` (AES-256, ENCRYPTION_KEY ile)
