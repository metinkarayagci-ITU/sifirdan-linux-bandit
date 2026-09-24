# 00 · Uzak depoyu klonlamak

[Başlangıç](../README.md) · [Part 6 içindekiler](README.md)

**Hedef:** `bandit28`'in parolası bir **Git deposunda** duruyor. Depo, `ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo` adresinde; `bandit27-git` kullanıcısının parolası, `bandit27`'nin parolasıyla aynı. Bu part boyunca depoyu **kendi makinemize** klonlayıp içinde arayacağız.

## Neden kendi makinemizde?

OverTheWire'ın yönergesi net: klonlamayı Bandit sunucusunda değil, **kendi bilgisayarında** yap (bunun için yerelde `git` kurulu olmalı). Kendi terminalimizde (WSL/Kali) çalışıp depoyu bir geçici klasöre indiririz:

```
$ cd /tmp
$ git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
Cloning into 'repo'...
bandit27-git@bandit.labs.overthewire.org's password:  ← bandit27'nin parolası
$ cd repo
$ ls
README
$ cat README
The password to the next level is: ‹bandit28 parolası›
```

`git clone <adres>`, uzak depoyu tüm geçmişiyle birlikte yerele kopyalar. Parola sorulunca `bandit27`'nin parolasını gireriz (SSH parola girişinde olduğu gibi ekranda görünmez). Bu ilk depoda parola doğrudan `README` içinde.

## Perde arkası

Git, yazılım geliştirmenin merkezindeki **sürüm kontrol** sistemidir; bir projenin bütün geçmişini saklar. Bir depoyu klonlamak sadece "son hâli" indirmek değildir — **tüm tarihçeyi** getirir. Bu part'ın bütün fikri bu ayrıntıda gizli: bir deponun görünen son hâlinde bir şey olmasa bile, geçmişinde, dallarında ya da etiketlerinde saklı kalmış olabilir. İlk adımda parola apaçık ortada; sonraki adımlarda onu geçmişin içinde aramayı öğreneceğiz.

> **Faydalı olabilir:** [Bandit Level 28](https://overthewire.org/wargames/bandit/bandit28.html).

<!-- part6-altnav -->

---

[Part 6 içindekiler](README.md) · [01 · Geçmişe bakmak](01-gecmise-bakmak.md) →
