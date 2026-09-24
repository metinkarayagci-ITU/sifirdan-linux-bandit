# 01 · Doğru portu bulmak

[Başlangıç](../README.md) · [Part 4 içindekiler](README.md)

**Hedef:** Bu seviye üç işi birleştiriyor. `bandit16`'nın parolasını, `localhost`'ta **31000–32000 arasındaki** bir porta göndereceğiz — ama önce (1) hangi portların açık olduğunu, (2) bunlardan hangisinin **SSL/TLS** konuştuğunu bulmamız gerekiyor. Doğru servis bize parola yerine bir **SSH anahtarı** verecek.

## Adım 1 — Açık portları taramak

Bin portu elle denemek yerine bir port tarayıcı kullanırız: `nmap`.

```
$ nmap -p31000-32000 localhost

PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown
```

- `-p31000-32000` → yalnız bu port aralığını tara.

Binlerce porttan yalnız beşi açık. Alan daraldı.

## Adım 2 — Hangisi SSL konuşuyor?

Beş portun bazıları düz TCP, bazıları SSL. Ayrımı `openssl s_client` ile yaparız: SSL konuşan porta bağlanınca bir TLS el sıkışması (handshake) ve sertifika görürüz; düz port ise anlamsız yanıt verir ya da el sıkışması başarısız olur. Denemede yalnız birkaç port düzgün TLS oturumu açar.

## Adım 3 — Parolayı gönder, anahtarı al

SSL konuşan doğru porta parolamızı göndeririz; servis bu kez bir metin değil, bir **özel SSH anahtarı** döner:

```
$ cat /etc/bandit_pass/bandit16 | openssl s_client -connect localhost:31790 -quiet
Correct!
-----BEGIN OPENSSH PRIVATE KEY-----
‹özel anahtar›
-----END OPENSSH PRIVATE KEY-----
```

Bu anahtarı bir dosyaya kaydeder (`/tmp` altında), izinlerini `chmod 600` ile daraltır ve Part 3'te öğrendiğimiz gibi `ssh -i` ile `bandit17`'ye gireriz:

```
$ ssh -i /tmp/bandit17.key bandit17@localhost -p 2220
```

![nmap açık portları bulur; doğru SSL portu anahtar döner](img/01-nmap.png)

## Perde arkası

Bu seviye, bir saldırının küçük bir provası gibidir: **keşif** (hangi portlar açık?), **parmak izi çıkarma** (bu port ne konuşuyor?), sonra **erişim** (doğru veriyi doğru servise gönder). `nmap` keşfin, `openssl s_client` parmak izinin standart araçlarıdır. Gerçek dünyada bir sisteme bakarken de sıralama aynıdır: önce ne açık, sonra ne konuşuyor, sonra nasıl konuşulur.

> **Faydalı olabilir:** [Bandit Level 17](https://overthewire.org/wargames/bandit/bandit17.html).

<!-- part4-altnav -->

---

← [00 · Şifreli bağlantı](00-sifreli-baglanti.md) · [Part 4 içindekiler](README.md) · [02 · İki dosyanın farkı](02-iki-dosyanin-farki.md) →
