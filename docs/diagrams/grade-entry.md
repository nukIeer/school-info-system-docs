# Not Girme İşlemi - Yapısal Dil Örneği

## Proses: Not Girme
**Girdi:** Öğrenci Bilgisi, Ders Bilgisi, Not Bilgisi
**Çıktı:** Kaydedilmiş Not Bilgisi

```plaintext
BAŞLA
    Öğretmen girişi yap
    EĞER giriş başarılı İSE
        Sınıf seç
        Şube seç
        Öğrenci seç
        Ders seç
        Not türü seç (Sınav, Proje, Performans)
        Not değeri gir
        EĞER not değeri 0-100 aralığında İSE
            Notu kaydet
            Ortalama hesapla
            Beşlik sisteme çevir
            Başarı durumunu belirle
            Bildirim gönder
        DEĞİLSE
            Hata mesajı göster
        SON EĞER
    DEĞİLSE
        Giriş hatası mesajı göster
    SON EĞER
BİTİR
```

## Açıklama

Not girme işlemi, öğretmenlerin öğrencilerin notlarını sisteme girmesini sağlayan temel süreçlerden biridir. Bu süreç aşağıdaki adımlardan oluşmaktadır:

### Süreç Adımları

1. **Giriş Kontrolü**
   - Öğretmen girişi yapılır
   - Giriş başarılı ise devam edilir
   - Giriş başarısız ise hata mesajı gösterilir

2. **Öğrenci Seçimi**
   - Sınıf seçilir
   - Şube seçilir
   - Öğrenci seçilir

3. **Not Bilgisi Girişi**
   - Ders seçilir
   - Not türü seçilir (Sınav, Proje, Performans)
   - Not değeri girilir

4. **Not Doğrulama**
   - Not değeri 0-100 aralığında kontrol edilir
   - Geçerli ise kaydedilir
   - Geçersiz ise hata mesajı gösterilir

5. **Not İşlemleri**
   - Not kaydedilir
   - Ortalama hesaplanır
   - Beşlik sisteme çevrilir
   - Başarı durumu belirlenir

6. **Bildirim**
   - İlgili kullanıcılara bildirim gönderilir 