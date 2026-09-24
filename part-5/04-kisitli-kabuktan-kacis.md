# 04 · Kısıtlı kabuktan kaçış

[Başlangıç](../README.md) · [Part 5 içindekiler](README.md)

**Hedef:** `bandit26`'ya girmek. `bandit25`'in ev dizininde `bandit26.sshkey` var; onunla giriş yapabiliriz. Ama bir sürpriz: `bandit26`'nın kabuğu `/bin/bash` değil; giriş yapar yapmaz bağlantı kapanıyor. Önce bu kabuğun ne olduğunu, sonra ondan **nasıl kaçılacağını** bulmalıyız.

## Kabuk neden kapanıyor?

`bandit26`'nın giriş kabuğunu `/etc/passwd`'den öğreniriz:

```
$ grep bandit26 /etc/passwd
bandit26:...:/home/bandit26:/usr/bin/showtext
$ cat /usr/bin/showtext
#!/bin/sh
export TERM=linux
exec more ~/text.txt
exit 0
```

Kabuk aslında bir betik: `more ~/text.txt` çalıştırıp çıkıyor. Yani `bandit26` olarak giriş yapınca bize kabuk değil, bir **sayfalayıcı** (pager, `more`) açılıyor ve dosya bitince oturum kapanıyor.

## more'u sayfalamaya zorlamak

`more`, gösterdiği metin ekrana **sığmıyorsa** kapanmaz — sayfalamaya durur ve bizden tuş bekler. İşte açık burada: terminal penceresini **çok küçük** yaparsak (`text.txt` bir kaç satırlık ASCII resim), `more` metnin tamamını gösteremez ve `--More--` diyerek bekler.

Bu bekleme anında `more`'un içinden `v` tuşuna basarız — bu, `more`'u `vi` düzenleyicisinde açar. Artık `vi` içindeyiz ve `vi`'den kabuk çağırabiliriz:

```
:set shell=/bin/bash
:shell
```

- `:set shell=/bin/bash` → `vi`'nin kullanacağı kabuğu bash yapar,
- `:shell` → o kabuğu açar.

Artık `bandit26` kimliğiyle gerçek bir bash kabuğundayız.

## Perde arkası

Bu, bir **kısıtlı kabuktan kaçış** (restricted shell escape) örneğidir — güvenlikte klasik bir konu. Fikir şu: sana tam bir kabuk yerine sınırlı bir program (burada `more`) verilmişse, o programın **başka programları çağırabildiği** her nokta bir kaçış fırsatıdır. `more`, `less`, `vi`, `man` gibi araçların hepsi içlerinden komut/kabuk çalıştırabilir; kısıtlı ortamlar bu yüzden dikkatle kapatılmalıdır. Pencereyi küçültüp `more`'u durmaya zorlamak da güzel bir ayrıntı: bir aracın davranışını, ona verilen ortamı (terminal boyutu) değiştirerek yönlendirdik.

> **Faydalı olabilir:** [Bandit Level 26](https://overthewire.org/wargames/bandit/bandit26.html).

<!-- part5-altnav -->

---

← [03 · Pin kodunu kırmak](03-pin-kodunu-kirmak.md) · [Part 5 içindekiler](README.md) · [05 · Kabuktan sonra son parola](05-kabuktan-sonra-son-parola.md) →
