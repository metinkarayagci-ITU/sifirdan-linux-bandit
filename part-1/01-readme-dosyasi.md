# 01 · readme: ilk parolayı okumak

[Başlangıç](../README.md) · [Part 1 içindekiler](README.md)

**Hedef:** `bandit1`'in parolası, `bandit0`'ın ev dizininde `readme` adlı bir dosyada duruyor. Onu okuyup bir sonraki seviyeye geçeceğiz.

## Önce elimizde ne var?

Bir yere bağlandığımızda ilk refleksimiz "elimde ne var?" diye bakmaktır (Part 0'daki [düşünce döngüsü](../part-0/README.md)). Ev dizinini listeleriz:

```
$ ls
readme
```

Tek bir dosya var: `readme`. İçeriğini `cat` ile okuruz:

```
$ cat readme
PAROLA_BURADA
```

Çıktıdaki `PAROLA_BURADA`, gerçek oturumda 32 karakterlik bir paroladır. Onu `bandit1`'e bağlanmak için kullanırız:

```
$ ssh bandit1@bandit.labs.overthewire.org -p 2220
```

## Perde arkası

`cat` dosyayı bir editör penceresinde açmaz; içeriğini okuyup terminale basar (Part 0 · [04 · Dosya içeriğini okumak](../part-0/04-dosya-icerigini-okumak.md)). Küçük bir dosyanın içine hızlıca bakmanın en kolay yolu budur.

> **Faydalı olabilir:** Bandit her seviyede işe yarayabilecek komutları kendi sayfasında listeler (`ls`, `cd`, `cat`, `file`, `du`, `find`): [Bandit Level 1](https://overthewire.org/wargames/bandit/bandit1.html).

<!-- part1-altnav -->

---

← [00 · Sunucuya SSH ile bağlanmak](00-ssh-ile-baglanma.md) · [Part 1 içindekiler](README.md) · [02 · Adı `-` olan dosya](02-tire-ile-baslayan-dosya.md) →
