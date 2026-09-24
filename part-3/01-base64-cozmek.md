# 01 · Base64 çözmek

[Başlangıç](../README.md) · [Part 3 içindekiler](README.md)

**Hedef:** `bandit11`'in parolası `data.txt` içinde, ama bu kez veri **Base64** ile kodlanmış. Base64 bir şifreleme değildir — sadece ikili veriyi düz metin karakterleriyle taşımak için kullanılan tersine çevrilebilir bir kodlamadır.

## Kodlanmış veriyi tanımak

```
$ cat data.txt
‹Base64 kodlu satır›
```

Sonu `=` ya da `==` ile biten, yalnızca harf-rakam-`+`-`/` içeren bu görünüm Base64'ün tipik imzasıdır. Çözmek için `base64` komutunun `-d` (*decode*) seçeneğini kullanırız:

```
$ base64 -d data.txt
The password is ‹bandit11 parolası›
```

Kodlama açılınca cümle okunur hâle gelir ve parola içinde görünür.

## Perde arkası

Base64'ü "şifre" ile karıştırmamak önemli: bir anahtar gerektirmez, herkes çözebilir. Amacı gizlemek değil, e-posta ekleri, veri URL'leri ya da HTTP başlıkları gibi yalnız metin kabul eden kanallardan ikili veriyi güvenle **geçirmektir.** Güvenlikte sık karşına çıkar; bir jetonun (token) ya da yapılandırmanın "şifreli" sanılıp aslında sadece Base64 olduğunu tanımak, ilk bakışta çözülen birçok bulmacanın anahtarıdır. `=` ile biten metin gördüğünde ilk denenecek şey `base64 -d`.

> **Faydalı olabilir:** [Bandit Level 11](https://overthewire.org/wargames/bandit/bandit11.html).

<!-- part3-altnav -->

---

← [00 · Görünür metni ayıklamak](00-gorunur-metni-ayiklamak.md) · [Part 3 içindekiler](README.md) · [02 · 13 harf kaydırmak (ROT13)](02-rot13.md) →
