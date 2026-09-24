# 01 · Boyut ve türe göre aramak

[Başlangıç](../README.md) · [Part 2 içindekiler](README.md)

**Hedef:** `bandit6`'nın parolası yine `inhere` altında bir yerde, ama bu kez üç özelliği birden verilmiş: **insan-okunabilir**, **1033 bayt** boyutunda ve **çalıştırılabilir değil.** Bir önceki adımda dosyaları elle eledik; burada dosya sayısı elle bakılamayacak kadar çok — o yüzden aramayı komuta yaptırırız.

## Neden elle olmuyor?

```
$ ls
maybehere00  maybehere01  maybehere02  ...  maybehere19
```

Yirmi alt dizin, her birinde bir sürü dosya. Hepsini tek tek `file`'lamak saatler alır. Doğru araç `find`: dosya ağacında **koşullara uyanı** bulur (Part 0 · [08 · grep ve find](../part-0/08-grep-ve-find.md)).

## Koşulları find'e çevirmek

Hedefin üç özelliğini üç seçeneğe çeviririz:

```
$ find . -readable -size 1033c ! -executable
./maybehere07/.file2
```

- `-size 1033c` → tam **1033 bayt** (`c` = bayt/karakter).
- `! -executable` → çalıştırma izni **olmayan** (`!` koşulu tersine çevirir).
- `-readable` → okuyabildiğimiz dosyalar.

Üç koşul aynı anda sağlanınca geriye tek dosya kalır. İçeriğini `cat` ile okuruz:

```
$ cat ./maybehere07/.file2
‹bandit6 parolası›
```

## Perde arkası

`find`'ın gücü, koşulları **birleştirebilmesinden** gelir: yan yana yazılan koşullar "ve" (VE) anlamına gelir, `!` ise olumsuzlar. Bir hedefi kelimelerle tarif edebiliyorsan (`şu boyutta, şu izinde, şu tür`), onu neredeyse birebir `find` seçeneklerine çevirebilirsin. Bu, "aradığımı nasıl bir sorguya dökerim?" alışkanlığının ilk adımı.

> **Faydalı olabilir:** [Bandit Level 6](https://overthewire.org/wargames/bandit/bandit6.html).

<!-- part2-altnav -->

---

← [00 · Tek okunabilir dosya](00-tek-okunabilir-dosya.md) · [Part 2 içindekiler](README.md) · [02 · Sahibine göre dosya bulmak](02-sahibine-gore-dosya-bulmak.md) →
