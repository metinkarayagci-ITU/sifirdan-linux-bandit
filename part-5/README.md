# Part 5 — Bandit Level 22–27

[Başlangıç](../README.md)

Part 4'te ağ ve yetki dünyasına girdik. Part 5'te sistemin **arka planını** kurcalıyoruz: zamanlanmış görevler (cron), betik okuma, kendi kodunu başka bir kimliğe koşturma, kaba kuvvet ve kısıtlı kabuklardan kaçış. Ortak tema, bir sistemin otomatik davranışlarını okuyup onlardaki açıkları kullanmak.

Bu part Level 22'den Level 27'ye kadarki altı adımı kapsar.

## Bu part'ta ne yapıyoruz?

| Sayfa | Görev | Anahtar kavram |
|---|---|---|
| [00 · Zamanlanmış görev okumak](00-zamanlanmis-gorev-okumak.md) | cron job'ı bulup okumak | `cron`, `/etc/cron.d/` |
| [01 · Adı hesaplanan dosya](01-adi-hesaplanan-dosya.md) | Betiğin hesabını tekrarlamak | `md5sum`, kod okuma |
| [02 · Kendi betiğini koşturmak](02-kendi-betigini-kosturmak.md) | Kendi betiğini başka kimliğe koşturmak | betik yazma, izinler |
| [03 · Pin kodunu kırmak](03-pin-kodunu-kirmak.md) | Dört haneli pini kaba kuvvetle kırmak | `for`, `seq`, `nc` |
| [04 · Kısıtlı kabuktan kaçış](04-kisitli-kabuktan-kacis.md) | `more`/`vi` üzerinden kabuğa çıkmak | restricted shell escape |
| [05 · Kabuktan sonra son parola](05-kabuktan-sonra-son-parola.md) | setuid ile yetki yükseltme | `bandit27-do` |

## Örnekler hakkında

- Komut çıktıları, Bandit'in mekaniğini **kendi makinemde yerel olarak** taklit ederek üretildi; gerçek sunucudaki davranış aynıdır. Çıktılarda parola yerine görünen `‹...›` ifadesi, gerçek oturumda 32 karakterlik rastgele bir dizidir.
- Kod bloklarında `$` ile başlayan satır bizim yazdığımız komuttur; altındaki satır(lar) çıktıdır.

---

← [Part 4](../part-4/README.md) · [Başlangıç](../README.md) · [00 · Zamanlanmış görev okumak](00-zamanlanmis-gorev-okumak.md) →
