# Sıfırdan Linux ve Siber Güvenlik: OverTheWire Bandit

Komut satırını sıfırdan öğrenip [OverTheWire Bandit](https://overthewire.org/wargames/bandit/) savaş oyunuyla uygulamalı pekiştiren, **baştan sona tek başına takip edilebilen** bir kaynak. Daha önce hiç terminal kullanmamış biri düşünülerek yazıldı.

Bu repo kendi başına yeterlidir; başka bir yazıyı ya da videoyu izlemiş olma şartı yoktur. Aynı içeriği anlatı biçiminde Medium'da da yazıyorum ([serinin Medium hâli](https://medium.com/p/b0ad03a4fdf0)); istersen oradan da okuyabilirsin, ama buradaki sayfalar o yazıları okumuş olmayı varsaymaz.

## Kimin için

- Terminalle ilk kez tanışan ve nereden başlayacağını bilemeyenler.
- Siber güvenliğe girmeden önce Linux ve komut satırı zeminini sağlam kurmak isteyenler.

Ön bilgi gerekmez. İhtiyacımız olan tek şey bir Linux terminali — onu da ilk sayfa, [00 · Ortam kurulumu](part-0/00-ortam-kurulumu.md), anlatır.

## Nasıl ilerler

İçerik iki katman hâlinde:

- **Part 0 — Linux / Terminal Temelleri:** Bandit'e girmeden önce ihtiyacımız olan komutlar ve kavramlar. Doğrudan seviyelere atlamak yerine önce zemini kurarız.
- **Part 1–6 — Bandit:** Öğrendiklerimizi OverTheWire Bandit seviyelerinde uygularız; her seviye, o ana kadar öğrendiğimiz bir-iki kavramı gerçekten kullandırır.

Her sayfa küçük ve tek konuludur; sırayla okunacak biçimde birbirine bağlıdır (sayfaların altında "önceki / sonraki" bağlantıları vardır).

## İçindekiler

| Part | Konu | Durum |
|---|---|---|
| **0** | [Linux / Terminal Temelleri](part-0/README.md) | hazır |
| 1 | Bandit Level 0–4 | hazırlanıyor |
| 2 | Bandit Level 5–9 | — |
| 3 | Bandit Level 10–15 | — |
| 4 | Bandit Level 16–21 | — |
| 5 | Bandit Level 22–27 | — |
| 6 | Bandit Level 28–33 | — |

## Örnekler hakkında

- Ekran görüntülerini ve metin çıktılarını **Kali Linux (WSL)** üzerinde, **Bash** ile kendi `metin` kullanıcımla aldım. Kendi sistemimizde kullanıcı adı, makine adı, tarih ve bazı sayılar farklı olacaktır.
- Kod bloklarında `→` işaretinden sonrası açıklamadır, terminale yazılmaz.
- `command`, `username` gibi İngilizce adlar yer tutucudur; yerlerine kendi değerimizi yazarız.

## Bandit ve parolalar

Bandit seviyelerinin **parolaları bu repoda yer almaz.** İki nedenle: OverTheWire'ın kuralları oyun parolalarının yayımlanmasını yasaklar, ayrıca parolalar zaman zaman değişir. Her sayfa, parolanın **nerede ve nasıl** bulunacağını anlatır; parolayı kendi oturumunda sen bulursun. (Bandit'in kendi önerisi de bu: bulduğun parolaları kendine not al.)

## Telif ve teşekkür

Bandit, [OverTheWire](https://overthewire.org/) topluluğunun ücretsiz sunduğu bir savaş oyunudur; seviyeler, açıklamaları ve dosyaları OverTheWire'a aittir. Bu repo bağımsız bir **öğrenme rehberi / writeup**'tır: OverTheWire'ın içeriğini yeniden yayımlamaz, seviyeleri kendi cümlelerimle anlatır ve hiçbir oyun parolası içermez. Buradaki açıklama ve örnekler öğrenmen için serbestçe kullanılabilir.
