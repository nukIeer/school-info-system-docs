# Giriş Yapma Alt Seviye Diyagramı

E-Okul Veli Bilgilendirme Sistemi'nde giriş yapma sürecini gösteren alt seviye diyagramı aşağıda verilmiştir.

```mermaid
graph TD
    A[Giriş Yap]
    B[Kullanıcı Tipi Seçimi]
    C[Yönetici Girişi]
    D[Öğretmen Girişi]
    E[Öğrenci/Veli Girişi]
    F[Kullanıcı Adı/Şifre Kontrolü]
    G[Başarılı Giriş]
    H[Başarısız Giriş]
    I[Ana Sayfaya Yönlendir]
    J[Hata Mesajı Göster]
    
    A --> B
    B --> C
    B --> D
    B --> E
    C --> F
    D --> F
    E --> F
    F --> G
    F --> H
    G --> I
    H --> J
```

## Açıklama

Giriş yapma süreci, sistemin güvenliğini sağlayan temel süreçlerden biridir. Bu süreç aşağıdaki adımlardan oluşmaktadır:

### Süreç Adımları

1. **Kullanıcı Tipi Seçimi**
   - Yönetici girişi
   - Öğretmen girişi
   - Öğrenci/Veli girişi

2. **Kimlik Doğrulama**
   - Kullanıcı adı kontrolü
   - Şifre kontrolü
   - Güvenlik doğrulaması

3. **Giriş Sonucu**
   - Başarılı giriş
     - Ana sayfaya yönlendirme
     - Oturum başlatma
     - Yetkilendirme
   - Başarısız giriş
     - Hata mesajı gösterme
     - Yeniden deneme imkanı
     - Güvenlik önlemleri

4. **Güvenlik Önlemleri**
   - Şifre sıfırlama
   - Hesap kilitleme
   - Güvenlik logları
   - IP kontrolü 