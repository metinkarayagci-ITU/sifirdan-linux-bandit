# 01 · Terminal, shell ve komut yapısı

[Başlangıç](../README.md) · [Part 0 içindekiler](README.md)

## Terminal neden?

Linux kullanırken bir noktadan sonra grafik arayüz yeterli gelmemeye başlıyor. Dosyaları tek tek açmak, klasörler arasında tıklayarak dolaşmak ve her işlem için ayrı bir pencere kullanmak yerine terminal üzerinden çok daha doğrudan çalışabiliyoruz.

Terminal bir arayüzdür; shell ise yazdığımız komutları yorumlayan katmandır. Terminalde çalıştırdığımız programlar da bu ikisinden ayrı şeylerdir.

## Komut + seçenekler + argümanlar

```
ls -l /var/log
```

- `ls`, yapılacak işlemi belirler.
- `-l`, bu işlemin nasıl yapılacağını belirleyen bir seçenektir.
- `/var/log` ise komuta verilen argümandır. Burada işlemin uygulanacağı dizini gösterir.

Her komutta bu üç parçanın da bulunması gerekmez: `pwd` tek başına yeterlidir. Bazen de tek bir komuta birden fazla seçenek veya argüman verebiliriz. Buradaki asıl amaç sözdizimini ezberlemek değil, bir komut gördüğümüzde parçalarını okuyabilmektir.

## Kısa ve uzun seçenekler

Birçok seçeneğin iki yazılışı vardır: tek tireli kısa biçim ve iki tireli, okunur uzun biçim.

```
ls -a        → kısa biçim
ls --all     → aynı seçeneğin uzun biçimi
```

İkisinin çıktısı aynıdır. Kısa seçenekler birleştirilebilir (`ls -la`); uzun seçenekler birleştirilemez, her biri ayrı yazılır.

## Birden çok argüman

```
ls /tmp /etc/ssh
```

`ls` her argümanı ayrı ayrı listeler ve her listenin başına dizinin adını yazar:

```
/etc/ssh:
moduli
ssh_config
ssh_config.d
sshd_config
sshd_config.d
```

(Çıktının `/tmp:` kısmı sistemden sisteme değişir.)

## Seçenek her zaman argümandan önce mi?

Genel alışkanlık seçeneği önce yazmaktır: `ssh -p 2222 kullanici@sunucu`. Ancak birçok komut seçeneği argümandan sonra da kabul eder; örneğin `ssh kullanici@sunucu -p 2222` da çalışır. Başka kaynaklarda iki yazılışı da görürsek şaşırmayalım.

## Klavye kısayolları

```
Tab        → komutu / dosya adını tamamlar (iki kez basınca seçenekleri listeler)
↑ / ↓      → önceki komutlar arasında gezinir
Ctrl+C     → çalışan komutu durdurur
Ctrl+L     → ekranı temizler
Ctrl+A     → satırın başına gider
Ctrl+E     → satırın sonuna gider
history    → daha önce yazdığımız komutları listeler
```

<!-- part0-altnav -->

---

← [00 · Ortam kurulumu](00-ortam-kurulumu.md) · [Part 0 içindekiler](README.md) · [02 · Dosya sistemi ve gezinme](02-dosya-sistemi-ve-gezinme.md) →
