# 00 · Görünür metni ayıklamak

[Başlangıç](../README.md) · [Part 3 içindekiler](README.md)

**Hedef:** `bandit10`'un parolası `data.txt` içinde, ama dosya artık düz metin değil — çoğu **okunamaz ikili veri**, parola ise aralarındaki birkaç okunabilir satırdan biri ve önünde birkaç `=` karakteri var.

## İkili dosyayı doğrudan okumak neden olmaz?

```
$ file data.txt
data.txt: data
```

`file` "data" diyor: yani ham ikili. `cat` ile bastırırsak terminal anlamsız karakterlerle dolar, hatta bozulabilir. İhtiyacımız olan şey, bu ikili yığının **içindeki okunabilir metin parçalarını** çekip çıkarmak. Bunu `strings` yapar: bir dosyadaki yazdırılabilir karakter dizilerini listeler.

## strings ve grep birlikte

```
$ strings data.txt | grep "=="
========== the
========== password
========== is
========== ‹bandit10 parolası›
```

- `strings data.txt` → ikili yığından okunabilir dizileri süzer,
- `| grep "=="` → bunların içinden `=` işareti taşıyanları bırakır (parolanın işareti buydu).

Çıktıdaki son satırda, `=` dizisinin ardından parola görünür.

## Perde arkası

`strings`, adli bilişimin (forensics) ilk araçlarından biridir: bir çalıştırılabilir dosyanın, bellek dökümünün ya da bilinmeyen bir dosyanın içinde gizli URL'ler, mesajlar veya parolalar aramak için kullanılır. "İkili görünüyor ama içinde metin de olabilir" sezgisi burada devreye girer. `grep` ile birleşince, gürültünün içinden aradığın kalıba tek adımda inersin.

> **Faydalı olabilir:** [Bandit Level 10](https://overthewire.org/wargames/bandit/bandit10.html).

<!-- part3-altnav -->

---

[Part 3 içindekiler](README.md) · [01 · Base64 çözmek](01-base64-cozmek.md) →
