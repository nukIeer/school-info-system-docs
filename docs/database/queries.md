# Örnek SQL Sorguları

Bu dokümanda E-Okul Veli Bilgilendirme Sistemi için kullanılabilecek örnek SQL sorguları bulunmaktadır.

## Öğrenci İşlemleri

### 1. Öğrenci Ekleme
```sql
INSERT INTO OGRENCI (ad, soyad, adres, telefon, tc_kimlik, sifre, sinif, sube, fotograf)
VALUES ('Ahmet', 'Yılmaz', 'İstanbul', '5551234567', '12345678901', 'hashed_password', '9', 'A', 'foto.jpg');
```

### 2. Öğrenci Bilgilerini Güncelleme
```sql
UPDATE OGRENCI
SET adres = 'Ankara', telefon = '5559876543'
WHERE id = 1;
```

### 3. Öğrenci Silme
```sql
DELETE FROM OGRENCI
WHERE id = 1;
```

### 4. Öğrenci Listesi
```sql
SELECT id, ad, soyad, sinif, sube
FROM OGRENCI
ORDER BY sinif, sube, soyad;
```

## Not İşlemleri

### 1. Not Ekleme
```sql
INSERT INTO NOT (ogrenci_id, ders_id, sinav1, sinav2, proje1, performans1, donem, yil)
VALUES (1, 1, 85, 90, 95, 88, 1, 2024);
```

### 2. Not Güncelleme
```sql
UPDATE NOT
SET sinav1 = 90
WHERE ogrenci_id = 1 AND ders_id = 1 AND donem = 1 AND yil = 2024;
```

### 3. Öğrencinin Tüm Notlarını Listeleme
```sql
SELECT n.*, d.ad as ders_adi
FROM NOT n
JOIN DERS d ON n.ders_id = d.id
WHERE n.ogrenci_id = 1
ORDER BY d.ad;
```

### 4. Sınıf Ortalaması Hesaplama
```sql
SELECT d.ad as ders_adi, AVG(n.ortalama) as sinif_ortalamasi
FROM NOT n
JOIN DERS d ON n.ders_id = d.id
JOIN OGRENCI o ON n.ogrenci_id = o.id
WHERE o.sinif = '9' AND o.sube = 'A' AND n.donem = 1 AND n.yil = 2024
GROUP BY d.ad;
```

## Devamsızlık İşlemleri

### 1. Devamsızlık Ekleme
```sql
INSERT INTO DEVAMSIZLIK (ogrenci_id, tarih, tur)
VALUES (1, '2024-03-15', 'Özürlü');
```

### 2. Öğrencinin Devamsızlık Listesi
```sql
SELECT d.tarih, d.tur
FROM DEVAMSIZLIK d
WHERE d.ogrenci_id = 1
ORDER BY d.tarih DESC;
```

### 3. Sınıf Devamsızlık Raporu
```sql
SELECT o.ad, o.soyad, COUNT(*) as devamsizlik_sayisi
FROM DEVAMSIZLIK d
JOIN OGRENCI o ON d.ogrenci_id = o.id
WHERE o.sinif = '9' AND o.sube = 'A'
GROUP BY o.id, o.ad, o.soyad
ORDER BY devamsizlik_sayisi DESC;
```

## Kitap İşlemleri

### 1. Kitap Ekleme
```sql
INSERT INTO KITAP (ad, yazar, seri_no)
VALUES ('Suç ve Ceza', 'Dostoyevski', 'ISBN123456');
```

### 2. Öğrenciye Kitap Atama
```sql
INSERT INTO KITAP-OGRENCI (ogrenci_id, kitap_id, okuma_tarihi)
VALUES (1, 1, '2024-03-15');
```

### 3. Öğrencinin Okuduğu Kitaplar
```sql
SELECT k.ad, k.yazar, ko.okuma_tarihi
FROM KITAP-OGRENCI ko
JOIN KITAP k ON ko.kitap_id = k.id
WHERE ko.ogrenci_id = 1
ORDER BY ko.okuma_tarihi DESC;
```

## Belge İşlemleri

### 1. Belge Ekleme
```sql
INSERT INTO BELGE (ad, tur)
VALUES ('Takdir Belgesi', 'Başarı');
```

### 2. Öğrenciye Belge Verme
```sql
INSERT INTO BELGE-OGRENCI (ogrenci_id, belge_id, verilis_tarihi)
VALUES (1, 1, '2024-03-15');
```

### 3. Öğrencinin Belgeleri
```sql
SELECT b.ad, b.tur, bo.verilis_tarihi
FROM BELGE-OGRENCI bo
JOIN BELGE b ON bo.belge_id = b.id
WHERE bo.ogrenci_id = 1
ORDER BY bo.verilis_tarihi DESC;
```

## Öğretmen İşlemleri

### 1. Öğretmen Ekleme
```sql
INSERT INTO OGRETMEN (ad, soyad, email, kullanici_adi, sifre, brans)
VALUES ('Mehmet', 'Demir', 'mehmet@okul.com', 'mehmet.demir', 'hashed_password', 'Matematik');
```

### 2. Öğretmen Bilgilerini Güncelleme
```sql
UPDATE OGRETMEN
SET telefon = '5551234567', adres = 'İstanbul'
WHERE id = 1;
```

### 3. Branş Bazlı Öğretmen Listesi
```sql
SELECT ad, soyad, email, telefon
FROM OGRETMEN
WHERE brans = 'Matematik'
ORDER BY soyad;
```

## Ders İşlemleri

### 1. Ders Ekleme
```sql
INSERT INTO DERS (ad, sinif)
VALUES ('Matematik', 9);
```

### 2. Sınıf Ders Listesi
```sql
SELECT ad
FROM DERS
WHERE sinif = 9
ORDER BY ad;
```

## Sınav-Proje İşlemleri

### 1. Sınav Ekleme
```sql
INSERT INTO SINAV-PROJE (ders_id, baslik, tarih, aciklama)
VALUES (1, '1. Dönem 1. Sınav', '2024-03-20', 'Tüm konular');
```

### 2. Ders Sınav Listesi
```sql
SELECT baslik, tarih, aciklama
FROM SINAV-PROJE
WHERE ders_id = 1
ORDER BY tarih DESC;
```

## Karma Sorgular

### 1. Öğrenci Başarı Durumu
```sql
SELECT o.ad, o.soyad, d.ad as ders_adi, n.ortalama, n.beslik_karsilik
FROM OGRENCI o
JOIN NOT n ON o.id = n.ogrenci_id
JOIN DERS d ON n.ders_id = d.id
WHERE o.id = 1 AND n.donem = 1 AND n.yil = 2024
ORDER BY d.ad;
```

### 2. Sınıf Başarı Sıralaması
```sql
SELECT o.ad, o.soyad, AVG(n.ortalama) as genel_ortalama
FROM OGRENCI o
JOIN NOT n ON o.id = n.ogrenci_id
WHERE o.sinif = '9' AND o.sube = 'A' AND n.donem = 1 AND n.yil = 2024
GROUP BY o.id, o.ad, o.soyad
ORDER BY genel_ortalama DESC;
```

### 3. Öğretmen Ders Yükü
```sql
SELECT o.ad, o.soyad, COUNT(DISTINCT d.id) as ders_sayisi
FROM OGRETMEN o
JOIN DERS d ON o.brans = d.ad
GROUP BY o.id, o.ad, o.soyad
ORDER BY ders_sayisi DESC;
``` 