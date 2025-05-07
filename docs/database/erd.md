# Birim İlişki Diyagramı (ERD)

E-Okul Veli Bilgilendirme Sistemi'nin veritabanı tasarımını gösteren ERD diyagramı aşağıda verilmiştir.

```mermaid
erDiagram
    OGRENCI {
        int id PK
        string ad
        string soyad
        string adres
        string telefon
        string tc_kimlik
        string sifre
        string sinif
        string sube
        string fotograf
    }
    
    NOT {
        int id PK
        int ogrenci_id FK
        int ders_id FK
        int sinav1
        int sinav2
        int sinav3
        int proje1
        int proje2
        int performans1
        int performans2
        int performans3
        float ortalama
        int beslik_karsilik
        int donem
        int yil
    }
    
    DEVAMSIZLIK {
        int id PK
        int ogrenci_id FK
        date tarih
        string tur
    }
    
    KITAP-OGRENCI {
        int id PK
        int ogrenci_id FK
        int kitap_id FK
        date okuma_tarihi
    }
    
    BELGE-OGRENCI {
        int id PK
        int ogrenci_id FK
        int belge_id FK
        date verilis_tarihi
    }
    
    OGRETMEN {
        int id PK
        string ad
        string soyad
        string adres
        string telefon
        string email
        string kullanici_adi
        string sifre
        string brans
    }
    
    DERS {
        int id PK
        string ad
        int sinif
    }
    
    KITAP {
        int id PK
        string ad
        string yazar
        string seri_no
    }
    
    BELGE {
        int id PK
        string ad
        string tur
    }
    
    SINAV-PROJE {
        int id PK
        int ders_id FK
        string baslik
        date tarih
        string aciklama
    }

    OGRENCI ||--o{ NOT : "alır"
    OGRENCI ||--o{ DEVAMSIZLIK : "yapar"
    OGRENCI ||--o{ KITAP-OGRENCI : "okur"
    OGRENCI ||--o{ BELGE-OGRENCI : "alır"
    OGRETMEN ||--o{ DERS : "verir"
    DERS ||--o{ NOT : "içerir"
    DERS ||--o{ SINAV-PROJE : "içerir"
    KITAP ||--o{ KITAP-OGRENCI : "okunur"
    BELGE ||--o{ BELGE-OGRENCI : "verilir"
```

## Açıklama

ERD diyagramı, sistemin veritabanı yapısını ve tablolar arasındaki ilişkileri göstermektedir. Sistem aşağıdaki temel tablolardan oluşmaktadır:

### Temel Tablolar

1. **Öğrenci Tablosu**
   - Öğrenci bilgileri
   - Kişisel bilgiler
   - İletişim bilgileri

2. **Not Tablosu**
   - Sınav notları
   - Proje notları
   - Performans notları
   - Ortalama hesaplamaları

3. **Devamsızlık Tablosu**
   - Devamsızlık kayıtları
   - Devamsızlık türleri
   - Tarih bilgileri

4. **Kitap-Öğrenci Tablosu**
   - Kitap okuma kayıtları
   - Okuma tarihleri
   - Kitap bilgileri

5. **Belge-Öğrenci Tablosu**
   - Belge kayıtları
   - Veriliş tarihleri
   - Belge bilgileri

6. **Öğretmen Tablosu**
   - Öğretmen bilgileri
   - İletişim bilgileri
   - Branş bilgileri

7. **Ders Tablosu**
   - Ders bilgileri
   - Sınıf bilgileri

8. **Kitap Tablosu**
   - Kitap bilgileri
   - Yazar bilgileri
   - Seri numaraları

9. **Belge Tablosu**
   - Belge bilgileri
   - Belge türleri

10. **Sınav-Proje Tablosu**
    - Sınav bilgileri
    - Proje bilgileri
    - Tarih bilgileri 