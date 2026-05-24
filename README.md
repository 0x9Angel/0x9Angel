# Hey there! I'm Angel 👋

### Cybersecurity Student · Offensive Security · Systems & Cryptography Engineer

![Pentesting](https://img.shields.io/badge/-Pentesting-1f1f1f?style=flat-square&logo=hackthebox&logoColor=white)
![Offensive Security](https://img.shields.io/badge/-Offensive%20Security-c00?style=flat-square)
![SOC](https://img.shields.io/badge/-SOC-1f6feb?style=flat-square)
![Rust](https://img.shields.io/badge/-Rust-000?style=flat-square&logo=rust)
![Cryptography](https://img.shields.io/badge/-Cryptography-555?style=flat-square&logo=keepassxc&logoColor=white)
![CTF](https://img.shields.io/badge/-CTF-2ea44f?style=flat-square)

---

## About Me

Cybersecurity student working at the intersection of **offensive security** and **secure systems engineering**. I split my time between breaking things (web & infra pentesting, CTFs, red-team tooling) and building things the right way (custom security tools in Rust, post-quantum cryptography, end-to-end encrypted messaging).

> *I break things to understand how they work — then I build the version that doesn't.*

---

##  Currently Building

###  Crypto — Sovereign encrypted messenger (flagship project)

A production-grade end-to-end encrypted messaging platform for **European enterprise and government**, written in **Rust + Tauri + React**. Same codebase ships on Windows / macOS / Linux / iOS / Android.

- **End-to-end encryption** via X3DH + Double Ratchet (the Signal protocol).
- **Enterprise-ready**: OIDC SSO, SCIM 2.0 provisioning, Ed25519-signed audit logs, on-prem license gating, active/passive HA replication.
- **SQLCipher-encrypted local store** with Argon2id KDF, 15 schema migrations shipped.
- **250+ tests passing, 0 clippy warnings** with strict `deny(unwrap_used)` policy on production code paths.
- Target customers: French/EU defense industrials (Airbus, Thales, Dassault), regulated industries, investigative journalism.

###  Gotham — Custom post-quantum mixnet protocol

The transport layer underneath Crypto. A **Sphinx-format mixnet** I designed and implemented from scratch in Rust — the same class of network as Tor and Nym, but tuned for real-time messaging (50-300 ms median vs 800-2000 ms for Tor) and **post-quantum from day one**.

- **X25519 + ML-KEM-768 hybrid** key encapsulation (NIST FIPS 203 compliant).
- **Loopix-style Poisson mixing + cover traffic** — observer can't distinguish active from idle users.
- **QUIC + Noise XK** per-link transport with pluggable fallbacks (TLS 1.3, obfs4, meek-CDN planned).
- **Stateless relays** with LRU+TTL replay cache — nothing to subpoena, nothing to seize.
- Fuzz harnesses (`cargo-fuzz`), Kani model-checking proofs, and dudect-style timing-leak benches in place.

###  Custom offensive tooling

Red-team utilities in Rust and Python — CTF write-ups, web exploitation primitives, infrastructure recon. Some public, some private until they stop being useful.

---

##  Recent Highlights

- Shipped 8 phases of a custom mixnet protocol (~25k lines of Rust + 6k TypeScript) with full test coverage.
- Implemented classical Sphinx **folded shift-and-pad construction** (Danezis-Goldberg 2009) from the paper — including the cumulative-filler invariant.
- Wrote production-grade hybrid post-quantum KEM combining X25519 + ML-KEM-768 with HKDF-derived sub-keys.
- Designed and shipped a **Tauri 2 desktop app** integrating end-to-end encryption with a custom mixnet — UI, backend, and protocol layer.
- Authored an internal **threat model** with explicit "what we resist" / "what we don't" tables, the kind a CISO actually wants to read.

---

##  Ask Me About

- **Offensive security** — web app pentesting (OWASP top 10, business logic), infrastructure recon, Active Directory abuse, Linux privilege escalation.
- **Cryptography in practice** — Signal-style ratchets, Sphinx mixnets, post-quantum migration, AEAD discipline, constant-time programming pitfalls.
- **Rust for security tooling** — async with Tokio, zero-copy parsers, fuzz harnesses, lint policies that catch real bugs.
- **CTF strategy** — pwn / crypto / web / forensics. Always down for a team-up.
- **Linux administration** — Arch, systemd hardening (sandboxing, namespaces, seccomp), eBPF observability.

---

##  Languages & Tools

### Languages
![Rust](https://img.shields.io/badge/-Rust-000?style=for-the-badge&logo=rust)
![Python](https://img.shields.io/badge/-Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Bash](https://img.shields.io/badge/-Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)
![TypeScript](https://img.shields.io/badge/-TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![React](https://img.shields.io/badge/-React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)

### Frameworks & Runtimes
![Tauri](https://img.shields.io/badge/-Tauri-FFC131?style=for-the-badge&logo=tauri&logoColor=black)
![Tokio](https://img.shields.io/badge/-Tokio-3E73AA?style=for-the-badge)
![QUIC](https://img.shields.io/badge/-QUIC-1f6feb?style=for-the-badge)
![SQLite](https://img.shields.io/badge/-SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)

### Cryptography
![X25519](https://img.shields.io/badge/-X25519-555?style=for-the-badge)
![ML--KEM](https://img.shields.io/badge/-ML--KEM--768-c00?style=for-the-badge)
![Noise%20Protocol](https://img.shields.io/badge/-Noise%20XK-2ea44f?style=for-the-badge)
![ChaCha20--Poly1305](https://img.shields.io/badge/-ChaCha20--Poly1305-555?style=for-the-badge)

### Security & Infrastructure
![Linux](https://img.shields.io/badge/-Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Arch Linux](https://img.shields.io/badge/-Arch%20Linux-1793D1?style=for-the-badge&logo=archlinux&logoColor=white)
![Docker](https://img.shields.io/badge/-Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/-Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![Burp Suite](https://img.shields.io/badge/-Burp%20Suite-FF6633?style=for-the-badge&logo=burpsuite&logoColor=white)
![Nmap](https://img.shields.io/badge/-Nmap-004088?style=for-the-badge)
![Wireshark](https://img.shields.io/badge/-Wireshark-1679A7?style=for-the-badge&logo=wireshark&logoColor=white)

---

> *Building the things I wish existed. Mostly in Rust, mostly secure-by-default.*
