# Part 6 — Bandit Level 28–33

[Başlangıç](../README.md)

Serinin son part'ı. Burada bambaşka bir araç devreye giriyor: **Git**. Parola artık bir dosyada değil, bir Git deposunun içinde saklı — kimi zaman apaçık, kimi zaman geçmişte, bir dalda ya da bir etikette. Son adımda ise bir kez daha bir kabuktan kaçıyoruz.

Bu part Level 28'den Level 33'e kadarki altı adımı kapsar. Git seviyelerinde depoları **kendi makinemize** klonlarız (yerelde `git` kurulu olmalı).

## Bu part'ta ne yapıyoruz?

| Sayfa | Görev | Anahtar komut |
|---|---|---|
| [00 · Uzak depoyu klonlamak](00-uzak-depoyu-klonlamak.md) | Depoyu klonlayıp okumak | `git clone` |
| [01 · Geçmişe bakmak](01-gecmise-bakmak.md) | Silinen parolayı tarihçeden bulmak | `git log -p` |
| [02 · Dallar arasında](02-dallar-arasinda.md) | Başka bir daldaki parola | `git branch -a`, `git show` |
| [03 · Etiketlerde saklı](03-etiketlerde-sakli.md) | Bir etikette saklı parola | `git tag`, `git show` |
| [04 · Depoya dosya itmek](04-depoya-dosya-itmek.md) | Depoya push edip yanıt almak | `git push`, `git add -f` |
| [05 · Büyük harfe çeviren kabuk](05-buyuk-harfe-ceviren-kabuk.md) | Filtreleyen kabuktan kaçış | `$0` |

## Örnekler hakkında

- Git seviyelerindeki depolar gerçek OverTheWire deposunun yapısını yansıtır; komut çıktıları kendi makinemde üretildi. Çıktılarda parola yerine görünen `‹...›` ifadesi, gerçek oturumda 32 karakterlik rastgele bir dizidir.
- Kod bloklarında `$` ile başlayan satır bizim yazdığımız komuttur; `>>` ile başlayan satır ise büyük-harf kabuğunun istemidir.

---

← [Part 5](../part-5/README.md) · [Başlangıç](../README.md) · [00 · Uzak depoyu klonlamak](00-uzak-depoyu-klonlamak.md) →
