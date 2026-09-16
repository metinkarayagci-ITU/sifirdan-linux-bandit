# 00 · Ortam kurulumu

[Başlangıç](../README.md) · [Part 0 içindekiler](README.md)

Part 0'daki örnekleri denemek için bir Linux terminaline, Part 1'den itibaren de bir SSH istemcisine ihtiyacımız var.

## Linux terminali: üç seçenek

| Seçenek | Kimin için | Not |
|---|---|---|
| **WSL** (Windows Subsystem for Linux) | Windows kullananlar | En hızlı yol. PowerShell'i yönetici olarak açıp `wsl --install` yazmak Ubuntu kurar; Kali için `wsl --install -d kali-linux`. |
| **Sanal makine** | Sistemini değiştirmek istemeyenler | VirtualBox veya VMware içine Ubuntu ya da Kali kurulur. Daha çok disk ve bellek ister. |
| **Kurulu Linux / macOS** | Zaten kullananlar | Doğrudan terminali açmak yeterli. macOS'ta bazı komutların çıktısı farklıdır. |

## Hangi shell'deyiz?

Örnekler **Bash** varsayar. Kali'nin masaüstü kurulumunda ve macOS'ta varsayılan shell **zsh**'tır; komutların çoğu aynı çalışır ama `help` gibi Bash'e özgü olanlar çalışmaz.

```
echo $0      → bash (ya da -bash) veya zsh yazar
bash         → Bash'e geç
exit         → önceki shell'e dön
```

## SSH istemcisi

Kurulu olup olmadığını sürümünü sorarak anlarız:

```
ssh -V
```

Kali'deki çıktı:

```
OpenSSH_10.3p1 Debian-4, OpenSSL 3.6.2 7 Apr 2026
```

Sürüm numarası farklı olabilir; önemli olan `OpenSSH` ile başlayan bir satır görmek. Windows 10 ve 11'de aynı komut PowerShell'de de çalışır. Debian/Ubuntu tabanlı bir sistemde yoksa: `sudo apt install openssh-client`.

## Terminalde kopyala / yapıştır

Terminalde **Ctrl+C kopyalamaz, çalışan komutu durdurur.** Bunun yerine:

```
Ctrl+Shift+C   → kopyala (çoğu Linux terminali)
Ctrl+Shift+V   → yapıştır (çoğu Linux terminali)
```

Windows Terminal'de (WSL) metin seçiliyken Ctrl+C kopyalar, Ctrl+V yapıştırır. Part 1'de parolaları yapıştırırken bu işimize yarayacak.

## Bu repodaki örnekler hakkında

Ekran görüntülerini Kali Linux (WSL) üzerinde, Bash ile kendi `metin` kullanıcımla aldım. Bu yüzden prompt görüntülerde iki satırdır:

```
┌──(metin㉿kali)-[~]
└─$
```

Kendi sistemimizde kullanıcı adı, makine adı ve prompt'un görünümü farklı olacaktır; taşıdığı bilgi aynıdır (bkz. [02 · Dosya sistemi ve gezinme](02-dosya-sistemi-ve-gezinme.md)).

<!-- part0-altnav -->

---

[Part 0 içindekiler](README.md) · [01 · Terminal, shell ve komut yapısı](01-terminal-shell-komut-yapisi.md) →
