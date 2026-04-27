<p align="center">
    <img src="doc/demo/logo.png" width="80px" />
    <h1 align="center">Cloud Mail</h1>
    <p align="center">Cloudflare Workers üzerinde çalışmak üzere tasarlanmış basit, duyarlı bir e-posta hizmeti 🎉</p> 
    <p align="center">
       <a href="/README-en.md" style="margin-left: 5px">Türkçe</a> | İngilizce
    </p>
    <p align="center">
        <a href="https://github.com/maillab/cloud-mail/tree/main?tab=MIT-1-ov-file" target="_blank" >
            <img src="https://img.shields.io/badge/license-MIT-green" />
        </a>    
        <a href="https://github.com/maillab/cloud-mail/releases" target="_blank" >
            <img src="https://img.shields.io/github/v/release/maillab/cloud-mail" alt="releases" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/issues" >
            <img src="https://img.shields.io/github/issues/maillab/cloud-mail" alt="issues" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/stargazers" target="_blank">
            <img src="https://img.shields.io/github/stars/maillab/cloud-mail" alt="stargazers" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/forks" target="_blank" >
            <img src="https://img.shields.io/github/forks/maillab/cloud-mail" alt="forks" />
        </a>
    </p>
    <p align="center">
        <a href="https://trendshift.io/repositories/14418" target="_blank" >
            <img src="https://trendshift.io/api/badge/repositories/14418" alt="trendshift" >
        </a>
    </p>
</p>

## Açıklama
Sadece tek bir alan adı ile büyük e-posta platformlarına benzer şekilde birden fazla farklı e-posta adresi oluşturabilirsiniz. Bu proje, sunucu maliyetlerini düşürmek ve kendi e-posta hizmetinizi oluşturmak için Cloudflare Workers üzerinde yayına alınabilir.

## Proje Önizlemesi

- [Canlı Demo](https://skymail.ink)<br>
- [Kurulum Kılavuzu](https://doc.skymail.ink/en/)<br>


| ![](/doc/demo/demo1.png) | ![](/doc/demo/demo2.png) |
|--------------------------|--------------------------|
| ![](/doc/demo/demo3.png) | ![](/doc/demo/demo4.png) |

## Özellikler

- **💰 Düşük Maliyetli Kullanım**: Sunucu gerektirmez — maliyetleri azaltmak için Cloudflare Workers'a kurun.

- **💻 Duyarlı Tasarım**: Hem masaüstü hem de çoğu mobil tarayıcıya otomatik olarak uyum sağlar.

- **📧 E-posta Gönderimi**: Toplu e-posta gönderimini ve ekleri destekleyen Resend ile entegredir.

- **🛡️ Yönetici Özellikleri**: RBAC tabanlı erişim kontrolü ile kullanıcı ve e-posta yönetimi için yönetici kontrolleri.

- **📦 Ek Desteği**: R2 nesne depolama aracılığıyla saklanan ve indirilen ekleri gönderip alın.

- **🔔 E-posta Yönlendirme**: Alınan e-postaları Telegram botlarına veya diğer e-posta sağlayıcılarına yönlendirin.

- **📡 Açık API**: API aracılığıyla toplu kullanıcı oluşturmayı ve çok koşullu e-posta sorgularını destekler.

- **📈 Veri Görselleştirme**: Kullanıcı e-posta büyümesi dahil sistem verilerini görselleştirmek için ECharts kullanın.

- **🎨 Kişiselleştirme**: Web sitesi başlığını, giriş arka planını ve şeffaflığı özelleştirin.

- **🤖 CAPTCHA**: Otomatik kaydı önlemek için Turnstile CAPTCHA ile entegre edilmiştir.

- **📜 Daha Fazla Özellik**: Geliştirilme aşamasında...

## Teknoloji Yığını

- **Platform**: [Cloudflare Workers](https://developers.cloudflare.com/workers/)

- **Web Framework**: [Hono](https://hono.dev/)

- **ORM**: [Drizzle](https://orm.drizzle.team/)

- **Frontend Framework**: [Vue3](https://vuejs.org/)

- **UI Framework**: [Element Plus](https://element-plus.org/)

- **E-posta Hizmeti**: [Resend](https://resend.com/)

- **Önbellek**: [Cloudflare KV](https://developers.cloudflare.com/kv/)

- **Veritabanı**: [Cloudflare D1](https://developers.cloudflare.com/d1/)

- **Dosya Depolama**: [Cloudflare R2](https://developers.cloudflare.com/r2/)

## Proje Yapısı

```
cloud-mail
├── mail-worker                    # Backend worker projesi
│   ├── src

│   │   ├── api                     # API katmanı
│   │   ├── const                   # Proje sabitleri
│   │   ├── dao                  # Veri erişim katmanı
│   │   ├── email                 # E-posta işleme ve yönetimi
│   │   ├── entity                 # Veritabanı varlıkları
│   │   ├── error                 # Özel istisnalar
│   │   ├── hono                 # Web framework, middleware, hata yönetimi
│   │   ├── i18n                 # Uluslararasılaştırma
│   │   ├── init                 # Veritabanı ve önbellek başlatma
│   │   ├── model                 # Yanıt veri modelleri
│   │   ├── security             # Kimlik doğrulama ve yetkilendirme
│   │   ├── service                 # İş mantığı katmanı
│   │   ├── template             # Mesaj şablonları
│   │   ├── utils                 # Yardımcı fonksiyonlar
│   │   └── index.js             # Giriş noktası
│   ├── package.json             # Proje bağımlılıkları
│   └── wrangler.toml             # Proje yapılandırması
│
├─ mail-vue                        # Frontend Vue projesi
│   ├── src
│   │   ├── axios                  # Axios yapılandırması
│   │   ├── components             # Özel bileşenler
│   │   ├── echarts                 # ECharts entegrasyonu
│   │   ├── i18n                 # Uluslararasılaştırma
│   │   ├── init                 # Başlangıç başlatma işlemleri
│   │   ├── layout                 # Ana düzen bileşenleri
│   │   ├── perm                 # İzinler ve erişim kontrolü
│   │   ├── request                 # API istek katmanı
│   │   ├── router                 # Router yapılandırması
│   │   ├── store                 # Global durum yönetimi
│   │   ├── utils                 # Yardımcı fonksiyonlar
│   │   ├── views                 # Sayfa bileşenleri
│   │   ├── app.vue                 # Kök bileşen
│   │   ├── main.js                 # Giriş JS dosyası
│   │   └── style.css             # Global stiller
│   ├── package.json             # Proje bağımlılıkları
└── └── env.release                 # Ortam yapılandırması


## Destek

<a href="https://doc.skymail.ink/support.html">
<img width="170px" src="./doc/images/support.png" alt="">
</a>

## Lisans

Bu proje [MIT](LICENSE) lisansı altında lisanslanmıştır.

## İletişim

[Telegram](https://t.me/cloud_mail_tg)