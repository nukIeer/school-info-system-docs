# Veritabanı Tabloları

Bu dokümanda E-Okul Veli Bilgilendirme Sistemi'nin veritabanı tablolarının detaylı açıklamaları bulunmaktadır.

## 1. Öğrenci Tablosu (OGRENCI)

Öğrencilerin temel bilgilerini içeren tablo.

| Alan Adı | Veri Tipi | Açıklama | Kısıtlamalar |
|----------|-----------|-----------|--------------|
| id | int | Benzersiz tanımlayıcı | Primary Key, Auto Increment |
| ad | string | Öğrencinin adı | Not Null |
| soyad | string | Öğrencinin soyadı | Not Null |
| adres | string | Öğrencinin adresi | Null |
| telefon | string | İletişim numarası | Null |
| tc_kimlik | string | TC Kimlik numarası | Unique, Not Null |
| sifre | string | Şifre (hash'lenmiş) | Not Null |
| sinif | string | Öğrencinin sınıfı | Not Null |
| sube | string | Öğrencinin şubesi | Not Null |
| fotograf | string | Fotoğraf URL'i | Null |

## 2. Not Tablosu (NOT)

Öğrencilerin ders notlarını içeren tablo.

| Alan Adı | Veri Tipi | Açıklama | Kısıtlamalar |
|----------|-----------|-----------|--------------|
| id | int | Benzersiz tanımlayıcı | Primary Key, Auto Increment |
| ogrenci_id | int | Öğrenci referansı | Foreign Key |
| ders_id | int | Ders referansı | Foreign Key |
| sinav1 | int | 1. sınav notu | 0-100 arası |
| sinav2 | int | 2. sınav notu | 0-100 arası |
| sinav3 | int | 3. sınav notu | 0-100 arası |
| proje1 | int | 1. proje notu | 0-100 arası |
| proje2 | int | 2. proje notu | 0-100 arası |
| performans1 | int | 1. performans notu | 0-100 arası |
| performans2 | int | 2. performans notu | 0-100 arası |
| performans3 | int | 3. performans notu | 0-100 arası |
| ortalama | float | Ders ortalaması | Hesaplanan alan |
| beslik_karsilik | int | 5'lik sistem karşılığı | 1-5 arası |
| donem | int | Dönem bilgisi | 1 veya 2 |
| yil | int | Akademik yıl | Not Null |

## 3. Devamsızlık Tablosu (DEVAMSIZLIK)

Öğrencilerin devamsızlık kayıtlarını içeren tablo.

| Alan Adı | Veri Tipi | Açıklama | Kısıtlamalar |
|----------|-----------|-----------|--------------|
| id | int | Benzersiz tanımlayıcı | Primary Key, Auto Increment |
| ogrenci_id | int | Öğrenci referansı | Foreign Key |
| tarih | date | Devamsızlık tarihi | Not Null |
| tur | string | Devamsızlık türü | Not Null |

## 4. Kitap-Öğrenci Tablosu (KITAP-OGRENCI)

Öğrencilerin okuduğu kitapların kayıtlarını içeren tablo.

| Alan Adı | Veri Tipi | Açıklama | Kısıtlamalar |
|----------|-----------|-----------|--------------|
| id | int | Benzersiz tanımlayıcı | Primary Key, Auto Increment |
| ogrenci_id | int | Öğrenci referansı | Foreign Key |
| kitap_id | int | Kitap referansı | Foreign Key |
| okuma_tarihi | date | Kitabın okunduğu tarih | Not Null |

## 5. Belge-Öğrenci Tablosu (BELGE-OGRENCI)

Öğrencilere verilen belgelerin kayıtlarını içeren tablo.

| Alan Adı | Veri Tipi | Açıklama | Kısıtlamalar |
|----------|-----------|-----------|--------------|
| id | int | Benzersiz tanımlayıcı | Primary Key, Auto Increment |
| ogrenci_id | int | Öğrenci referansı | Foreign Key |
| belge_id | int | Belge referansı | Foreign Key |
| verilis_tarihi | date | Belgenin verildiği tarih | Not Null |

## 6. Öğretmen Tablosu (OGRETMEN)

Öğretmenlerin bilgilerini içeren tablo.

| Alan Adı | Veri Tipi | Açıklama | Kısıtlamalar |
|----------|-----------|-----------|--------------|
| id | int | Benzersiz tanımlayıcı | Primary Key, Auto Increment |
| ad | string | Öğretmenin adı | Not Null |
| soyad | string | Öğretmenin soyadı | Not Null |
| adres | string | Öğretmenin adresi | Null |
| telefon | string | İletişim numarası | Null |
| email | string | E-posta adresi | Unique, Not Null |
| kullanici_adi | string | Kullanıcı adı | Unique, Not Null |
| sifre | string | Şifre (hash'lenmiş) | Not Null |
| brans | string | Branş bilgisi | Not Null |

## 7. Ders Tablosu (DERS)

Ders bilgilerini içeren tablo.

| Alan Adı | Veri Tipi | Açıklama | Kısıtlamalar |
|----------|-----------|-----------|--------------|
| id | int | Benzersiz tanımlayıcı | Primary Key, Auto Increment |
| ad | string | Ders adı | Not Null |
| sinif | int | Sınıf seviyesi | Not Null |

## 8. Kitap Tablosu (KITAP)

Kütüphanedeki kitapların bilgilerini içeren tablo.

| Alan Adı | Veri Tipi | Açıklama | Kısıtlamalar |
|----------|-----------|-----------|--------------|
| id | int | Benzersiz tanımlayıcı | Primary Key, Auto Increment |
| ad | string | Kitap adı | Not Null |
| yazar | string | Yazar adı | Not Null |
| seri_no | string | Kitap seri numarası | Unique, Not Null |

## 9. Belge Tablosu (BELGE)

Belge türlerini içeren tablo.

| Alan Adı | Veri Tipi | Açıklama | Kısıtlamalar |
|----------|-----------|-----------|--------------|
| id | int | Benzersiz tanımlayıcı | Primary Key, Auto Increment |
| ad | string | Belge adı | Not Null |
| tur | string | Belge türü | Not Null |

## 10. Sınav-Proje Tablosu (SINAV-PROJE)

Sınav ve proje bilgilerini içeren tablo.

| Alan Adı | Veri Tipi | Açıklama | Kısıtlamalar |
|----------|-----------|-----------|--------------|
| id | int | Benzersiz tanımlayıcı | Primary Key, Auto Increment |
| ders_id | int | Ders referansı | Foreign Key |
| baslik | string | Sınav/Proje başlığı | Not Null |
| tarih | date | Sınav/Proje tarihi | Not Null |
| aciklama | string | Açıklama | Null | 