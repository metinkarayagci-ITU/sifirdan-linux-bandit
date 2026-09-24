# 04 · Depoya dosya itmek

[Başlangıç](../README.md) · [Part 6 içindekiler](README.md)

**Hedef:** `bandit32`'nin parolası. Şimdiye kadar hep depodan **okuduk**; bu kez depoya bir dosya **yazmamız** (push) gerekiyor. `bandit31-git` deposunun `README.md`'si görevi açıkça söylüyor: `master` dalına, içeriği `May I come in?` olan `key.txt` adlı bir dosya it.

## Görevi okumak

```
$ git clone ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo
$ cd repo
$ cat README.md
This time your task is to push a file to the remote repository.
Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

Bir de gizli bir engel var: depoda `.gitignore` dosyası `*.txt` içeriyor; yani Git, `.txt` uzantılı dosyaları **varsayılan olarak yok sayar.**

```
$ cat .gitignore
*.txt
```

## Dosyayı oluşturup itmek

Dosyayı yaratır, ama `.gitignore`'u aşmak için `git add`'i `-f` (*force*) ile çağırırız; sonra commit'leyip push ederiz:

```
$ echo 'May I come in?' > key.txt
$ git add -f key.txt
$ git commit -m "key"
$ git push origin master
...
remote: Well done! Here is the password for the next level:
remote: ‹bandit32 parolası›
```

Push tamamlanınca sunucunun kancası (hook) doğru dosyayı görür ve yanıt olarak `bandit32`'nin parolasını döner.

## Perde arkası

Bu adımda Git'in okuma dışındaki tarafını gördük: `add` → `commit` → `push` döngüsü, günlük geliştirmenin belkemiğidir. İki öğretici ayrıntı var: (1) `git push`, yerel değişiklikleri uzak depoya gönderir ve burada sunucu tarafındaki bir **kanca** (hook) o push'a tepki verir — otomasyonun yaygın bir kalıbı; (2) `.gitignore` bir dosyayı yok saydığında `git add -f` ile zorlamak gerekir. "Neden eklenmiyor?" sorusunun cevabı çoğu zaman `.gitignore`'dur; bunu bilmek çok zaman kazandırır.

> **Faydalı olabilir:** [Bandit Level 32](https://overthewire.org/wargames/bandit/bandit32.html).

<!-- part6-altnav -->

---

← [03 · Etiketlerde saklı](03-etiketlerde-sakli.md) · [Part 6 içindekiler](README.md) · [05 · Büyük harfe çeviren kabuk](05-buyuk-harfe-ceviren-kabuk.md) →
