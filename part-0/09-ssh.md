# 09 · SSH

[Başlangıç](../README.md) · [Part 0 içindekiler](README.md)

SSH ile bağlandığımızda komutları artık kendi bilgisayarımızda değil, uzak makinedeki oturumda çalıştırırız. Bağlantı kurduğumuz anda terminal yine aynı terminal gibi görünür; fakat arka tarafta artık farklı bir makineyle konuşuyoruz. Bu nedenle bir komut çalıştırmadan önce hangi sistemde olduğumuzu bilmek, terminal kullanımının temel alışkanlıklarından biridir.

## Bağlantının adımları

```
ssh -p 2222 kullanici@sunucu
```

1. **İlk bağlantıda host key sorusu.** SSH, bağlandığımız sunucunun kimliğini daha önce görmediyse sorar:

   ```
   The authenticity of host '[sunucu]:2222 ([ip-adresi]:2222)' can't be established.
   ED25519 key fingerprint is SHA256:...
   This key is not known by any other names.
   Are you sure you want to continue connecting (yes/no/[fingerprint])?
   ```

   `yes` yazarız. Sunucunun kimliği `~/.ssh/known_hosts` dosyasına kaydedilir ve bir dahaki bağlantıda bu soru gelmez. (Parmak izi ve adres sunucuya göre değişir.)

2. **Parola.** `kullanici@sunucu's password:` satırında parolayı yazarız. Yazarken ekranda **hiçbir karakter görünmez**, yıldız bile çıkmaz; bu normaldir. Yazıp Enter'a basarız.

3. **Uzak prompt.** Bağlantı kurulunca prompt'taki kullanıcı ve makine adı değişir. Emin olmak için `whoami` ve `pwd`.

4. **Çıkış.** `exit` yazınca oturum kapanır ve kendi makinemizin prompt'una döneriz.

## Sık görülen bağlantı hataları

```
ssh: connect to host localhost port 2222: Connection refused
```

O adreste, o portta dinleyen bir SSH hizmeti yok: port numarası yanlış olabilir ya da hizmet kapalıdır. (Bu çıktıyı, SSH sunucusu olmayan bir makinede `ssh -p 2222 localhost` ile aldım.)

```
Permission denied, please try again.
```

Kullanıcı adı ya da parola yanlış. Parola görünmediği için yazım hatası kolay olur; yavaşça yeniden deneriz. Kopyala-yapıştır için bkz. [00 · Ortam kurulumu](00-ortam-kurulumu.md).

```
ssh: Could not resolve hostname ...: Name or service not known
```

Sunucu adı yanlış yazılmış ya da internet bağlantısı yok.

```
ssh: connect to host ... port ...: Connection timed out
```

Sunucuya hiç ulaşılamıyor: port yanlış olabilir ya da ağ bağlantıyı engelliyor olabilir.

## Standart port ve -p

SSH'ın standart portu 22'dir; `-p` yazmazsak 22'ye bağlanılır. Sunucu başka bir port kullanıyorsa `-p` ile belirtmek zorundayız. `ssh kullanici@sunucu -p 2222` yazılışı da çalışır (bkz. [01](01-terminal-shell-komut-yapisi.md)).

<!-- part0-altnav -->

---

← [08 · grep ve find](08-grep-ve-find.md) · [Part 0 içindekiler](README.md) · [10 · Yardım ve hata mesajları](10-yardim-ve-hata-mesajlari.md) →
