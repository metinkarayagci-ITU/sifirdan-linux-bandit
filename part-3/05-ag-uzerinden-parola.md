# 05 · Ağ üzerinden parola

[Başlangıç](../README.md) · [Part 3 içindekiler](README.md)

**Hedef:** `bandit15`'in parolasını bir dosyadan değil, **ağdan** alacağız: `bandit14`'ün parolasını `localhost`'un **30000 numaralı portuna** gönderirsek, sunucu bize bir sonrakini geri yollar. Bu, seride ilk kez bir dosyayla değil, çalışan bir **ağ servisiyle** konuştuğumuz an.

## Bir porta veri göndermek

Şimdiye kadar hep dosyalarla çalıştık; burada bir TCP portuna bağlanıp veri göndermemiz gerekiyor. Bunun temel aracı `nc` (netcat) — "ağın İsviçre çakısı" da denir. Elimizdeki parolayı bir boru ile `nc`'ye verip 30000 portuna yollarız:

```
$ cat /etc/bandit_pass/bandit14 | nc localhost 30000
Correct!
‹bandit15 parolası›
```

- `cat /etc/bandit_pass/bandit14` → bu seviyenin (bandit14) parolasını okur,
- `| nc localhost 30000` → onu `localhost`'un 30000 portundaki servise gönderir.

Servis parolayı doğru bulunca `Correct!` der ve `bandit15`'in parolasını geri yollar.

## Perde arkası

`nc`, bir porta ham veri göndermenin ve o porttaki servisin ne konuştuğunu görmenin en doğrudan yoludur. Bir web sunucusuna elle HTTP isteği yollamaktan, açık bir portu yoklamaya kadar sayısız işte karşına çıkar. Buradaki kavramsal sıçrama şu: bir bilgisayardaki "servisler" birer **port** üzerinden dinler; doğru portu bulup doğru veriyi gönderirsen onunla konuşabilirsin. Sonraki seviyelerde aynı fikri şifreli bağlantılarla (SSL/TLS) tekrar göreceğiz.

> **Faydalı olabilir:** [Bandit Level 15](https://overthewire.org/wargames/bandit/bandit15.html).

## Part 3'ün sonunda

Bu part'ta veri artık "düz" değildi: görünür metni ikiliden ayıkladık (`strings`), kodlamayı çözdük (`base64 -d`), yer değiştirmeyi geri aldık (ROT13/`tr`), katman katman sıkıştırmayı açtık (`file` + uygun araç döngüsü), parola yerine bir anahtarla giriş yaptık (`ssh -i`) ve ilk kez bir ağ servisiyle konuştuk (`nc`). Ortak fikir: verinin **hangi biçimde** olduğunu tanımak, onu açacak aracı seçmenin yarısıdır. Part 4'te ağ servisleri, şifreli bağlantılar ve yetki yükseltme (setuid) konularına gireceğiz.

<!-- part3-altnav -->

---

← [04 · Parola yerine anahtar](04-parola-yerine-anahtar.md) · [Part 3 içindekiler](README.md)
