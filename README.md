# Hey there! I'm Angel 👋

**Cybersecurity Student · Offensive Security · Systems & Cryptography · Freelance Web & E-commerce Dev**

## About Me

Cybersecurity student (Bachelor Cybersécurité, Ynov Toulouse) working at the intersection of offensive security and secure systems engineering. I split my time between breaking things (web & infra pentesting, CTFs, red-team tooling) and building things the right way (custom security tools in Rust, post-quantum cryptography, end-to-end encrypted messaging). On the other side of the desk, I work as a freelance developer and co-founded StarsBrand, where I handle everything technical on web and e-commerce projects.

> I break things to understand how they work, then I build the version that doesn't.

## Currently Building

### Crypto: sovereign encrypted messenger (flagship project)

A production-grade end-to-end encrypted messaging platform for European enterprise and government, written in Rust + Tauri + React. One codebase, shipping installers for Windows, macOS and Linux; mobile targets build but are not signed or released yet.

* End-to-end encryption via X3DH + Double Ratchet (the Signal protocol), with a hybrid X25519 + ML-KEM-768 post-quantum leg folded into the handshake.
* Enterprise-ready: OIDC SSO, SCIM 2.0 provisioning, Ed25519-signed audit logs, on-prem license gating, active/passive HA replication.
* SQLCipher-encrypted local store with Argon2id KDF, **35 schema migrations** shipped, each one-way and versioned.
* **661 Rust tests** plus a TypeScript suite, **zero clippy warnings** under `-D warnings`, with `deny(clippy::unwrap_used)` enforced on non-test code across the protocol crates.
* **71 findings triaged from a full adversarial audit: 54 fixed, 10 reduced, 7 open** — every residual named in the register with what it costs and what would close it, rather than quietly dropped.
* Community edition published; relay operators are being onboarded and the network is not yet operator-diverse (see Gotham below — I state this plainly rather than claim anonymity the deployment cannot deliver).
* Target customers: French/EU defense industrials, regulated industries, public institutions, investigative journalism.

Product site: [crypto-app.net](https://crypto-app.net) · Build log: [crypto-organisation.netlify.app](https://crypto-organisation.netlify.app)

### Gotham: custom post-quantum mixnet protocol

The transport layer underneath Crypto. A Sphinx-format mixnet I designed and implemented from scratch in Rust — the same class of network as Tor and Nym, tuned for real-time messaging and post-quantum from day one.

* X25519 + ML-KEM-768 hybrid key encapsulation (NIST FIPS 203 compliant).
* Loopix-style Poisson mixing + cover traffic, so an observer cannot distinguish an active user from an idle one.
* QUIC + Noise XK per-link transport with pluggable fallbacks (TLS 1.3, obfs4, meek-CDN planned).
* Relays hold almost nothing: a bounded LRU+TTL replay cache of opaque per-hop MACs, and that is it.
* Fuzz harnesses (`cargo-fuzz`), Kani model-checking proofs, and dudect-style timing-leak benches in place.
* Per-hop header MACs cover the whole downstream routing block, so a relay that tags a packet to correlate it with a colluding peer is caught at the first honest hop.

**Where the network actually stands.** Five relays are live, all on Oracle Cloud, all under one operator label — mine. Path selection fails closed on operator diversity, so it refuses to build a route through two relays it cannot *prove* belong to different operators. That means the mixnet does not route yet, by design, and messages currently take a store-and-forward mailbox path: content stays end-to-end encrypted, transport metadata does not. Three independent operators is what changes that. **Running one public relay is the single most useful thing anyone can do for this project**, and the install is one command.

### Nyx: systems programming language

A systems language written in Rust with a Cranelift backend.

* Affine types, second-class references, lexical borrow checking, Python-readable surface syntax.
* M0 shipped: skeleton, CLI, lexer, 32 passing tests, clean clippy/fmt, full spec in-repo.
* M1 in progress: recursive descent parser with Pratt precedence.

### Encrypted DNS client

Cross-platform Oblivious DNS-over-HTTPS client in Rust (RFC 9230).

* HPKE X25519 / AES-128-GCM, hickory-resolver, ring, local stub resolver on `:53`.
* Hardened IPC (closed enum protocol, peer-credential auth, mutex-serialized access).
* Dynamic WFP sessions on Windows, socket activation on Unix. 60 tests passing.

### Privacy suite and custom offensive tooling

* `fp-audit`, `leak-guard`, `anonguard-helperd`: Rust/Tauri privacy tools built around an nftables killswitch architecture.
* Red-team utilities in Rust and Python: CTF write-ups, web exploitation primitives, infrastructure recon. Some public, some private until they stop being useful.
* Defensive OSINT / CTI: full investigations on phishing domains and francophone leak marketplaces, written up as formal dossiers (verified / inferred / not captured) and reported through PHAROS, Cybermalveillance and Signal Spam.

### Alpharelec SAV

Tauri v2 + React + SQLite workshop management app, sole developer, running in production in a family hi-fi repair business handling roughly 37,500 repair dossiers and 19,000 clients.

### StarsBrand: web & e-commerce studio

Co-founded studio where my partner owns design and art direction and I own the entire technical side.

* Headless e-commerce stack: Next.js + Tailwind on the front, Shopify as the back office through the raw Storefront GraphQL API, self-hosted, Cart API basket, Shopify checkout, GDPR consent management, GA4, ISR.
* In-house design system (design tokens, Tailwind preset, React components) reused across Next.js, Shopify Liquid and Tauri apps.
* `shopify_audit.py`: Python tool that scans a Shopify store for legal and technical compliance, then generates the report.
* Delivery and hardening work on live sites: [kao-project.fr](https://kao-project.fr) for an esport structure, local business sites, SPF/DMARC and Cloudflare bot policy cleanups, SEO/GEO fixes.

## Recent Highlights

* Shipped a custom mixnet protocol across 8 phases — roughly **84k lines of Rust and 7k of TypeScript** in the monorepo — with the test and lint discipline above.
* Implemented the classical Sphinx folded shift-and-pad construction (Danezis–Goldberg 2009) from the paper, including the cumulative-filler invariant.
* Wrote a production hybrid post-quantum KEM combining X25519 + ML-KEM-768 with HKDF-derived sub-keys.
* Shipped a coordinated wire-breaking release: header format v3, a versioned X3DH derivation, and signed invitation links — sequenced relays-first because an updated client cannot reach an un-upgraded fleet, and the failure would have been silent.
* Ran two adversarial review passes over my own security fixes and found fifteen defects **in the fixes themselves**, including one where a patch introduced a denial of service while closing a different hole. Fixed and regression-tested, each with a test that fails on the old code.
* Authored an internal threat model with explicit "what we resist" / "what we don't" tables — the kind a CISO actually wants to read.
* Completed the TryHackMe Jr Penetration Tester path (Dec 2025), on top of Web Fundamentals and Pre Security.
* Bac Pro CIEL with highest honours (2026), now starting a Bachelor in Cybersecurity at Ynov Toulouse.

## How I Work

A few habits that show up in every repo here, because they are the reason I trust any of it:

* **Measure before asserting.** If a README says 661 tests, I ran them. If a threat model says a property holds, there is a test that fails without it.
* **Name the residual.** Every security register I keep has a "reduced" column, not just fixed and open, and each entry says exactly what is still exposed and what would close it. A fix that is real but partial gets written up as partial.
* **A security fix is new code, and new code has new defects.** Patches get reviewed as adversarially as the original, because more than once the patch was the bug.
* **Refuse to claim what the deployment does not deliver.** The mixnet above is a good protocol running on a network that cannot route yet, and I say so on the product site too.

## Ask Me About

* **Offensive security**: web app pentesting (OWASP Top 10, business logic), infrastructure recon, Active Directory abuse, Linux privilege escalation.
* **Cryptography in practice**: Signal-style ratchets, Sphinx mixnets, post-quantum migration, AEAD discipline, constant-time programming pitfalls.
* **Rust for security tooling**: async with Tokio, zero-copy parsers, fuzz harnesses, lint policies that catch real bugs.
* **Compilers**: Cranelift codegen, affine type systems, borrow checking.
* **CTF strategy**: pwn / crypto / web / forensics. Always down for a team-up.
* **Linux administration**: Arch, systemd hardening (sandboxing, namespaces, seccomp), eBPF observability.

## Languages & Tools

**Languages**

![Rust](https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-003B57?style=for-the-badge&logo=sqlite&logoColor=white)

**Frameworks & Runtimes**

![Tauri](https://img.shields.io/badge/Tauri-24C8DB?style=for-the-badge&logo=tauri&logoColor=black)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Tokio](https://img.shields.io/badge/Tokio-000000?style=for-the-badge&logo=rust&logoColor=white)
![Astro](https://img.shields.io/badge/Astro-BC52EE?style=for-the-badge&logo=astro&logoColor=white)
![Cranelift](https://img.shields.io/badge/Cranelift-F46623?style=for-the-badge&logo=webassembly&logoColor=white)

**Cryptography**

![X3DH + Double Ratchet](https://img.shields.io/badge/X3DH%20%2B%20Double%20Ratchet-1F6FEB?style=for-the-badge)
![ML-KEM-768](https://img.shields.io/badge/ML--KEM--768-1F6FEB?style=for-the-badge)
![Sphinx](https://img.shields.io/badge/Sphinx%20mixnet-1F6FEB?style=for-the-badge)
![ChaCha20-Poly1305](https://img.shields.io/badge/ChaCha20--Poly1305-1F6FEB?style=for-the-badge)
![Argon2id](https://img.shields.io/badge/Argon2id-1F6FEB?style=for-the-badge)
![Noise XK](https://img.shields.io/badge/Noise%20XK-1F6FEB?style=for-the-badge)
![HPKE](https://img.shields.io/badge/HPKE-1F6FEB?style=for-the-badge)

**Security & Infrastructure**

![Arch Linux](https://img.shields.io/badge/Arch%20Linux-1793D1?style=for-the-badge&logo=archlinux&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![nftables](https://img.shields.io/badge/nftables-EE0000?style=for-the-badge&logo=linux&logoColor=white)
![Wireshark](https://img.shields.io/badge/Wireshark-1679A7?style=for-the-badge&logo=wireshark&logoColor=white)
![Burp Suite](https://img.shields.io/badge/Burp%20Suite-FF6633?style=for-the-badge&logo=burpsuite&logoColor=white)
![QUIC](https://img.shields.io/badge/QUIC-005571?style=for-the-badge&logo=cloudflare&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)
![Oracle Cloud](https://img.shields.io/badge/Oracle%20Cloud-F80000?style=for-the-badge&logo=oracle&logoColor=white)

## Run a Gotham Relay

The network needs independent operators more than it needs anything else. One command, a small VPS with a public IP, and you become the diversity the path selector is waiting for:

```sh
GOTHAM_OPERATOR=<your nickname> GOTHAM_TIER=mix \
  sudo -E bash -c "$(curl -fsSL https://raw.githubusercontent.com/0x9Angel/gotham-relay/main/infra/scripts/install-relay.sh)"
```

Read [OPERATOR-GUIDE.md](https://github.com/0x9Angel/gotham-relay/blob/main/OPERATOR-GUIDE.md), [LOGGING-POLICY.md](https://github.com/0x9Angel/gotham-relay/blob/main/LOGGING-POLICY.md) and [ABUSE-FAQ.md](https://github.com/0x9Angel/gotham-relay/blob/main/ABUSE-FAQ.md) first — they say exactly what your machine would store and what it would expose, including the parts that are not flattering.

## Currently Open To

* **Alternance / internship** in offensive security or secure systems engineering (Toulouse or remote), alongside the Bachelor at Ynov.
* **Freelance** web and e-commerce work through StarsBrand — headless Shopify, Next.js, security and compliance hardening.
* **Security review swaps.** If you are building something cryptographic, I will read yours properly if you read mine.

## Get in Touch

* Security reports on Crypto/Gotham: please follow the coordinated disclosure process in each repo's `SECURITY.md` rather than opening a public issue.
* Everything else: open an issue, or reach me through [crypto-app.net](https://crypto-app.net).

---

*Building the things I wish existed. Mostly in Rust, mostly secure by default — and where it is not yet, the README says so.*
