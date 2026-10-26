<div align="center">

# Mehmet Mutioğlu

### Offensive & defensive security · AI-assisted full-stack development

`Penetration Testing` · `Application Security` · `Blue-Team Tooling` · `Secure Full-Stack` · `LLM Integration`

[![LinkedIn](https://img.shields.io/badge/LinkedIn-mehmetmutioglu-0a66c2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mehmetmutioglu/)
[![Website](https://img.shields.io/badge/Web-mution.com.tr-0b6e75)](https://mution.com.tr)
![Location](https://img.shields.io/badge/İstanbul-Türkiye-555)

</div>

---

## About

I build on both sides of the security line. In authorized lab and CTF environments I run end-to-end offensive scenarios (recon → web app testing → exploitation), and I turn that attacker's perspective into defensive tools and secure software. I also ship production web applications where I design the authorization, data protection and security layers myself — so I see a vulnerability the way both the attacker and the defender do.

I work with an AI-assisted, test-first workflow using **Claude Code**, and I verify my own projects with automated test suites.

---

## 🛡️ Open-Source Security Tools

### [LogSentry](https://github.com/MMSolver/logsentry) — SSH/auth log attack detector
Python CLI that flags brute-force, user-enumeration and successful-breach patterns in SSH logs, each mapped to **MITRE ATT&CK** (T1110, T1078). Built test-first (29 pytest tests, GitHub Actions CI), with memory-safe streaming and XSS-safe HTML reports.
`Python` · `TDD` · `MITRE ATT&CK` · `Blue-Team`

### [SPECTER](https://github.com/MMSolver/specter) — multi-agent recon & analysis framework
For **authorized** pentest/CTF: a hierarchical agent swarm that maps a target, fingerprints services and produces a MITRE-mapped, prioritized attack plan. Every network action passes a hard **scope guard**; it plans, it never auto-executes. 33 tests, live web dashboard.
`Python` · `Multi-Agent` · `Offensive Security` · `MITRE ATT&CK`

### [AI Support Desk](https://github.com/MMSolver/ai-support-desk) — AI-assisted support platform
Ticket triage with OpenAI structured output, treating model output as untrusted input (shared Zod validation), with a human-in-the-loop "needs review" fallback, rate limiting and CSP security headers. 94 tests (Vitest + Playwright).
`Next.js` · `TypeScript` · `OpenAI` · `Secure Coding`

---

## 🚀 Products I've Shipped

> Source code is private (own SaaS) or client-owned, so these link to the live products rather than a repo.

### SporPilot — sports-school management SaaS · [sporpilot.vercel.app](https://sporpilot.vercel.app/)
My own multi-tenant SaaS. Role-based access enforced in the database with **Row Level Security across all 31 public tables (105 policies)** — a coach only sees their own students, with full cross-club data isolation. The AI club assistant receives only summarized data with names pseudonymized; phone and national-ID numbers are never sent. 214 Playwright tests.
`Next.js` · `Supabase (PostgreSQL)` · `RLS` · `Google Gemini`

### Uğur Kuruyemiş — e-commerce platform · [ugurkuruyemis.com.tr](https://ugurkuruyemis.com.tr)
Production e-commerce platform delivered for a two-branch retail business: **20 data models, 18 API routes, 45 pages**. Authentication (Auth.js + bcrypt), middleware role control, Redis rate limiting, Zod input validation and allow-list HTML sanitization.
`Next.js` · `TypeScript` · `Prisma` · `PostgreSQL` · `API Security`

---

## 🧰 Toolbox

**Offensive:** Burp Suite · SQLMap · ffuf · Gobuster · Nmap · Metasploit · Hydra · OWASP Top 10 · Kali Linux · Hack The Box
**Defensive:** log analysis · brute-force / credential-stuffing detection · Wireshark · tcpdump · MITRE ATT&CK
**Build:** Python · TypeScript · Next.js · PostgreSQL · Supabase · Prisma · LLM integration (structured output, data masking, human-in-the-loop) · TDD · Git · CI

---

## 📚 Learning Path

- **Cybersecurity training** — Jul 2026 → Oct 2026 (network security & penetration testing, hands-on)
- **Full-Stack Development program** — Oct 2026 → Jul 2027 (10 months, internship-backed, final project phase)

> **Learn deeply. Build practically. Solve real problems — on both sides of security.**
