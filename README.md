<div align="center">

# Mehmet Mutioğlu

### Siber Güvenlik · Sızma Testi · Güvenlik Araçları

`Penetration Testing` · `Web Uygulama Güvenliği` · `Blue Team Araçları` · `Çok Kiracılı Sistem Güvenlik Testi` · `LLM Güvenliği`

[![LinkedIn](https://img.shields.io/badge/LinkedIn-mehmetmutioglu-0a66c2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mehmetmutioglu/)
[![Web](https://img.shields.io/badge/Web-mution.com.tr-0b6e75)](https://mution.com.tr)
![Konum](https://img.shields.io/badge/İstanbul-Türkiye-555)

</div>

---

## Hakkımda

Güvenliğin iki tarafında da çalışıyorum. Yetkili lab ve CTF ortamlarında (Hack The Box) uçtan uca saldırı senaryoları yürütüyorum: keşif (recon) → web uygulama testi → istismar (exploitation). Bu saldırgan bakış açısını hem savunma araçlarına hem de gerçek ürünlere yönelik saldırı testlerine dönüştürüyorum.

Araçlarımı ve ürünlerimi **Claude Code** ile AI destekli, test öncelikli bir iş akışıyla geliştiriyorum. Benim odağım güvenlik tarafı: tehdit modelleme, erişim kontrolü tasarımı ve bunu otomatik saldırı testleriyle kanıtlamak.

---

## 🛡️ Güvenlik Araçlarım

### [LogSentry](https://github.com/MMSolver/logsentry) — SSH/auth log saldırı tespit aracı
SSH loglarında brute-force, kullanıcı keşfi (user enumeration) ve başarılı sızma örüntülerini yakalayan Python CLI aracı. Her bulgu **MITRE ATT&CK** ile eşleniyor (T1110, T1078). Kayan pencere (sliding window) ile tespit, LOW→CRITICAL önem puanlaması, büyük dosyalar için bellek dostu satır satır okuma ve XSS'e karşı korumalı HTML rapor. 29 pytest testi, GitHub Actions CI.
`Python` · `Blue Team` · `Tehdit Tespiti` · `MITRE ATT&CK`

### [SPECTER](https://github.com/MMSolver/specter) — çok ajanlı keşif ve analiz çerçevesi
**Yetkili** sızma testi ve CTF çalışmaları için: hedefi haritalayan, servisleri tanımlayan ve MITRE eşlemeli, önceliklendirilmiş bir saldırı planı çıkaran hiyerarşik ajan sistemi. Her ağ işlemi katı bir **kapsam koruyucusundan (scope guard)** geçer. Sadece plan yapar, istismarı asla kendiliğinden çalıştırmaz (insan onayı şart). 33 test, canlı web paneli.
`Python` · `Offensive Security` · `Keşif` · `AI Ajanları`

---

## 🔐 Gerçek Ürünlerde Güvenlik Testi

> Claude Code ile geliştirildi. Kaynak kodu gizli (kendi SaaS ürünüm) ya da müşteriye ait olduğu için canlı ürünlere bağlantı veriliyor.

### Sportudent — spor okulları için çok kiracılı SaaS · [sportudent.com](https://sportudent.com)
Canlıda, ilk ödeme yapan müşterisi olan bir ürün. Okullar arası veri izolasyonunu tasarladım ve ona saldırdım:
- **Okullar arası saldırı testi: 2.154 kontrol, hiçbir sızıntı yok.** 430 görünürlük kontrolü, 1.404 doğrudan yazma denemesi (başka okulun verisini güncelleme/silme/ekleme, kendi kaydını başka okula taşıma, kendi rolünü yükseltme) ve 80 fonksiyon üzerinde 320 **IDOR** çağrısı.
- **Testin kendisi de test edildi:** Kasıtlı olarak bir açık açıldığında test başarısız oluyor. Yani test gerçekten yetki duvarına ulaşıyor.
- Herkese açık şemadaki her tabloda Row Level Security (RLS). 44 `SECURITY DEFINER` fonksiyonun hepsinde yetki kontrolü. Anonim bağlantılar için 128–192 bit rastgele token.
- AI asistanına sadece özet veri gider, isimler takma adla değiştirilir. Telefon ve TC kimlik numarası asla gönderilmez.

`PostgreSQL RLS` · `IDOR` · `Erişim Kontrolü` · `Supabase`

### [AI Support Desk](https://github.com/MMSolver/ai-support-desk) — LLM çıktısına güvenilmeyen girdi gibi davranmak
Yapay zekâ ile destek talebi sınıflandırma. Model çıktısı kullanıcı girdisi gibi doğrulanıyor (ortak Zod şemaları). AI hata verirse talep "inceleme gerekli" olarak insana düşüyor (human-in-the-loop). IP bazlı istek sınırlama (rate limiting) ve CSP güvenlik başlıkları. 94 test (Vitest + Playwright).
`LLM Güvenliği` · `Girdi Doğrulama` · `Güvenli Kodlama`

### Uğur Kuruyemiş — e-ticaret platformu · [ugurkuruyemis.com.tr](https://ugurkuruyemis.com.tr)
İki şubeli bir mağaza için e-ticaret: kimlik doğrulama (Auth.js + bcrypt), middleware ile rol kontrolü, Redis ile istek sınırlama, Zod ile girdi doğrulama ve izinli etiket listesiyle HTML temizleme.
`Kimlik Doğrulama` · `Rate Limiting` · `API Güvenliği`

---

## 🧰 Kullandığım Araçlar

**Keşif ve OSINT:** Nmap · masscan · Maltego · theHarvester
**Web uygulama:** Burp Suite · SQLMap · ffuf · Gobuster · Nikto · OWASP Top 10 (SQLi, XSS, IDOR)
**İstismar:** Metasploit · Netcat · Hydra
**Savunma:** log analizi · brute-force / credential-stuffing tespiti · Wireshark · tcpdump · Nessus · MITRE ATT&CK
**Platformlar:** Kali Linux · Linux · Hack The Box
**Otomasyon:** Python · Docker · Git · CI · Claude Code

---

## 📚 Eğitim

- **Siber güvenlik eğitimi** — Tem 2026 → Eki 2026 · ağ güvenliği ve sızma testi, uygulamalı lab çalışmaları
- **Yazılım geliştirme programı** — Eki 2026 → Tem 2027 (devam ediyor)
- **Sertifikalar** — Cisco: Introduction to Cybersecurity · Endpoint Security
