<p align="center">
  <img src="assets/banner.svg" width="100%" alt="Mehmet Mutioğlu — Cybersecurity · Penetration Testing · Security Tooling">
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/mehmetmutioglu/"><img src="https://img.shields.io/badge/LinkedIn-mehmetmutioglu-21262d?style=for-the-badge&logo=linkedin&logoColor=00ff9c&labelColor=0d1117" alt="LinkedIn"></a>
  <a href="https://mution.com.tr"><img src="https://img.shields.io/badge/Website-mution.com.tr-21262d?style=for-the-badge&logo=googlechrome&logoColor=00ff9c&labelColor=0d1117" alt="Website"></a>
  <img src="https://img.shields.io/badge/Location-İstanbul,%20Türkiye-21262d?style=for-the-badge&logo=googlemaps&logoColor=00ff9c&labelColor=0d1117" alt="Location">
</p>

---

## About

Cybersecurity alanında **offensive** ve **defensive** tarafta birlikte çalışıyorum. Yetkili lab ve CTF ortamlarında (Hack The Box) uçtan uca saldırı senaryoları yürütüyorum: **recon → web application testing → exploitation**. Bu saldırgan bakış açısını kendi güvenlik araçlarıma ve gerçek ürünlere yönelik **attack test**'lere dönüştürüyorum.

Araçlarımı ve ürünlerimi **Claude Code** ile **AI-assisted, test-first** bir iş akışıyla geliştiriyorum. Odağım güvenlik tarafı: **threat modeling**, **access control** tasarımı ve bunu otomatik saldırı testleriyle kanıtlamak.

<table>
  <tr>
    <th align="left">Offensive Security</th>
    <th align="left">Defensive Security</th>
    <th align="left">Product Security</th>
  </tr>
  <tr>
    <td valign="top">Recon &amp; OSINT<br>Web application testing<br>OWASP Top 10 (SQLi, XSS, IDOR)<br>Exploitation (lab / CTF)</td>
    <td valign="top">Log analysis<br>Brute-force &amp; credential-stuffing detection<br>MITRE ATT&amp;CK mapping<br>Traffic analysis</td>
    <td valign="top">Multi-tenant isolation (RLS)<br>Cross-tenant attack testing<br>LLM output validation<br>Rate limiting &amp; input validation</td>
  </tr>
</table>

---

## Security Tools

### [LogSentry](https://github.com/MMSolver/logsentry) · SSH/auth log attack detector

SSH loglarında **brute-force**, **user enumeration** ve **successful breach** örüntülerini yakalayan Python CLI aracı. Her bulgu **MITRE ATT&CK** ile eşleniyor (T1110, T1078).

- **Sliding window** ile tespit, LOW → CRITICAL **severity scoring**
- Büyük dosyalar için **memory-safe streaming**, XSS'e karşı korumalı HTML rapor
- 4 rapor formatı (terminal, JSON, CSV, HTML), SIEM/SOC iş akışına uygun
- 29 **pytest** testi, **GitHub Actions CI**

<img src="https://img.shields.io/badge/Python-21262d?style=flat-square&logo=python&logoColor=00ff9c"> <img src="https://img.shields.io/badge/Blue%20Team-21262d?style=flat-square"> <img src="https://img.shields.io/badge/MITRE%20ATT%26CK-21262d?style=flat-square"> <img src="https://img.shields.io/badge/Threat%20Detection-21262d?style=flat-square">

### [SPECTER](https://github.com/MMSolver/specter) · multi-agent recon & analysis framework

**Yetkili** penetration test ve CTF çalışmaları için hiyerarşik bir **AI agent** sistemi. Hedefi haritalıyor, servisleri tanımlıyor ve MITRE eşlemeli, önceliklendirilmiş bir **attack plan** çıkarıyor.

- Her ağ işlemi katı bir **scope guard**'dan geçer
- Sadece plan yapar, exploit'i asla kendiliğinden çalıştırmaz (**human approval** şart)
- CVE adayları için **false-positive** kontrolü yapan konsensüs motoru
- 33 test, canlı web dashboard

<img src="https://img.shields.io/badge/Python-21262d?style=flat-square&logo=python&logoColor=00ff9c"> <img src="https://img.shields.io/badge/Offensive%20Security-21262d?style=flat-square"> <img src="https://img.shields.io/badge/Recon-21262d?style=flat-square"> <img src="https://img.shields.io/badge/AI%20Agents-21262d?style=flat-square">

---

## Security Testing on Real Products

> Claude Code ile geliştirildi. Kaynak kodu private (kendi SaaS ürünüm) ya da müşteriye ait olduğu için canlı ürünlere bağlantı veriliyor.

### Sportudent · multi-tenant SaaS · [sportudent.com](https://sportudent.com)

Spor okulları için canlıda olan, ilk ödeme yapan müşterisi bulunan bir ürün. Okullar arası **tenant isolation** modelini tasarladım ve ona saldırdım:

<table>
  <tr>
    <td align="center"><h3>2.154</h3>cross-tenant<br>attack check</td>
    <td align="center"><h3>0</h3>data<br>leak</td>
    <td align="center"><h3>320</h3>IDOR call<br>(80 function)</td>
    <td align="center"><h3>44 / 44</h3>SECURITY DEFINER<br>function with authz</td>
  </tr>
</table>

- **430 visibility** kontrolü ve **1.404 direct-write** denemesi: başka okulun verisini güncelleme/silme/ekleme, kendi kaydını başka okula taşıma, **privilege escalation**. Hepsi engellendi.
- **Mutation-tested:** Kasıtlı olarak bir açık açıldığında test başarısız oluyor. Yani test gerçekten yetki duvarına ulaşıyor.
- Public şemadaki her tabloda **Row Level Security (RLS)**, anonim linkler için 128–192 bit token.
- AI asistanına sadece özet veri gider, isimler **pseudonymize** edilir. Telefon ve TC kimlik numarası asla gönderilmez.

<img src="https://img.shields.io/badge/PostgreSQL%20RLS-21262d?style=flat-square&logo=postgresql&logoColor=00ff9c"> <img src="https://img.shields.io/badge/IDOR%20Testing-21262d?style=flat-square"> <img src="https://img.shields.io/badge/Access%20Control-21262d?style=flat-square"> <img src="https://img.shields.io/badge/Supabase-21262d?style=flat-square&logo=supabase&logoColor=00ff9c">

### [AI Support Desk](https://github.com/MMSolver/ai-support-desk) · LLM output as untrusted input

AI ile destek talebi sınıflandırma. Model çıktısı kullanıcı girdisi gibi doğrulanıyor (ortak **Zod** şemaları). AI hata verirse talep insana düşüyor (**human-in-the-loop**). IP bazlı **rate limiting** ve **CSP** security header'ları var. 94 test (Vitest + Playwright).

<img src="https://img.shields.io/badge/LLM%20Security-21262d?style=flat-square"> <img src="https://img.shields.io/badge/Input%20Validation-21262d?style=flat-square"> <img src="https://img.shields.io/badge/Secure%20Coding-21262d?style=flat-square">

### Uğur Kuruyemiş · e-commerce platform · [ugurkuruyemis.com.tr](https://ugurkuruyemis.com.tr)

İki şubeli bir mağaza için e-ticaret. **Authentication** (Auth.js + bcrypt), middleware ile **role-based access control**, Redis ile **rate limiting**, Zod ile **input validation** ve **allow-list HTML sanitization**.

<img src="https://img.shields.io/badge/Authentication-21262d?style=flat-square"> <img src="https://img.shields.io/badge/Rate%20Limiting-21262d?style=flat-square"> <img src="https://img.shields.io/badge/API%20Security-21262d?style=flat-square">

---

## Toolbox

**Recon & OSINT**<br>
<img src="https://img.shields.io/badge/Nmap-21262d?style=for-the-badge"> <img src="https://img.shields.io/badge/masscan-21262d?style=for-the-badge"> <img src="https://img.shields.io/badge/Maltego-21262d?style=for-the-badge"> <img src="https://img.shields.io/badge/theHarvester-21262d?style=for-the-badge">

**Web Application**<br>
<img src="https://img.shields.io/badge/Burp%20Suite-21262d?style=for-the-badge&logo=burpsuite&logoColor=00ff9c"> <img src="https://img.shields.io/badge/SQLMap-21262d?style=for-the-badge"> <img src="https://img.shields.io/badge/ffuf-21262d?style=for-the-badge"> <img src="https://img.shields.io/badge/Gobuster-21262d?style=for-the-badge"> <img src="https://img.shields.io/badge/Nikto-21262d?style=for-the-badge"> <img src="https://img.shields.io/badge/OWASP%20Top%2010-21262d?style=for-the-badge&logo=owasp&logoColor=00ff9c">

**Exploitation**<br>
<img src="https://img.shields.io/badge/Metasploit-21262d?style=for-the-badge&logo=metasploit&logoColor=00ff9c"> <img src="https://img.shields.io/badge/Netcat-21262d?style=for-the-badge"> <img src="https://img.shields.io/badge/Hydra-21262d?style=for-the-badge">

**Defensive**<br>
<img src="https://img.shields.io/badge/Wireshark-21262d?style=for-the-badge&logo=wireshark&logoColor=00ff9c"> <img src="https://img.shields.io/badge/tcpdump-21262d?style=for-the-badge"> <img src="https://img.shields.io/badge/Nessus-21262d?style=for-the-badge"> <img src="https://img.shields.io/badge/MITRE%20ATT%26CK-21262d?style=for-the-badge"> <img src="https://img.shields.io/badge/Log%20Analysis-21262d?style=for-the-badge">

**Platforms & Automation**<br>
<img src="https://img.shields.io/badge/Kali%20Linux-21262d?style=for-the-badge&logo=kalilinux&logoColor=00ff9c"> <img src="https://img.shields.io/badge/Linux-21262d?style=for-the-badge&logo=linux&logoColor=00ff9c"> <img src="https://img.shields.io/badge/Hack%20The%20Box-21262d?style=for-the-badge&logo=hackthebox&logoColor=00ff9c"> <img src="https://img.shields.io/badge/Python-21262d?style=for-the-badge&logo=python&logoColor=00ff9c"> <img src="https://img.shields.io/badge/Docker-21262d?style=for-the-badge&logo=docker&logoColor=00ff9c"> <img src="https://img.shields.io/badge/Git-21262d?style=for-the-badge&logo=git&logoColor=00ff9c"> <img src="https://img.shields.io/badge/GitHub%20Actions-21262d?style=for-the-badge&logo=githubactions&logoColor=00ff9c"> <img src="https://img.shields.io/badge/Claude%20Code-21262d?style=for-the-badge&logo=anthropic&logoColor=00ff9c">

---

## Education & Certifications

- **Cybersecurity Training** · Tem 2026 → Eki 2026 · network security ve penetration testing, uygulamalı lab çalışmaları
- **Software Development Program** · Eki 2026 → Tem 2027 · devam ediyor
- **Cisco** · Introduction to Cybersecurity · Endpoint Security

---

<p align="center">
  <sub><code>authorized testing only · responsible disclosure</code></sub>
</p>
