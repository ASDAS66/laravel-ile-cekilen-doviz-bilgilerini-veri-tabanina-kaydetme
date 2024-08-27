#TCMB Döviz Kurları Laravel Projesi#

Bu proje, Türkiye Cumhuriyet Merkez Bankası'ndan (TCMB) güncel döviz kurlarını çekip, bu verileri veritabanına kaydetmek için geliştirilmiş bir Laravel uygulamasıdır.

Özellikler
##Güncel Döviz Kurları Çekme: TCMB'nin sağladığı XML servisinden döviz kurlarını çekme.
##Veritabanına Kaydetme: Çekilen döviz kurlarını veritabanına kaydetme.
##Planlanmış Görev: Döviz kurlarını düzenli olarak güncellemek için Laravel Scheduler kullanımı.
Kurulum
##Projenin çalışması için aşağıdaki adımları izleyin:

###1. Depoyu Klonlayın
<code>
git clone https://github.com/kullanici_adiniz/proje_adi.git
cd proje_adi
</code>
###3. Gerekli Bağımlılıkları Yükleyin
<code>
composer install</code>
###4. Çevresel Değişkenleri Ayarlayın
.env dosyanızı oluşturun ve veritabanı ayarlarını yapın:
<code>
php artisan key:generate</code>

.env dosyasında aşağıdaki ayarları yapın:
<code>
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=veritabani_adi
DB_USERNAME=kullanici_adi
DB_PASSWORD=sifre</code>
###4. Veritabanı Migrasyonlarını Çalıştırın

<code>
php artisan migrate</code>code>
###5. Projeyi Çalıştırın
<code>php artisan serve</code>
###6. TCMB Döviz Kurlarını Çekme
Döviz kurlarını çekmek için aşağıdaki komutu çalıştırın:
<code>
php artisan tcmb:fetch-rates</code>
###7. Planlanmış Görev Ayarı (Opsiyonel)
Döviz kurlarını düzenli olarak çekmek için App\Console\Kernel.php dosyasına gerekli cron işini ekleyin. Örneğin, günlük olarak kur çekmek için:
<code>
$schedule->command('tcmb:fetch-rates')->daily();</code>
Daha sonra sunucunuzda crontab ayarını yapmayı unutmayın:
<code>
* * * * * php /path/to/your/project/artisan schedule:run >> /dev/null 2>&1</code>
Kullanım
Döviz kurlarını çekmek ve veritabanına kaydetmek için:
<code>
php artisan tcmb:fetch-rates</code>
Bu komut, TCMB'nin sağladığı XML servisinden döviz kurlarını çekip veritabanınıza kaydeder.
