# 03 · Pin kodunu kırmak

[Başlangıç](../README.md) · [Part 5 içindekiler](README.md)

**Hedef:** `bandit25`'in parolası, 30002 portundaki bir servisten alınabilir — ama servis, `bandit24`'ün parolasının **yanında dört haneli gizli bir pin kodu** da istiyor. Pin'i öğrenmenin başka yolu yok: 0000'dan 9999'a kadar **hepsini denemek** (kaba kuvvet — *brute force*) gerekiyor.

## Servisi tanımak

Önce ne istediğini görelim:

```
$ nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password
for user bandit24 and the secret pincode on a single line, separated
by a space.
```

Servis her satırda `‹parola› ‹pin›` biçiminde bir deneme bekliyor. 10.000 olasılık var; elle denenmez, ama tek tek bağlanmak da yavaş. İyi haber: servis **aynı bağlantıda** ardışık denemeleri kabul ediyor, yeni bağlantı açmaya gerek yok.

## 10.000 denemeyi tek seferde göndermek

Bütün pin olasılıklarını (parola ile birlikte) üretip tek bir `nc` bağlantısından yollarız:

```
$ for i in $(seq -w 0000 9999); do
    echo "‹bandit24 parolası› $i"
  done | nc localhost 30002
...
Correct!
The password of user bandit25 is ‹bandit25 parolası›
```

- `seq -w 0000 9999` → 0000'dan 9999'a kadar (baştaki sıfırlar korunarak) tüm sayılar,
- her biri için `echo "‹parola› $i"` → bir deneme satırı,
- hepsi bir boru ile `nc`'ye → servise akıtılır.

Doğru pin gelince servis `Correct!` der ve `bandit25`'in parolasını basar. Yanlış denemelerin arasından doğru satırı ayıklamak için çıktıyı `grep -v Wrong` ile de süzebiliriz.

## Perde arkası

Kaba kuvvet, olasılık uzayı **yeterince küçük** olduğunda geçerli bir yöntemdir — burada yalnız 10.000 ihtimal var. Asıl ders, servisin tasarımındaki iki noktayı fark etmek: (1) deneme sayısını sınırlamaması (rate limiting yok), (2) aynı bağlantıda binlerce denemeye izin vermesi. Gerçek sistemlerde bu ikisi tam da kaba kuvvete karşı konan savunmalardır; yokluğu, dört haneli bir pini saniyeler içinde kırılabilir kılar. Bir kabuk döngüsüyle (`for`) binlerce girdi üretip bir servise akıtmak, otomasyonun günlük bir aracıdır.

> **Faydalı olabilir:** [Bandit Level 25](https://overthewire.org/wargames/bandit/bandit25.html).

<!-- part5-altnav -->

---

← [02 · Kendi betiğini koşturmak](02-kendi-betigini-kosturmak.md) · [Part 5 içindekiler](README.md) · [04 · Kısıtlı kabuktan kaçış](04-kisitli-kabuktan-kacis.md) →
