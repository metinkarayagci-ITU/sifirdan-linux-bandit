# Part 2 — Bandit Level 5–9

[Başlangıç](../README.md)

Part 1'de Bandit'e bağlanıp ilk beş adımı attık. Part 2'de tek bir soru farklı kılıklarda karşımıza çıkıyor: **"aradığım şeyi nasıl tarif ederim?"** Dosya sayısı gözle bakılamayacak kadar arttığında, tek tek incelemek yerine koşulu bir araca söyleyip süzdürmeyi öğreniyoruz.

Bu part Level 5'ten Level 9'a kadarki beş adımı kapsar; hepsinin dayanağı Part 0'daki `file`, `find`, `grep` ve pipe kavramları.

## Bu part'ta ne yapıyoruz?

| Sayfa | Görev | Part 0 dayanağı |
|---|---|---|
| [00 · Tek okunabilir dosya](00-tek-okunabilir-dosya.md) | Türe göre ayıklamak (`file`) | [06 · Dosya adları ve türleri](../part-0/06-dosya-adlari-ve-turleri.md) |
| [01 · Boyut ve türe göre aramak](01-boyut-ve-ture-gore-aramak.md) | `find` ile koşul birleştirme | [08 · grep ve find](../part-0/08-grep-ve-find.md) |
| [02 · Sahibine göre dosya bulmak](02-sahibine-gore-dosya-bulmak.md) | Tüm diski tarayıp gürültüyü ayıklamak | [05 · Akışlar](../part-0/05-akislar-pipe-yonlendirme.md), [08](../part-0/08-grep-ve-find.md) |
| [03 · Kalabalıkta bir kelime](03-kalabalikta-bir-kelime.md) | Büyük dosyada `grep` ile süzmek | [08 · grep ve find](../part-0/08-grep-ve-find.md) |
| [04 · Yalnız bir kez geçen satır](04-yalniz-bir-kez-gecen-satir.md) | `sort \| uniq -u` ile eşsiz satır | [05 · Akışlar, pipe ve yönlendirme](../part-0/05-akislar-pipe-yonlendirme.md) |

## Örnekler hakkında

- Komut çıktıları, Bandit'in mekaniğini **kendi makinemde yerel olarak** taklit ederek üretildi; gerçek sunucudaki dosya adları ve davranış aynıdır. Çıktılarda parola yerine görünen `‹...›` ifadesi, gerçek oturumda 32 karakterlik rastgele bir dizidir.
- Kod bloklarında `$` ile başlayan satır bizim yazdığımız komuttur; altındaki satır(lar) çıktıdır.

---

← [Part 1](../part-1/README.md) · [Başlangıç](../README.md) · [00 · Tek okunabilir dosya](00-tek-okunabilir-dosya.md) →
