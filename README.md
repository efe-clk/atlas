# Atlas

Birbirinden tamamen bağımsız statik web sitelerini ("atlasları") tek bir repoda toplayan ve GitHub Pages ile yayınlayan depo.

Yayın adresi: **https://efe-clk.github.io/atlas/**

## Atlaslar

| Atlas | Açıklama |
|---|---|
| [Arayüz Atlası](https://efe-clk.github.io/atlas/arayuz-atlasi/) | Yazılımların birbiriyle nasıl konuştuğunu (API'ler, protokoller, kimlik doğrulama) canlı akış şemalarıyla anlatan terim rehberi. |
| [Açık Kaynak Repo Atlası](https://efe-clk.github.io/atlas/acik-kaynak-repo-atlasi/) | Kod kalitesi, dokümantasyonu ya da topluluğuyla öne çıkan GitHub repolarının kategorilere ayrılmış, aranabilir dizini. |
| [Dijital Diller Atlası](https://efe-clk.github.io/atlas/dijital-diller-atlasi/) | Devre tanımlamadan SQL'e kadar bilgisayar dili ailelerini soyutlama katmanlarına göre alt türleri ve kod örnekleriyle haritalayan rehber. |

## Yapı

```
atlas/
├── index.html                  # tüm atlasları listeleyen ana sayfa
├── 404.html                    # hata sayfası
├── .nojekyll                   # GitHub Pages'te Jekyll işlemesini kapatır
├── README.md
├── LICENSE                     # CC BY 4.0
├── arayuz-atlasi/
│   └── index.html
├── acik-kaynak-repo-atlasi/
│   └── index.html
└── dijital-diller-atlasi/
    └── index.html
```

Bir atlas ek dosyaya ihtiyaç duyarsa bunları kendi klasöründeki `assets/` altına koyar.

## Yeni atlas ekleme

1. Kurallara uygun bir klasör adı seçin (ör. `veri-yapilari-atlasi`) ve klasörü oluşturun.
2. Sitenin HTML dosyasını bu klasöre `index.html` adıyla koyun. Görsel, font vb. ek dosyalar varsa klasörün içindeki `assets/` altına yerleştirin.
3. Aşağıdaki kurallara göre dosyayı gözden geçirin: mutlak yolları göreli yapın, `localStorage`/`sessionStorage` anahtarlarına klasör adını önek olarak ekleyin.
4. Kökteki `index.html` içinde `ATLASES` dizisine tek satır ekleyin:
   ```js
   { slug: "veri-yapilari-atlasi", title: "Veri Yapıları Atlası", desc: "Tek cümlelik açıklama." },
   ```
5. Bu README'deki atlas tablosuna bir satır ekleyin.
6. Yerelde test edin (aşağıya bakın), commit'leyip `main` dalına push'layın. GitHub Pages birkaç dakika içinde güncellenir.

## Kurallar

- **Bağımsızlık:** Her atlas kendi klasöründe kendi kendine yeter. Bir atlas başka bir atlasın klasöründeki dosyalara bağlanmaz. CDN'den yüklenen kütüphaneler ve fontlar serbesttir.
- **Klasör adlandırma:** Küçük harf, Türkçe karakter yok (`ç→c`, `ğ→g`, `ı→i`, `ö→o`, `ş→s`, `ü→u`), kelimeler tire ile ayrılır. Ör. "Açık Kaynak Repo Atlası" → `acik-kaynak-repo-atlasi`.
- **Göreli yollar:** Site `efe-clk.github.io/atlas/` alt yolunda çalışır. `/` ile başlayan yollar (`/assets/logo.png`) alan adının köküne gider ve kırılır; bunun yerine `./assets/logo.png` yazın. (Tek istisna `404.html`: Pages bu sayfayı her derinlikte sunduğu için ana sayfa linki `/atlas/` olarak yazılmıştır. Siteye özel bir domain bağlanıp site kökte çalışmaya başlarsa bu linki `/` yapın.)
- **Depolama anahtarları:** Tüm atlaslar aynı origin'i (`efe-clk.github.io`) paylaşır, yani `localStorage` ve `sessionStorage` ortaktır. Çakışmayı önlemek için her anahtara klasör adıyla önek ekleyin: `tema` → `arayuz-atlasi:tema`. Okuma ve yazma noktalarının hepsini aynı şekilde değiştirin.

## Yerelde test

Site `/atlas/` alt yolunda çalıştığı için sunucuyu reponun **bir üst dizininden** başlatın:

```sh
cd ..
python3 -m http.server 8000
```

Ardından http://localhost:8000/atlas/ adresini açın.

## Lisans

Bu repodaki içerik [Creative Commons Atıf 4.0 Uluslararası (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.tr) lisansıyla paylaşılmaktadır. Atıf vermek koşuluyla ticari amaçlar dahil kopyalayabilir, dağıtabilir ve değiştirebilirsiniz.

Atıf örneği: *"Atlas — Efe Çelik, https://github.com/efe-clk/atlas, CC BY 4.0"*

Lisansın tam metni: [LICENSE](LICENSE)
