# 00 · Zamanlanmış görev okumak

[Başlangıç](../README.md) · [Part 5 içindekiler](README.md)

**Hedef:** `bandit22`'nin parolası bir dosyada, ama o dosyayı bir **zamanlanmış görev** (cron job) düzenli aralıklarla oluşturuyor. Yani parolayı bulmak için, önce sistemde hangi işin otomatik çalıştığını okumamız gerekiyor.

## cron nedir, yapılandırması nerede?

`cron`, komutları belirli zamanlarda otomatik çalıştıran bir zamanlayıcıdır. Sistem genelindeki cron tanımları `/etc/cron.d/` altında durur. Oraya bakarız:

```
$ ls /etc/cron.d/
... cronjob_bandit22 cronjob_bandit23 cronjob_bandit24 ...
$ cat /etc/cron.d/cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```

`* * * * *`, işin **her dakika** çalıştığı anlamına gelir; çalıştırdığı şey `/usr/bin/cronjob_bandit22.sh` betiği. Betiğin ne yaptığını okuruz:

```
$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/‹dosya adı›
cat /etc/bandit_pass/bandit22 > /tmp/‹dosya adı›
```

Betik, `bandit22`'nin parolasını `/tmp` altındaki belirli bir dosyaya yazıyor ve herkesin okuyabilmesi için iznini `644` yapıyor. Öyleyse o dosyayı okumamız yeter:

```
$ cat /tmp/‹dosya adı›
‹bandit22 parolası›
```

## Perde arkası

Bu seviyenin dersi, bir sistemde **otomatik çalışan işleri** incelemenin önemidir. Zamanlanmış görevler çoğu zaman gözden kaçar ama sistemin "arka planda ne yaptığını" anlatır — ve kötü yapılandırılmış bir cron job (örneğin bir parolayı herkesin okuyabileceği bir yere yazmak) doğrudan bir açığa dönüşür. Bir makineyi incelerken `/etc/cron.d/`, `/etc/crontab` ve kullanıcı crontab'larına bakmak rutin bir adımdır.

> **Faydalı olabilir:** [Bandit Level 22](https://overthewire.org/wargames/bandit/bandit22.html).

<!-- part5-altnav -->

---

[Part 5 içindekiler](README.md) · [01 · Adı hesaplanan dosya](01-adi-hesaplanan-dosya.md) →
