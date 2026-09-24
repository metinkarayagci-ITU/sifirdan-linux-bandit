# Part 3 — Bandit Level 10–15

[Başlangıç](../README.md)

Part 2'de veri düz metindi; sadece süzmemiz gerekiyordu. Part 3'te veri **kılık değiştiriyor**: kodlanıyor, kaydırılıyor, katman katman sıkıştırılıyor. Buradaki ortak beceri, verinin **hangi biçimde** olduğunu tanımak ve onu açacak doğru aracı seçmek.

Bu part Level 10'dan Level 15'e kadarki altı adımı kapsar.

## Bu part'ta ne yapıyoruz?

| Sayfa | Görev | Anahtar araç |
|---|---|---|
| [00 · Görünür metni ayıklamak](00-gorunur-metni-ayiklamak.md) | İkiliden okunabilir metni çekmek | `strings`, `grep` |
| [01 · Base64 çözmek](01-base64-cozmek.md) | Base64 kodlamasını açmak | `base64 -d` |
| [02 · 13 harf kaydırmak (ROT13)](02-rot13.md) | Harf kaydırmayı geri almak | `tr` |
| [03 · Katman katman açmak](03-katman-katman-acmak.md) | Tekrarlı sıkıştırmayı çözmek | `xxd -r`, `file`, `gunzip`/`bunzip2`/`tar` |
| [04 · Parola yerine anahtar](04-parola-yerine-anahtar.md) | SSH özel anahtarıyla giriş | `ssh -i` |
| [05 · Ağ üzerinden parola](05-ag-uzerinden-parola.md) | Bir ağ servisiyle konuşmak | `nc` |

## Örnekler hakkında

- Komut çıktıları, Bandit'in mekaniğini **kendi makinemde yerel olarak** taklit ederek üretildi; gerçek sunucudaki davranış aynıdır. Çıktılarda parola yerine görünen `‹...›` ifadesi, gerçek oturumda 32 karakterlik rastgele bir dizidir.
- Kod bloklarında `$` ile başlayan satır bizim yazdığımız komuttur; altındaki satır(lar) çıktıdır.

---

← [Part 2](../part-2/README.md) · [Başlangıç](../README.md) · [00 · Görünür metni ayıklamak](00-gorunur-metni-ayiklamak.md) →
