# Part 4 — Bandit Level 16–21

[Başlangıç](../README.md)

Part 3'te verinin biçimiyle uğraştık. Part 4'te sahne genişliyor: **ağ servisleri**, **şifreli bağlantılar** ve **yetki** kavramları giriyor. Artık yalnız dosya okumuyor; portlarla konuşuyor, servisleri kendimiz kuruyor ve başka kullanıcıların yetkilerini kullanıyoruz.

Bu part Level 16'dan Level 21'e kadarki altı adımı kapsar.

## Bu part'ta ne yapıyoruz?

| Sayfa | Görev | Anahtar araç |
|---|---|---|
| [00 · Şifreli bağlantı](00-sifreli-baglanti.md) | SSL/TLS porta parola göndermek | `openssl s_client` |
| [01 · Doğru portu bulmak](01-dogru-portu-bulmak.md) | Port tarama + servis parmak izi | `nmap`, `openssl s_client` |
| [02 · İki dosyanın farkı](02-iki-dosyanin-farki.md) | Değişen tek satırı bulmak | `diff` |
| [03 · Girişte kapı yüzüne kapanınca](03-giriste-atilan-kabuk.md) | Giriş betiğini baypas etmek | `ssh ... komut` |
| [04 · Bir başkası adına çalıştırmak](04-baskasi-adina-calistirmak.md) | setuid ile yetki kullanmak | `bandit20-do` |
| [05 · Kendi servisine bağlanmak](05-kendi-servisine-baglanmak.md) | Dinleyen bir servis kurmak | `nc -l`, iş kontrolü |

## Örnekler hakkında

- Komut çıktıları, Bandit'in mekaniğini **kendi makinemde yerel olarak** taklit ederek üretildi; gerçek sunucudaki davranış aynıdır. Çıktılarda parola yerine görünen `‹...›` ifadesi, gerçek oturumda 32 karakterlik rastgele bir dizidir.
- Kod bloklarında `$` ile başlayan satır bizim yazdığımız komuttur; altındaki satır(lar) çıktıdır.

---

← [Part 3](../part-3/README.md) · [Başlangıç](../README.md) · [00 · Şifreli bağlantı](00-sifreli-baglanti.md) →
