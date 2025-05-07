# Giriş Yapma İşlemi - Yapısal Dil Örneği

## Proses: Giriş Yapma
**Girdi:** Kullanıcı Adı, Şifre
**Çıktı:** Giriş Durumu

```plaintext
BAŞLA
    Kullanıcı tipi seç (Yönetici, Öğretmen, Öğrenci/Veli)
    Kullanıcı adı gir
    Şifre gir
    EĞER kullanıcı adı ve şifre doğru İSE
        EĞER hesap aktif İSE
            EĞER IP adresi güvenli İSE
                Oturum başlat
                Yetkileri yükle
                Ana sayfaya yönlendir
                Giriş logunu kaydet
            DEĞİLSE
                Güvenlik uyarısı göster
                Yöneticiye bildir
            SON EĞER
        DEĞİLSE
            Hesap devre dışı mesajı göster
            Yöneticiye bildir
        SON EĞER
    DEĞİLSE
        Hatalı giriş sayacını artır
        EĞER hatalı giriş sayısı >= 3 İSE
            Hesabı kilitle
            Yöneticiye bildir
        DEĞİLSE
            Hatalı giriş mesajı göster
        SON EĞER
    SON EĞER
BİTİR
```

## Açıklama

Giriş yapma işlemi, sistemin güvenliğini sağlayan temel süreçlerden biridir. Bu süreç aşağıdaki adımlardan oluşmaktadır:

### Süreç Adımları

1. **Kullanıcı Tipi Seçimi**
   - Yönetici
   - Öğretmen
   - Öğrenci/Veli

2. **Kimlik Bilgileri Girişi**
   - Kullanıcı adı
   - Şifre

3. **Kimlik Doğrulama**
   - Kullanıcı adı kontrolü
   - Şifre kontrolü
   - Hesap durumu kontrolü

4. **Güvenlik Kontrolleri**
   - IP adresi kontrolü
   - Hesap kilitleme kontrolü
   - Hatalı giriş sayısı kontrolü

5. **Oturum Yönetimi**
   - Oturum başlatma
   - Yetkileri yükleme
   - Ana sayfaya yönlendirme

6. **Log ve Bildirim**
   - Giriş logunu kaydetme
   - Güvenlik bildirimleri
   - Yönetici bildirimleri 