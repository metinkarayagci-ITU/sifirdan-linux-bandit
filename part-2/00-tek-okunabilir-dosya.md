# 00 · Tek okunabilir dosya

[Başlangıç](../README.md) · [Part 2 içindekiler](README.md)

**Hedef:** `bandit5`'in parolası, `inhere` dizinindeki dosyalardan yalnızca **insan tarafından okunabilir** olanın içinde. Part 1'de gizli tek bir dosyayı bulmuştuk; burada karışıklık artıyor — birden çok dosya var ve hangisinin işe yaradığını *türüne* bakarak ayırmamız gerekiyor.

## Önce ortama bakalım

Her seviyede olduğu gibi ilk refleks aynı: elimizde ne var?

```
$ ls
inhere
$ cd inhere
$ ls
-file00  -file01  -file02  -file03  -file04
-file05  -file06  -file07  -file08  -file09
```

On dosya, hepsinin adı tire ile başlıyor. Part 1'de öğrendiğimiz gibi (`[02 · Adı - olan dosya](../part-1/02-tire-ile-baslayan-dosya.md)`), bu adları komuta verirken başlarına `./` koymamız gerekecek.

## "Okunabilir" olan hangisi?

Dosyaların çoğu ekrana basınca anlamsız karakter yığını verir; parola ise düz metindir. Tek tek açmak yerine, her dosyanın **ne tür veri içerdiğini** `file` komutuna sorarız (Part 0 · [06 · Dosya adları ve türleri](../part-0/06-dosya-adlari-ve-turleri.md)):

```
$ file ./*
./-file00: data
./-file01: data
./-file02: OpenPGP Secret Key
./-file03: data
./-file04: data
./-file05: data
./-file06: Non-ISO extended-ASCII text, with NEL line terminators
./-file07: ASCII text
./-file08: data
./-file09: data
```

`./*` kabuğun bütün dosya adlarını komuta yollaması demektir; başındaki `./` sayesinde tire ile başlayan adlar da seçenek sanılmaz. Çıktıda aradığımız işaret açık: **`ASCII text`** yalnızca `-file07`'de var. Ötekiler `data` (ham ikili) ya da başka biçimler.

```
$ cat ./-file07
‹bandit5 parolası›
```

## Perde arkası

`file`, bir dosyanın adına ya da uzantısına değil, **içindeki ilk baytlara** (sihirli sayı — *magic number*) bakarak tür tahmini yapar. Bu yüzden uzantısız dosyalarda bile işe yarar ve güvenlikte "bu dosya gerçekten iddia ettiği şey mi?" sorusunun ilk aracıdır. Bulduğumuz parolayla `bandit5`'e geçeriz.

> **Faydalı olabilir:** [Bandit Level 5](https://overthewire.org/wargames/bandit/bandit5.html).

<!-- part2-altnav -->

---

[Part 2 içindekiler](README.md) · [01 · Boyut ve türe göre aramak](01-boyut-ve-ture-gore-aramak.md) →
