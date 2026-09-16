# Part 0 — Linux / Terminal Temelleri

[Başlangıç](../README.md)

Bandit'e girmeden önce ihtiyacımız olan komut satırı temelleri. Doğrudan Bandit seviyelerine atlamak yerine önce zemini kurarız: `pwd`, `ls`, `cat`, `grep`, `find`, SSH ve dosya izinleri gibi kavramlarla ilk kez burada, sakin bir ortamda tanışırız. Sayfaları sırayla okumak en verimlisidir; her sayfanın altında önceki/sonraki bağlantısı vardır.

## Bölümler

| # | Sayfa | İçinde ne var |
|---|---|---|
| 00 | [Ortam kurulumu](00-ortam-kurulumu.md) | WSL / sanal makine, hangi shell'deyiz, SSH istemcisi, kopyala-yapıştır |
| 01 | [Terminal, shell ve komut yapısı](01-terminal-shell-komut-yapisi.md) | komut + seçenek + argüman, uzun seçenekler, klavye kısayolları |
| 02 | [Dosya sistemi ve gezinme](02-dosya-sistemi-ve-gezinme.md) | path, `pwd`, `whoami`, prompt, `cd`, `ls`, `ls -l` sütunları, dizin ağacı |
| 03 | [Dosya ve dizin işlemleri](03-dosya-ve-dizin-islemleri.md) | `mkdir`, `touch`, `cp`, `mv`, `rm`, `-r`, `-i`, joker karakter uyarısı |
| 04 | [Dosya içeriğini okumak](04-dosya-icerigini-okumak.md) | `cat`, `less` tuşları, `head`, `tail`, `du` |
| 05 | [Akışlar, pipe ve yönlendirme](05-akislar-pipe-yonlendirme.md) | stdin/stdout/stderr deneyleri, `\|`, `>`, `>>`, `2>`, `2>&1`, `<` |
| 06 | [Dosya adları ve türleri](06-dosya-adlari-ve-turleri.md) | boşluk, tırnak türleri, tire ile başlayan adlar, `file`, `reset` |
| 07 | [İzinler](07-izinler.md) | `-rw-r--r--`, sahip ve grup, dizin izinleri, `id`, `chmod` |
| 08 | [grep ve find](08-grep-ve-find.md) | `grep -i -v -n -r`, `find -type -size -user`, birleştirme |
| 09 | [SSH](09-ssh.md) | host key onayı, bağlantı hataları, `exit` |
| 10 | [Yardım ve hata mesajları](10-yardim-ve-hata-mesajlari.md) | `man`, `help`, `--help`, `type`, hata mesajları sözlüğü |

## Terminalde düşünme döngüsü

Part 0'daki araçların hepsinin ortak bir mantığı var: terminalde çalışırken genellikle önce problemi parçalara ayırıyoruz. Bu bölümdeki komutları öğrendikten sonra aşağıdaki akışlar tanıdık gelecek.

Elimizde adı belli olmayan bir dosya varsa:

```
Bulunduğun yeri kontrol et
        ↓
İçeriği listele
        ↓
Dosyanın türünü anlamaya çalış
        ↓
Gerekirse içeriğini incele
```

Bir metin içinde belirli bir bilgi arıyorsak:

```
Veriyi al
   ↓
Gereksiz çıktıyı azalt
   ↓
Belirli deseni ara
   ↓
Sonucu incele
```

Bir dosyayı bulmamız gerekiyorsa:

```
Arama alanını belirle
        ↓
Koşulları belirle
        ↓
Uygun aracı kullan
```

Bunları küçük bir çalışma alışkanlığına dönüştürebiliriz. Bir problemle karşılaştığımızda rastgele komutlar denemek yerine:

```
1. Nerede olduğunu kontrol et.
2. Hangi kullanıcıyla çalıştığını kontrol et.
3. Elinde ne olduğunu listele.
4. Dosya veya verinin türünü anlamaya çalış.
5. Problemi küçük parçalara ayır.
6. İhtiyaca uygun aracı seç.
7. Çıktıyı dikkatlice oku.
8. Gerekirse çıktıyı başka bir araca aktar.
9. Bilmediğin bir seçeneği dokümantasyondan öğren.
10. Hata aldıysan önce hata mesajını incele.
```

Bu liste bir ezber listesi değil; terminalde düşünmeye başlamak için kullanabileceğimiz basit bir kontrol noktası. Zamanla bu adımların çoğu otomatikleşir.

## Alıştırmalar

Her biri, ilgili sayfayı okuduktan sonra kendi terminalimizde denenmek için. Çözüm yok; takılırsak ilgili sayfaya döneriz.

1. **(02)** Ev dizinimizden başlayıp yalnız relative path kullanarak `/etc`'ye gidelim, sonra tek komutla ev dizinine dönelim. Her adımda `pwd` ile doğrulayalım.
2. **(02)** Ev dizinimizde `ls` ile `ls -a` çıktısını karşılaştıralım: hangi öğeler yalnız ikincisinde var, neden?
3. **(03)** `deneme/alt/en-alt` dizin yapısını tek komutla oluşturalım, sonra `deneme`'yi tamamen silelim. Silmeden önce içinde ne olduğunu listeleyelim.
4. **(04)** `/etc/services` dosyasının yalnız ilk 5 ve son 5 satırını görelim.
5. **(05)** Var olan bir dosyayla var olmayan bir dosyayı aynı `cat` komutuna verelim; normal çıktıyı `iyi.txt`'ye, hatayı `kotu.txt`'ye ayıralım.
6. **(06)** Adında boşluk olan bir dosya oluşturup içeriğini iki farklı yazımla okuyalım.
7. **(06)** Uzantısı `.txt` olan ama içi sıkıştırılmış veri olan bir dosya hazırlayıp `file` ile türünü doğrulayalım.
8. **(07)** Kendi oluşturduğumuz bir dosyanın izinlerini okuyalım; sahibe çalıştırma izni verip farkı `ls -l` ile görelim.
9. **(08)** `/etc` altında adında `ssh` geçen dizinleri, hata mesajları görünmeden bulalım.
10. **(10)** `cd`, `ls` ve `echo` için hangisine `help`, hangisine `man` ile bakmamız gerektiğini `type` ile belirleyelim.

---

[Başlangıç](../README.md) · [00 · Ortam kurulumu](00-ortam-kurulumu.md) →
