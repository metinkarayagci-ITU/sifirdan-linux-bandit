# 01 · Adı hesaplanan dosya

[Başlangıç](../README.md) · [Part 5 içindekiler](README.md)

**Hedef:** `bandit23`'ün parolası yine bir cron job tarafından `/tmp` altına yazılıyor — ama bu kez dosyanın adı sabit değil, betik onu **hesaplayarak** üretiyor. Betiği okuyup aynı hesabı biz de yapmalıyız.

## Betiği okumak

Bir önceki adımdaki gibi cron tanımından betiğin yolunu bulup okuruz:

```
$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash
myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

Betiği satır satır okuyalım:

- `myname=$(whoami)` → betik hangi kullanıcı olarak çalışıyorsa onun adı. Cron bunu **bandit23** olarak çalıştırır, yani `myname` = `bandit23`.
- `mytarget=...` → `I am user bandit23` metninin **MD5 özetini** alır, ilk alanı (özet) kalır. İşte hedef dosyanın adı bu.
- Son satır → `bandit23`'ün parolasını `/tmp/$mytarget` dosyasına yazar.

## Aynı hesabı yapmak

Dosyanın adını öğrenmek için betiğin yaptığı hesabı **elle** tekrarlarız. Dikkat: betik `bandit23` olarak çalıştığı için metin `I am user bandit23` olmalı (biz `bandit22`'yiz ama hedef `bandit23`):

```
$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
‹hesaplanan dosya adı›
$ cat /tmp/‹hesaplanan dosya adı›
‹bandit23 parolası›
```

## Perde arkası

Buradaki asıl beceri, **bir betiği okuyup ne yaptığını çözebilmek** ve onun bir parçasını kendin yeniden üretmek. Betiğin dosya adını "gizlediği" düşünülebilir, ama gizlilik bir hesap gizli olduğu için değil, sadece o hesabı yapmadığın için var; hesabı gördüğün an sır kalmıyor. Bu, "kod okuma" becerisinin ilk somut sınavı — ki güvenlikte belki de en değerli beceridir. Dikkat edilecek incelik: betik hangi kullanıcı olarak çalışıyor? Adı ona göre hesapla.

> **Faydalı olabilir:** [Bandit Level 23](https://overthewire.org/wargames/bandit/bandit23.html).

<!-- part5-altnav -->

---

← [00 · Zamanlanmış görev okumak](00-zamanlanmis-gorev-okumak.md) · [Part 5 içindekiler](README.md) · [02 · Kendi betiğini koşturmak](02-kendi-betigini-kosturmak.md) →
