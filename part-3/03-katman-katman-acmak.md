# 03 · Katman katman açmak

[Başlangıç](../README.md) · [Part 3 içindekiler](README.md)

**Hedef:** `bandit13`'ün parolası `data.txt` içinde, ama dosya **defalarca sıkıştırılmış** bir dosyanın hexdump'ı (onaltılık dökümü). Yani önce dökümü geri ikili dosyaya çevirmemiz, sonra katman katman açmamız gerekiyor. Bu, serinin ilk gerçekten çok adımlı bulmacası.

## Önce temiz bir çalışma alanı

Bu adımda birçok ara dosya üreteceğiz; ev dizinini kirletmemek için `/tmp` altında geçici bir klasör açarız (Bandit'in kendi önerisi de budur):

```
$ mkdir /tmp/calisma_a1b2 && cd /tmp/calisma_a1b2
$ cp ~/data.txt .
```

## Dökümü geri çevirmek

`data.txt`, `xxd` ile üretilmiş bir onaltılık dökümdür. `xxd -r` (*reverse*) bunu tekrar ikili dosyaya çevirir:

```
$ xxd -r data.txt > veri
$ file veri
veri: gzip compressed data, ...
```

## Türü sor, uygun araçla aç, tekrarla

Buradan sonrası bir döngü: her adımda `file` ile türe bak, uygun araçla aç, çıkan dosyaya yine `file` uygula. Sıkıştırma türleri değişir (gzip, bzip2, tar):

```
$ file veri          → gzip  → mv veri veri.gz;  gunzip veri.gz
$ file veri          → bzip2 → mv veri veri.bz2; bunzip2 veri.bz2
$ file veri          → gzip  → ...
$ file veri          → POSIX tar archive → tar xf veri
$ file veri          → bzip2 → ...
$ file veri          → POSIX tar archive → tar xf veri
$ file veri          → gzip  → ...
$ file veri          → ASCII text
$ cat veri
The password is ‹bandit13 parolası›
```

Her tür kendi aracıyla açılır: `gunzip` (gzip), `bunzip2` (bzip2), `tar xf` (tar arşivi). Sekiz-dokuz katman sonra `file` nihayet `ASCII text` dediğinde parolaya ulaşırız.

## Perde arkası

Buradaki fikir tek bir komut değil, bir **yöntem**: "ne olduğunu bilmiyorsan, önce `file` ile sor, sonra uygun araçla bir katman aç, sonra tekrar sor." Bu döngü, bilinmeyen bir dosyayı çözerken körlemesine deneme yapmaktan çok daha hızlıdır. Ayrıca `/tmp` altında geçici klasörle çalışmak, dağınık işleri temiz tutmanın standart alışkanlığıdır. (Tekrarlı türleri gözünle takip etmek istersen `file` çıktısını her adımda okumak yeterli; ismi tahmin edilmesin diye `mktemp -d` ile rastgele klasör de kullanılabilir.)

Bulduğumuz parolayla `bandit13`'e geçeriz.

> **Faydalı olabilir:** [Bandit Level 13](https://overthewire.org/wargames/bandit/bandit13.html).

<!-- part3-altnav -->

---

← [02 · 13 harf kaydırmak (ROT13)](02-rot13.md) · [Part 3 içindekiler](README.md) · [04 · Parola yerine anahtar](04-parola-yerine-anahtar.md) →
