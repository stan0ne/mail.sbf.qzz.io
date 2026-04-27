## GitHub Action ile Dağıtım

**GitHub Deposunu Yapılandırma**

1. Depoyu forklayın veya klonlayın: [https://github.com/eoao/cloud-mail](https://github.com/stan0ne/cloud-mail)
2. GitHub deponuzun Settings (Ayarlar) sekmesine gidin.
3. Settings → Secrets and variables → Actions → New repository secret yolunu izleyin.
4. Aşağıdaki Secret'ları ekleyin:

| Secret Adı              | Gerekli | Kullanım Amacı                                                  				|
| ----------------------- | :--: | -------------------------------------------------------------------------------- |
| `CLOUDFLARE_API_TOKEN`  |  ✅  | Cloudflare API Belirteci (Workers ve ilgili kaynaklar için izin gereklidir)    	|
| `CLOUDFLARE_ACCOUNT_ID` |  ✅  | Cloudflare Hesap ID'si                                    						|
| `D1_DATABASE_ID`        |  ✅  | D1 Veritabanınızın ID'si                                   						|
| `KV_NAMESPACE_ID`       |  ✅  | KV Namespace (İsim Alanı) ID'niz                                  				|
| `R2_BUCKET_NAME`        |  ✅  | R2 Bucket (Depolama Alanı) adınız                                   				|
| `DOMAIN`                |  ✅  | E-posta hizmeti için  alan adı (Örn: `["xx.xx"], çoklu için ,` kullanın)			|
| `ADMIN`                 |  ✅  | Yönetici e-posta adresiniz (Örn: admin@example.com)      						|
| `JWT_SECRET`            |  ✅  | JWT oluşturma ve doğrulama için kullanılacak rastgele uzun bir dize				|
| `INIT_URL`              |  ❌  | (İsteğe bağlı) Dağıtım sonrası veritabanını başlatmak için Worker URL'si			|

---

**Cloudflare API Belirteci Alınması**

1. [Cloudflare Dashboard](https://dash.cloudflare.com/profile/api-tokens) 'ni ziyaret edin.
2. Yeni bir API belirteci oluşturun.
3. "Edit Cloudflare Workers" şablonunu seçin ve aşağıdaki tabloya göre gerekli izinleri ekleyin.
   ![dc2e1dc8dcd217644759c46c6c705de1](https://i.miji.bid/2025/07/07/dc2e1dc8dcd217644759c46c6c705de1.png)
4. Belirteci kaydedin ve GitHub Secrets içindeki `CLOUDFLARE_API_TOKEN` alanına kopyalayın.

**Cloudflare Hesap ID'si Alınması**
1. Hesap ID'si, Cloudflare panelindeki hesap ayarlarında bulunabilir.
2. Bunu GitHub Secrets içindeki `CLOUDFLARE_ACCOUNT_ID` alanına kopyalayın.

**İş Akışını Çalıştırma**
1. Actions sayfasından iş akışını (workflow) manuel olarak çalıştırın; sonraki süreçte ana depo (upstream) ile her senkronizasyonda otomatik olarak Cloudflare Workers'a dağıtılacaktır. Eğer `INIT_URL` yapılandırılmadıysa, veritabanı ilklendirmesi için `https://proje-alan-adiniz/api/init/jwt_secret_kodunuz` adresini manuel olarak ziyaret etmeniz gerekir.
2. Ana depoyu otomatik senkronize etmek için bir bot kullanabilir veya manuel olarak Sync Upstream butonuna tıklayabilirsiniz.