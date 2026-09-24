# 05 · Kendi servisine bağlanmak

[Başlangıç](../README.md) · [Part 4 içindekiler](README.md)

**Hedef:** Ev dizinindeki `suconnect` adlı setuid program, komut satırında verdiğimiz porta bağlanır; oradan bir satır okuyup **bu seviyenin (bandit20) parolasıyla** karşılaştırır. Eşleşirse `bandit21`'in parolasını geri gönderir. Yani programın bağlanacağı **bir servisi kendimiz kurmalıyız** ve o servis, doğru parolayı söylemeli.

## Programı tanımak

```
$ ./suconnect
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP.
If it receives the correct password from the other side, the next
password is transmitted back.
```

Program bir **istemci**: bir porta bağlanıp oradan gelen satırı bekliyor. Öyleyse bizim de o portta **dinleyen** ve bağlanana bandit20 parolasını söyleyen bir servis çalıştırmamız gerek.

## İki uçlu kurulum

Bunun için iki şeyi aynı anda koştururuz: bir yanda `nc` ile bir portu **dinleyip** parolayı söyleyen taraf, öbür yanda ona bağlanan `suconnect`. `nc`'yi arka planda (`&`) başlatıp, sonra `suconnect`'i aynı porta yönlendiririz (Part 0'daki iş kontrolü — *job control*):

```
$ cat /etc/bandit_pass/bandit20 | nc -l -p 1337 &
$ ./suconnect 1337
Read: ‹bandit20 parolası›
Password matches, sending next password
‹bandit21 parolası›
```

- `nc -l -p 1337` → 1337 portunda **dinler** (`-l` = listen); bağlanana bandit20 parolasını verir,
- `&` → bu işi arka plana atar, terminal bize geri döner,
- `./suconnect 1337` → programı o porta bağlar; parola eşleşince `bandit21`'in parolasını basar.

## Perde arkası

Buradaki kavramsal sıçrama, ağ iletişiminin **iki tarafı** olduğunu somut olarak görmek: bir **dinleyen** (server, `nc -l`), bir de **bağlanan** (client, `suconnect`). Şimdiye kadar hep bağlanan taraftık; burada ilk kez bir servisi **biz kurduk.** Aynı zamanda iş kontrolüyle (`&`, arka plan) iki işi tek terminalde eşzamanlı yürütmeyi kullandık — `screen` ya da `tmux` da benzer işi görür. "Programın beklediği tarafı kendim sağlarım" düşüncesi, ağ güvenliğinde tekrar tekrar karşına çıkar.

> **Faydalı olabilir:** [Bandit Level 21](https://overthewire.org/wargames/bandit/bandit21.html).

## Part 4'ün sonunda

Bu part'ta ağ ve yetki dünyasına girdik: şifreli bağlantılarla konuştuk (`openssl s_client`), açık portları keşfedip parmak izlerini çıkardık (`nmap`), iki durumun farkına odaklandık (`diff`), bir giriş betiğini baypas ettik (`ssh ... komut`), setuid ile başka bir kullanıcının yetkisini kullandık (`bandit20-do`) ve ilk kez kendi ağ servisimizi kurduk (`nc -l`). Part 5'te işi zamanlanmış görevler (cron) ve kısıtlı kabuklardan kaçış devralacak.

<!-- part4-altnav -->

---

← [04 · Bir başkası adına çalıştırmak](04-baskasi-adina-calistirmak.md) · [Part 4 içindekiler](README.md)
