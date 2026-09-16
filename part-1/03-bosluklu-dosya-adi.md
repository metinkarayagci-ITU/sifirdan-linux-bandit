# 03 · Adında boşluk olan dosya

[Başlangıç](../README.md) · [Part 1 içindekiler](README.md)

**Hedef:** `bandit3`'ün parolası, adında boşluklar olan `spaces in this filename` adlı dosyada. Part 0'da boşluklu adları görmüştük ([06 · Dosya adları ve türleri](../part-0/06-dosya-adlari-ve-turleri.md)); uygulama zamanı.

## Sorun

```
$ ls
spaces in this filename
```

Bu tek bir dosya — ama adı dört kelimeden oluşuyor. Doğrudan `cat spaces in this filename` yazarsak shell bunu **dört ayrı dosya** (`spaces`, `in`, `this`, `filename`) sanır, çünkü boşluk argümanları birbirinden ayırır.

## Çözüm

Adı bir bütün olarak vermenin iki yolu var. Tırnak içine almak:

```
$ cat "spaces in this filename"
PAROLA_BURADA
```

Ya da her boşluğu `\` ile kaçışlamak:

```
$ cat spaces\ in\ this\ filename
PAROLA_BURADA
```

İkisi de aynı sonucu verir. Pratikte en kolayı **Tab ile tamamlamadır**: `cat spa` yazıp Tab'a basınca shell adı bizim yerimize, kaçışlarıyla birlikte doğru biçimde tamamlar.

> **Faydalı olabilir:** [Bandit Level 3](https://overthewire.org/wargames/bandit/bandit3.html).

<!-- part1-altnav -->

---

← [02 · Adı `-` olan dosya](02-tire-ile-baslayan-dosya.md) · [Part 1 içindekiler](README.md) · [04 · Gizli dosya](04-gizli-dosya.md) →
