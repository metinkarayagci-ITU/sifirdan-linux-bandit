# 03 · Dosya ve dizin işlemleri

⬅ Medium'daki bölüm: **Dosya ve dizinlerle temel işlemler** · [Part 0 içindekiler](README.md)

Dosyaları ve dizinleri yalnızca görüntülemeyiz. Gerektiğinde oluşturabilir, kopyalayabilir, taşıyabilir, yeniden adlandırabilir veya silebiliriz. Buradaki amaç bu komutların bütün seçeneklerini bir anda öğrenmek değil; dosya sistemiyle çalışırken temel işlemlerin terminal üzerinden de doğrudan yapılabildiğini görmek.

Aşağıdaki çıktıları Kali'de, geçici bir dizinde aldım.

## mkdir: dizin oluşturmak

```
mkdir test
```

İç içe dizinleri tek seferde oluşturmak için `-p`:

```
mkdir -p proje/kaynak/eski
ls -R proje
```

```
proje:
kaynak

proje/kaynak:
eski

proje/kaynak/eski:
```

(`ls -R` alt dizinleri de listeler.)

## touch: boş dosya oluşturmak

```
touch notes.txt
```

`touch` aynı zamanda zaten var olan bir dosyanın son değiştirilme zamanını da günceller; komutun ismi de buradan gelir. Dosyanın içeriğine dokunmaz.

## cp: kopyalamak

```
cp notes.txt backup.txt
```

Dizin kopyalarken `-r` (recursive, "içindekilerle birlikte") gerekir. Unutursak:

```
cp proje yedek
```

```
cp: -r not specified; omitting directory 'proje'
```

Doğrusu:

```
cp -r proje yedek
```

## mv: taşımak veya yeniden adlandırmak

`mv`'nin iki işi var ve ikisi aynı komutla yapılır:

```
mv backup.txt old.txt      → aynı dizinde: yeniden adlandırır
mv old.txt proje/          → hedef bir dizinse: içine taşır
mv proje/old.txt ./yeni.txt → taşır ve aynı anda yeniden adlandırır
```

## rm: silmek

```
rm old.txt
```

Grafik arayüzlerdeki çöp kutusundan farklı olarak `rm` dosyayı doğrudan siler; geri almak için bir "geri dönüşüm kutusu" yoktur.

Dizinler için `rm` tek başına çalışmaz:

```
rm proje
```

```
rm: cannot remove 'proje': Is a directory
```

`rmdir` yalnız **boş** dizinleri siler:

```
rmdir proje
```

```
rmdir: failed to remove 'proje': Directory not empty
```

İçindekilerle birlikte silmek için `rm -r proje` kullanılır. Bu, dizinin altındaki her şeyi siler; yazmadan önce `ls -R proje` ile neyin gideceğine bakmak iyi bir alışkanlıktır.

## -i: silmeden önce sor

```
rm -i sil.txt
```

```
rm: remove regular empty file 'sil.txt'?
```

`y` yazarsak siler, başka bir şey yazarsak dosya yerinde kalır. `cp -i` ve `mv -i` de var olan bir dosyanın üzerine yazmadan önce sorar.

## Joker karakter (*) ile dikkat

`*`, "herhangi bir karakter dizisi" anlamına gelir ve shell tarafından eşleşen dosya adlarına genişletilir:

```
ls *.txt     → önce neyin eşleştiğine bak
rm *.txt     → bulunduğumuz dizindeki bütün .txt dosyalarını siler
```

`rm` ile joker karakter kullanmadan önce aynı deseni `ls` ile denemek, yanlış dosyaları silmemenin en kolay yoludur.
