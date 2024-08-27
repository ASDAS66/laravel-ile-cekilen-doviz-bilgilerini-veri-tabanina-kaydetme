TCMB Döviz Kurları Laravel Projesi
Bu proje, Türkiye Cumhuriyet Merkez Bankası'ndan (TCMB) güncel döviz kurlarını çekip, bu verileri veritabanına kaydetmek için geliştirilmiş bir Laravel uygulamasıdır.

Özellikler
Güncel Döviz Kurları Çekme: TCMB'nin sağladığı XML servisinden döviz kurlarını çekme.
Veritabanına Kaydetme: Çekilen döviz kurlarını veritabanına kaydetme.
Planlanmış Görev: Döviz kurlarını düzenli olarak güncellemek için Laravel Scheduler kullanımı.
Kurulum
Projenin çalışması için aşağıdaki adımları izleyin:

1. Depoyu Klonlayın
bash
Kodu kopyala
git clone https://github.com/kullanici_adiniz/proje_adi.git
cd proje_adi
2. Gerekli Bağımlılıkları Yükleyin
bash
Kodu kopyala
composer install
3. Çevresel Değişkenleri Ayarlayın
.env dosyanızı oluşturun ve veritabanı ayarlarını yapın:

bash
Kodu kopyala
cp .env.example .env
php artisan key:generate
.env dosyasında aşağıdaki ayarları yapın:

plaintext
Kodu kopyala
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=veritabani_adi
DB_USERNAME=kullanici_adi
DB_PASSWORD=sifre
4. Veritabanı Migrasyonlarını Çalıştırın
bash
Kodu kopyala
php artisan migrate
5. Projeyi Çalıştırın
bash
Kodu kopyala
php artisan serve
6. TCMB Döviz Kurlarını Çekme
Döviz kurlarını çekmek için aşağıdaki komutu çalıştırın:

bash
Kodu kopyala
php artisan tcmb:fetch-rates
7. Planlanmış Görev Ayarı (Opsiyonel)
Döviz kurlarını düzenli olarak çekmek için App\Console\Kernel.php dosyasına gerekli cron işini ekleyin. Örneğin, günlük olarak kur çekmek için:

php
Kodu kopyala
$schedule->command('tcmb:fetch-rates')->daily();
Daha sonra sunucunuzda crontab ayarını yapmayı unutmayın:

bash
Kodu kopyala
* * * * * php /path/to/your/project/artisan schedule:run >> /dev/null 2>&1
Kullanım
Döviz kurlarını çekmek ve veritabanına kaydetmek için:

bash
Kodu kopyala
php artisan tcmb:fetch-rates
Bu komut, TCMB'nin sağladığı XML servisinden döviz kurlarını çekip veritabanınıza kaydeder.
