# Kurulum Kılavuzu

Bu dokümanda E-Okul Veli Bilgilendirme Sistemi'nin kurulum adımları detaylı olarak anlatılmaktadır.

## Sistem Gereksinimleri

### Sunucu Gereksinimleri
- İşletim Sistemi: Windows Server 2019 veya üzeri
- CPU: 4 çekirdek veya üzeri
- RAM: 8GB veya üzeri
- Disk: 100GB veya üzeri
- Ağ: 100Mbps veya üzeri

### Yazılım Gereksinimleri
- Web Sunucusu: IIS 10.0 veya üzeri
- Veritabanı: SQL Server 2019 veya üzeri
- .NET Framework: 4.8 veya üzeri
- SSL Sertifikası: Geçerli bir SSL sertifikası

## Kurulum Adımları

### 1. Veritabanı Kurulumu

1. SQL Server Management Studio'yu açın
2. Yeni bir veritabanı oluşturun:
   ```sql
   CREATE DATABASE EOkulVBS
   ```
3. Veritabanı scriptini çalıştırın:
   ```sql
   USE EOkulVBS
   GO
   -- Script dosyasını çalıştırın
   ```

### 2. Web Sunucusu Kurulumu

1. IIS'i açın
2. Yeni bir web sitesi oluşturun:
   - Site adı: EOkulVBS
   - Fiziksel yol: C:\inetpub\wwwroot\EOkulVBS
   - Port: 443 (HTTPS)
   - SSL sertifikası: Seçin

3. Application Pool ayarları:
   - .NET Framework versiyonu: 4.8
   - Managed Pipeline Mode: Integrated
   - Identity: ApplicationPoolIdentity

### 3. Uygulama Kurulumu

1. Uygulama dosyalarını kopyalayın:
   ```
   xcopy /E /I /Y "KaynakKlasör" "C:\inetpub\wwwroot\EOkulVBS"
   ```

2. Web.config dosyasını düzenleyin:
   ```xml
   <configuration>
     <connectionStrings>
       <add name="DefaultConnection" 
            connectionString="Server=localhost;Database=EOkulVBS;Trusted_Connection=True;"
            providerName="System.Data.SqlClient" />
     </connectionStrings>
   </configuration>
   ```

3. Uygulama havuzunu yeniden başlatın:
   ```
   iisreset
   ```

### 4. SSL Sertifikası Kurulumu

1. SSL sertifikasını alın:
   - Let's Encrypt
   - Comodo
   - DigiCert

2. Sertifikayı IIS'e yükleyin:
   - IIS Manager > Server Certificates
   - Import
   - Sertifika dosyasını seçin

3. Web sitesine sertifikayı atayın:
   - Site > Bindings
   - HTTPS binding ekleyin
   - Sertifikayı seçin

### 5. Güvenlik Ayarları

1. Windows Authentication'ı etkinleştirin:
   ```
   %windir%\system32\inetsrv\appcmd.exe set config /section:windowsAuthentication /enabled:true
   ```

2. SSL/TLS ayarlarını yapılandırın:
   ```
   %windir%\system32\inetsrv\appcmd.exe set config /section:system.webServer/security/requestFiltering /sslFlags:"Ssl, SslNegotiateCert"
   ```

3. IP kısıtlamalarını ayarlayın:
   - IIS Manager > IP Address and Domain Restrictions
   - Add Allow Entry
   - Okul IP adreslerini ekleyin

### 6. Yedekleme Ayarları

1. Veritabanı yedekleme:
   ```sql
   BACKUP DATABASE EOkulVBS
   TO DISK = 'C:\Backup\EOkulVBS.bak'
   WITH FORMAT, INIT, NAME = 'EOkulVBS-Full Database Backup'
   ```

2. Otomatik yedekleme planı oluşturun:
   - SQL Server Agent > Jobs
   - New Job
   - Schedule: Daily
   - Backup scriptini ekleyin

### 7. Performans Ayarları

1. IIS ayarları:
   - Application Pool > Advanced Settings
   - Maximum Worker Processes: 1
   - Idle Time-out: 20 minutes
   - Recycling: 1740 minutes

2. SQL Server ayarları:
   - Memory: 4GB
   - Max Degree of Parallelism: 4
   - Cost Threshold for Parallelism: 50

### 8. Loglama Ayarları

1. IIS logları:
   - Log File Directory: C:\inetpub\logs\LogFiles
   - Log Format: W3C
   - Log Period: Daily

2. Uygulama logları:
   - Log Directory: C:\inetpub\wwwroot\EOkulVBS\Logs
   - Log Level: Information
   - Log Format: JSON

## Kurulum Sonrası Kontroller

### 1. Sistem Kontrolleri
- Veritabanı bağlantısı
- Web sitesi erişimi
- SSL sertifikası
- Windows Authentication

### 2. Performans Kontrolleri
- Sayfa yüklenme süreleri
- Veritabanı sorgu süreleri
- CPU ve RAM kullanımı
- Disk I/O

### 3. Güvenlik Kontrolleri
- SSL/TLS versiyonu
- Şifreleme algoritmaları
- Firewall kuralları
- IP kısıtlamaları

### 4. Yedekleme Kontrolleri
- Otomatik yedekleme
- Yedek dosya boyutu
- Yedek süresi
- Yedek konumu

## Sorun Giderme

### 1. Veritabanı Sorunları
- Bağlantı hatası
- Yetki hatası
- Disk alanı
- Performans sorunları

### 2. Web Sunucusu Sorunları
- 500 Internal Server Error
- 404 Not Found
- SSL hatası
- Authentication hatası

### 3. Uygulama Sorunları
- Sayfa yüklenme hatası
- JavaScript hatası
- CSS hatası
- API hatası

### 4. Performans Sorunları
- Yavaş sayfa yüklenme
- Yüksek CPU kullanımı
- Yüksek RAM kullanımı
- Disk I/O sorunları

## Bakım ve Güncelleme

### 1. Günlük Bakım
- Log dosyalarını kontrol etme
- Disk alanını kontrol etme
- Yedekleri kontrol etme
- Performans metriklerini kontrol etme

### 2. Haftalık Bakım
- Veritabanı indekslerini yenileme
- Temp dosyaları temizleme
- Log dosyalarını arşivleme
- Güvenlik güncellemelerini kontrol etme

### 3. Aylık Bakım
- Veritabanı bakımı
- IIS yeniden başlatma
- SSL sertifikası kontrolü
- Yedekleme testi

### 4. Yıllık Bakım
- Donanım kontrolü
- Yazılım güncellemeleri
- Lisans yenileme
- Performans optimizasyonu 