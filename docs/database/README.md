# Veritabanı Tasarım Dokümantasyonu

## Genel Bakış

Bu bölüm, E-Okul Veli Bilgilendirme Sistemi'nin veritabanı tasarım dokümantasyonunu içermektedir.

## İçindekiler

1. [Varlık İlişki Diyagramı](erd.md)
2. [Veritabanı Tabloları](tables.md)
3. [Örnek Sorgular](queries.md)

## Veritabanı Yapısı

Veritabanı, sistemin tüm temel işlevlerini destekleyecek şekilde tasarlanmıştır:

### Temel Tablolar
- [Kullanıcılar](tables.md#kullanicilar)
- [Öğrenciler](tables.md#ogrenciler)
- [Öğretmenler](tables.md#ogretmenler)
- [Sınıflar](tables.md#siniflar)

### Akademik Yönetim
- [Notlar](tables.md#notlar)
- [Dersler](tables.md#dersler)
- [Sınavlar](tables.md#sinavlar)

### Devamsızlık Sistemi
- [Devamsızlık Kayıtları](tables.md#devamsizlik-kayitlari)
- [Devamsızlık Türleri](tables.md#devamsizlik-turleri)

### Kütüphane Yönetimi
- [Kitaplar](tables.md#kitaplar)
- [Kitap Ödünç Kayıtları](tables.md#kitap-odunc-kayitlari)

### Belge Yönetimi
- [Belgeler](tables.md#belgeler)
- [Belge Türleri](tables.md#belge-turleri)

### İletişim
- [Duyurular](tables.md#duyurular)
- [Bildirimler](tables.md#bildirimler)

## İlgili Dokümantasyon

- [Sistem Genel Bakış](../diagrams/general-system.md)
- [Ekran Tasarımları](../screens/README.md)
- [Kurulum Kılavuzu](../installation/guide.md)
- [Kullanım Kılavuzu](../usage/guide.md)

## Veritabanı Tasarım Süreci

1. Gereksinim Analizi
   - Kullanıcı ihtiyaçlarının değerlendirilmesi
   - Sistem işlevsellik gereksinimleri
   - Veri depolama gereksinimleri

2. Kavramsal Tasarım
   - Varlık tanımlama
   - İlişki eşleştirme
   - [Varlık İlişki Diyagramı](erd.md)

3. Mantıksal Tasarım
   - Tablo yapısı
   - Alan tanımları
   - [Veritabanı Tabloları](tables.md)

4. Fiziksel Tasarım
   - İndeksler
   - Kısıtlamalar
   - [Örnek Sorgular](queries.md)

## Veritabanı Bakımı

### Yedekleme Prosedürleri
- Günlük otomatik yedeklemeler
- Haftalık tam yedeklemeler
- Aylık arşiv yedeklemeleri

### Performans Optimizasyonu
- Düzenli indeks bakımı
- Sorgu optimizasyonu
- Veritabanı istatistiklerinin güncellenmesi

### Güvenlik Önlemleri
- Kullanıcı erişim kontrolü
- Veri şifreleme
- Denetim günlüğü

## Destek ve Kaynaklar

Veritabanı ile ilgili sorularınız için:
- İletişim: [sevda.torun@example.com]
- GitHub: [nukIeer](https://github.com/nukIeer) 