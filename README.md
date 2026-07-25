<div align="center">

# 🛡️ Web Sitesi Güvenlik Ön Analiz Aracı
### Website Security Pre-Analysis Tool

[![Live Demo](https://img.shields.io/badge/demo-canlı%20%2F%20live-brightgreen?style=for-the-badge)](https://resuloztas.com/guvenlik-analizi)
[![Laravel](https://img.shields.io/badge/backend-Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)](https://laravel.com)
[![Tailwind](https://img.shields.io/badge/frontend-Tailwind%20CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![Passive Only](https://img.shields.io/badge/tarama-pasif%20%2F%20passive-blue?style=for-the-badge)](#)

**Aktif sızma testi yapmadan, tamamen pasif kaynaklardan bir sitenin güvenlik yüzeyini değerlendirir.**
**Evaluates a website's security surface using only passive, third-party data — zero direct probing.**

🇹🇷 [Türkçe](#-türkçe) &nbsp;•&nbsp; 🇬🇧 [English](#-english)

</div>

---

## 🇹🇷 Türkçe

### 🤔 Neden Pasif Tarama?

> Türk Ceza Kanunu 243-244. maddeler, izinsiz bir sisteme erişim veya sistemin çalışmasını engelleme fiillerini suç olarak tanımlıyor.

Bir domain girip "tara" butonuna basan herhangi bir ziyaretçi, aslında o sitenin sahibi olmayabilir. Bu yüzden klasik pentest araçlarının yaptığı **aktif port taraması, exploit denemesi** gibi işlemler burada tercih edilmedi. Bunun yerine, zaten herkese açık olan üçüncü parti veri kaynaklarından pasif bilgi toplanıyor: hedef sisteme hiçbir istek gönderilmiyor, sadece o sistem hakkında halihazırda toplanmış veriler sorgulanıyor.

### 🧩 Mimari — 4 Veri Kaynağı

| Kaynak | Ne Yapar |
|---|---|
| 🔒 **SSL Labs API** | Sertifika geçerliliği, protokol versiyonu, cipher suite zayıflıkları |
| 📡 **Shodan / Censys** | Açık portlar, çalışan servisler — önbellekten pasif sorgulama |
| 🕵️ **crt.sh** | Certificate Transparency loglarından unutulmuş subdomain'ler |
| ⚠️ **CIRCL CVE API** | Tespit edilen versiyonları bilinen açıklarla eşleştirme |

> 💡 **Shodan / Censys nasıl pasif kalıyor?** Bu servisler interneti sürekli tarayıp sonuçları önbelleğe alıyor, biz o önbelleğe bakıyoruz — hedef sisteme kendi isteğimizi hiç göndermiyoruz.

### 🔄 Kullanım Akışı

```
Domain girilir → 4 kaynaktan pasif veri toplanır → Teaser skoru üretilir
                                                          │
                                                          ▼
                                    KVKK uyumlu form → Tam rapor açılır
```

Her sorgu (form doldursun doldurmasın) `scan_requests` tablosuna loglanır; sadece formu dolduranlar açık rıza ile `leads` tablosuna eklenir.

### ⚙️ Teknik Yığın

`Laravel` `Tailwind CSS` `Proxmox` `Hetzner Cloud VPS` `Native PHP DNS`

### 📬 İletişim

Bu araç hakkında sorularınız veya benzer bir sistem kurmak istekleriniz için → **[resuloztas.com](https://resuloztas.com)**

---

## 🇬🇧 English

### 🤔 Why Passive-Only?

> Under Turkish Penal Code articles 243-244, unauthorized access to a system — or interfering with its operation — is a criminal offense.

Anyone who types a domain into a scanning tool might not actually own that system. So this tool deliberately skips everything an active scanner would normally do: **no port scanning, no exploit attempts, no direct probing.** Instead it pulls from third-party sources that already scanned the public internet and cached the results — no request is ever sent to the target itself.

### 🧩 Architecture — 4 Data Sources

| Source | What It Does |
|---|---|
| 🔒 **SSL Labs API** | Certificate validity, protocol version, cipher suite strength |
| 📡 **Shodan / Censys** | Open ports & running services — read passively from cache |
| 🕵️ **crt.sh** | Surfaces forgotten subdomains via Certificate Transparency logs |
| ⚠️ **CIRCL CVE API** | Cross-references fingerprinted versions against known CVEs |

> 💡 **How do Shodan/Censys stay passive?** Both continuously scan the public internet and cache results — this tool reads that cache instead of scanning the target itself.

### 🔄 Flow

```
Domain submitted → passive data pulled from 4 sources → teaser score generated
                                                                │
                                                                ▼
                                    KVKK-compliant form → full report unlocked
```

Every query is logged to a `scan_requests` table regardless of form completion; only consented submissions go into a separate `leads` table.

### ⚙️ Stack

`Laravel` `Tailwind CSS` `Proxmox` `Hetzner Cloud VPS` `Native PHP DNS`

### 📬 Contact

Questions about this tool, or want to build something similar? → **[resuloztas.com](https://resuloztas.com)**

<div align="center">

---

Made with 🛡️ by [Resul Öztaş](https://resuloztas.com) — İstanbul

</div>
