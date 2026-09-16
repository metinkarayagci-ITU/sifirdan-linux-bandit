# 02 · Adı `-` olan dosya

[Başlangıç](../README.md) · [Part 1 içindekiler](README.md)

**Hedef:** `bandit2`'nin parolası, adı yalnızca tek bir tire (`-`) olan bir dosyada. Part 0'da tire ile başlayan adların neden sorun çıkardığını görmüştük ([06 · Dosya adları ve türleri](../part-0/06-dosya-adlari-ve-turleri.md)); şimdi bunu ilk kez gerçek bir dosyada aşacağız.

## Sorun

```
$ ls
-
```

Dosya orada. Ama doğrudan okumaya çalışırsak:

```
$ cat -
```

Komut **hiçbir şey yapmadan bekler.** Çünkü birçok komut için tek başına `-`, bir dosya adı değil "standart girdiden (stdin) oku" anlamına gelir; `cat` klavyeden veri beklemeye başlar (çıkmak için Ctrl+C).

## Çözüm

Shell'e bunun bir dosya adı olduğunu, tire ile başlayan bir seçenek olmadığını söylememiz gerekir. Dosyanın önüne `./` ekleriz:

```
$ cat ./-
PAROLA_BURADA
```

`./` "bulunduğumuz dizindeki" demektir; `./-` artık tire ile başlamadığı için seçenek sanılmaz. Aynı işi girdi yönlendirmesiyle de yapabiliriz:

```
$ cat < -
PAROLA_BURADA
```

Burada dosyayı `cat`'e argüman olarak hiç vermeyiz; `<` ile dosyanın içeriğini doğrudan stdin'e bağlarız (Part 0 · [05 · Akışlar, pipe ve yönlendirme](../part-0/05-akislar-pipe-yonlendirme.md)). Bulduğumuz parolayla `bandit2`'ye geçeriz.

> **Faydalı olabilir:** [Bandit Level 2](https://overthewire.org/wargames/bandit/bandit2.html).

<!-- part1-altnav -->

---

← [01 · readme: ilk parolayı okumak](01-readme-dosyasi.md) · [Part 1 içindekiler](README.md) · [03 · Adında boşluk olan dosya](03-bosluklu-dosya-adi.md) →
