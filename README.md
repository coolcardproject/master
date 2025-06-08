# 🚀 [Proje Adı]

[Projenizin bir cümlelik kısa ve etkileyici açıklaması. Örneğin: "Kullanıcıların fotoğraf koleksiyonlarını düzenlemesini sağlayan modern bir web uygulaması."]

![Proje Ekran Görüntüsü veya Logosu]([Buraya bir ekran görüntüsü linki ekleyebilirsin])

Bu proje, [Projenin çözdüğü temel problem veya amacı] amacıyla geliştirilmiştir. [Projenin hedef kitlesi] için tasarlanmıştır ve [kullanılan en önemli 2-3 teknoloji, örn: Next.js, Prisma, Tailwind CSS] ile oluşturulmuştur.

## ✨ Özellikler

* **[Özellik 1]:** [Özelliğin kısa açıklaması, örn: Kullanıcıların e-posta ve şifre ile kayıt olabilmesi.]
* **[Özellik 2]:** [Özelliğin kısa açıklaması, örn: Sınırsız sayıda fotoğraf albümü oluşturma.]
* **[Özellik 3]:** [Özelliğin kısa açıklaması, örn: Fotoğraflara etiket ekleyerek kolayca arama yapma.]
* **[Özellik 4]:** [Özelliğin kısa açıklaması, örn: Mobil uyumlu ve şık arayüz.]

## 🛠️ Kurulum

Projeyi kendi bilgisayarınızda çalıştırmak için aşağıdaki adımları izleyin:

1.  **Repository'yi klonlayın:**
    ```bash
    git clone [https://github.com/](https://github.com/)[kullanici-adin]/[proje-adin].git
    ```
2.  **Proje dizinine gidin:**
    ```bash
    cd [proje-adin]
    ```
3.  **Bağımlılıkları yükleyin:**
    ```bash
    pnpm install
    ```
4.  **Ortam değişkenlerini ayarlayın:**
    * `.env.example` dosyasını kopyalayıp `.env` adında yeni bir dosya oluşturun.
    * `.env` dosyasındaki gerekli alanları (veritabanı bağlantısı, API anahtarları vb.) doldurun.
    ```bash
    cp .env.example .env
    ```
5.  **Veritabanını hazırlayın:**
    ```bash
    pnpm run db:push # Veya projenizdeki ilgili komut
    ```
6.  **Geliştirme sunucusunu başlatın:**
    ```bash
    pnpm run dev
    ```

Uygulama artık `http://localhost:3000` adresinde çalışıyor olmalı.

Adım 2: Asla Ana Dala Dokunma: Branch (Dal) Stratejisi
Tek başına da olsan, en önemli kural budur. Tüm işi tek bir dalda (main) yapmak, arabanın motorunu araba çalışırken tamir etmeye benzer.

Ne yapacaksın?

Projenin iki ana, kutsal dalı olacak: main ve develop.
main Dalı: Bu dal, projenin canlıda çalışan, stabil, test edilmiş versiyonunu temsil eder. Buraya asla doğrudan kod yazılmaz. Sadece develop dalından gelen ve tamamen hazır olan kodlar buraya birleştirilir.
develop Dalı: Bu dal, projenin "bir sonraki versiyonu" dur. Yaptığın tüm işler önce burada toplanır. Geliştirme dünyan bu dal etrafında döner.
GitHub reposunu bilgisayarına klonladıktan sonra hemen develop dalını oluştur:
Bash

git checkout -b develop
git push -u origin develop
Bu ne için?

Bu yapı sayesinde, bir özellik üzerinde çalışırken projenin stabil versiyonunu (main) asla bozmazsın. develop dalı senin oyun alanın olur.
Adım 3: Her İş İçin Yeni Bir Sayfa: Feature Branch Döngüsü
Projene ekleyeceğin her bir özellik, düzelteceğin her bir hata için yeni bir dal açacaksın. Bu, yaptığın işleri birbirinden ayırmanı sağlar.

Ne yapacaksın? (İş Akışı)

Fikri Göreve Çevir: Yapacağın işi (örn: "Kullanıcı giriş sayfası yapılacak") GitHub'un Issues sekmesinde yeni bir "issue" (görev) olarak aç. Buna bir başlık ve açıklama yaz.
Dalı Aç: develop dalındayken, o göreve özel yeni bir dal aç. Dalın adını issue numarasıyla başlatmak en iyisidir:
Bash

git checkout develop
git pull # En güncel halini al
git checkout -b feature/1-login-page  # "1", issue'nun numarası
Kodunu Yaz: Artık bu yeni daldasın (feature/1-login-page). Tüm kodlama işini burada yap. Sık sık, küçük ve anlamlı "commit"ler yap (git commit -m "feat: login formu eklendi").
İşini Gönder: İşin bittiğinde, bu dalı GitHub'a gönder:
Bash

git push -u origin feature/1-login-page
Pull Request (PR) Aç: GitHub'a git. "Compare & pull request" butonuna basarak feature/1-login-page dalından develop dalına bir "Pull Request" (birleştirme isteği) aç. PR'ın açıklamasına Fixes #1 yazarsan, bu PR birleştiğinde GitHub o issue'yu otomatik olarak kapatır.
Bu ne için?

Bu döngü, yaptığın her işi izole ve yönetilebilir hale getirir. Bir özellikte sorun çıkarsa, sadece o dalı geri almak veya düzeltmek yeterli olur, tüm proje etkilenmez. Tarihçen tertemiz kalır.
Adım 4: Kendi Kendinin Patronu Ol: "Kendi Kendine Code Review"
Tek başına çalışsan bile Pull Request (PR) açmak çok değerlidir. PR, senin için bir kalite kontrol kapısıdır.

Ne yapacaksın?

PR'ı açtıktan sonra birleştirmeden önce "Files changed" sekmesine git.
Yazdığın tüm kodu baştan sona bir daha oku. Sanki başkasının kodunu inceliyormuş gibi bak. Hataları, unutulmuş console.log'ları veya daha iyi yazılabilecek yerleri fark edeceksin.
Her şey yolundaysa, "Merge pull request" butonuna basarak kodunu develop dalıyla birleştir.
Artık işi bittiği için o feature dalını silebilirsin.
Bu ne için?

Bu, hataları develop dalına girmeden yakalamak için son bir şanstır. Disiplin kazandırır ve kod kaliteni artırır.
Adım 5: Güvenlik Ağı: GitHub Actions ile Otomasyon 🛡️
Bu, işin "ileri seviye" kısmıdır. GitHub, kodunda otomatik kontroller yapabilir. Sen bir PR açtığında, GitHub senin için testleri ve kontrolleri çalıştırır.

Ne yapacaksın?
Projenin kök dizininde .github/workflows adında bir klasör oluştur.
İçine ci.yml adında bir dosya oluştur ve şuna benzer bir içerik ekle:
YAML

name: Continuous Integration

on:
  push:
    branches: [ develop ]
  pull_request:
    branches: [ develop ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: pnpm/action-setup@v2
        with:
          version: 10
      - name: Use Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '20.x'
          cache: 'pnpm'

      - name: Install dependencies
        run: pnpm install

      - name: Run Lint
        run: pnpm run lint

      - name: Run Tests
        run: pnpm run test

      - name: Run Build
        run: pnpm run build
Bu ne için?
Bu otomasyon, bir PR açtığında kodunun lint kurallarına uyup uymadığını, testleri geçip geçmediğini ve başarıyla derlenip derlenmediğini otomatik olarak kontrol eder. Eğer bir sorun varsa, PR'ı birleştirmeni engeller. Bu senin en büyük güvencen olacak.
Adım 6: Sürüm Çıkmak ve Etiketleme
Projenin develop dalı yeterince olgunlaştığında ve yeni bir sürüm yayınlamaya hazır olduğunda, bu işi resmiyete dökersin.

Ne yapacaksın?

develop dalından main dalına yeni bir Pull Request aç.
Bu PR'ı birleştirerek projenin stabil versiyonunu güncelle.
GitHub'da "Releases" sekmesine git ve "Create a new release" butonuna bas.
Bir etiket (tag) adı ver (örn: v1.0.0).
Bu sürümde yaptığın yenilikleri açıklama kısmına yaz ve yayınla.
Bu ne için?

Bu, projenin geçmişinde önemli dönüm noktaları oluşturur. Geriye dönüp baktığında v1.0.0'da tam olarak hangi kodun olduğunu net bir şekilde görebilirsin.

## 🤝 Katkıda Bulunma

Bu proje şu anda tek kişi tarafından geliştirilmektedir, ancak gelecekte katkıda bulunmak isterseniz lütfen "Issues" bölümünden bir görev açın.


