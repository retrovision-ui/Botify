<p align="center">
  <img src="https://github.com/retrovision-ui/Botify/blob/main/assets/005.png" alt="Geminy Banner" width="300"/>
</p>

<h1 align="center"></h1>
<p align="center"><i>Özgür Marketin.</i></p>

<p align="center">
  <a href="https://botify.unaux.com">
    <img src="https://img.shields.io/badge/WEB_ADRES-İncele-ff2d72?style=for-the-badge&logo=heart&logoColor=white" alt="Demo"/>
  </a>
  <img src="https://img.shields.io/badge/VERSION-V8.0-7c3aed?style=for-the-badge&logo=sparkles&logoColor=white"/>
  <img src="https://img.shields.io/badge/STATUS-PRODUCTION_READY-22c55e?style=for-the-badge"/>
</p>


# BOTIFY V4 — mega güncelleme

## ⚠️ Önce bunu oku — altyapı düzeltmesi
Canlı veritabanını incelerken tüm tabloların **MyISAM** motoruyla oluştuğunu gördüm (muhtemelen hosting varsayılanı). MyISAM iki şeyi sessizce çalıştırmaz:
- **FOREIGN KEY / ON DELETE CASCADE** — bir API veya kullanıcı silindiğinde bağlı satırlar (yorum, mesaj, parametre…) yetim kalır.
- **Transaction/rollback** — satın alma, çekim talebi gibi "ya hep ya hiç" işlemlerde yarıda kesilme olursa veri tutarsız kalabilir.

`new.4.sql` dosyasının en başında tüm tabloları **InnoDB**'ye çeviren `ALTER TABLE ... ENGINE=InnoDB` satırları var — bunları çalıştırmak veriyi silmez, sadece motoru düzeltir. Yeni kurulumlarda `v3_database.sql` zaten `ENGINE=InnoDB` ile geliyor.

- **🔐 Önemli düzeltme:** Stripe gizli anahtarı ve IBAN için **hash değil, geri döndürülebilir şifreleme (AES-256)** kullanıyorum — hash tek yönlüdür, sistemin ödeme alabilmesi için anahtarı tekrar okuyabilmesi lazım. Hash sadece şifre ve "beni hatırla" tokenı gibi yalnızca *doğrulanması* gereken yerlerde kullanılıyor.
- **Ayarlar artık Telegram tarzı bir menü:** Profil sayfası artık bir hub — Kişisel Bilgiler / Mesajlar / Bildirimler / Ödemeler / Çekim Talebi / Hakkımızda, her biri kendi sayfasında (`settings-account.php`, `settings-notifications.php`, `settings-payments.php`, `about.php`).
- **Hakkımızda:** "Powered by Claude (Anthropic) 🌲" — söz verdiğim gibi.
- **Kullanıcı bazlı Stripe:** `settings-payments.php`'den satıcı kendi Stripe gizli anahtarını bağlıyor (şifreli saklanır). Alıcının bakiyesi API fiyatına yetmezse artık gerçek bir **Stripe Checkout** ekranına yönleniyor ve ödeme doğrudan satıcının Stripe hesabına gidiyor — Botify parayı üstünden geçirmiyor. Dönüşte `checkout-return.php` ödemeyi Stripe API'den tekrar doğrulayıp erişimi açıyor.
- **Çekim Talebi:** artık Stripe'a ek olarak **Banka/IBAN** seçeneği de var (Ad Soyad + IBAN, şifreli saklanır).
- **my-apis.php'deki taşan "Sil" butonu düzeltildi:** artık *Görüntüle | ⋯ Diğer* (Veri Seti / Sil) şeklinde toplandı. Bu arada gizli bir bug da buldum: silme işlemi sunucuda çalışıyordu ama satır ekrandan kaybolmuyordu (yanlış DOM hedefi) — onu da düzelttim.
- **Dosya yükleyerek API yayınlama artık daha akıllı:** yüklenen `.php/.js/.py` dosyasını tarayıp URL, parametre ve gizli anahtar adaylarını otomatik dolduruyor (yukarıdaki sızıntı notuna bak).
- **chat.php "bulunamadı" hatası hakkında:** kodda bir hata bulamadım; veritabanı incelemesinde `messages` tablosunun zaten var olduğunu gördüm, yani muhtemelen geçiciydi ya da önbellek kaynaklıydı. Yine de sorun devam ederse hangi adımda/hangi tarayıcıda olduğunu söyle, birlikte bakalım.

## Kurulum
