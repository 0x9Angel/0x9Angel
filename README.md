# Hey there! I'm Angel 👋

**Cybersecurity student. Offensive security, systems and cryptography.**

## About Me

I'm a cybersecurity student (Bachelor Cybersécurité at Ynov Toulouse), working where offensive security meets secure systems engineering. I spend my time breaking things (web and infrastructure pentesting, CTFs) and building them the right way: security tools in Rust, post-quantum cryptography, and an end-to-end encrypted messenger with its own anonymity network.

> I break things to understand how they work, then I build the version that doesn't.

## Currently Building

### Amon Messenger

An end-to-end encrypted messenger for Windows, macOS and Linux, written in Rust with Tauri and React. No phone number, no account on a server. Current version: 2.5.0 (November 2026).

* Every new session opens with a post-quantum key exchange, X-Wing (ML-KEM-768 + X25519), followed by a Double Ratchet.
* Groups are bound to their members' identity keys, and every join or leave is signed. Invitation links work once by default and can be revoked.
* Local data sits in an encrypted database (SQLCipher, Argon2id). The schema is at version 49, and every migration is one-way and tested.
* Installers and updates are signed, and the app checks every update before installing it.
* **2,796 Rust tests and 574 interface tests** on the 2.5.0 release, zero clippy warnings under `-D warnings`.
* A full internal security audit in October 2026, then adversarial reviews of every fix. Those reviews found **more than a hundred defects in the fixes themselves**, all handled before the release.

### The Amon network

The transport layer underneath Amon Messenger: a Sphinx-format mixnet I designed and implemented in Rust, in the same family as Tor and Nym, tuned for messaging and post-quantum from day one.

* Hybrid X25519 + ML-KEM-768 key encapsulation (NIST FIPS 203).
* Loopix-style Poisson mixing and cover traffic, so an observer cannot tell an active user from an idle one.
* QUIC links between relays.
* Relays keep almost nothing: a short-lived replay cache of opaque packet tags, with no addresses and no content.
* A relay is admitted only when two of the three directory authorities vouch for it.

**Where the network actually stands.** Five relays are live, all on Oracle Cloud, all run by me. Path selection fails closed on operator diversity: it refuses to route through relays it cannot prove belong to different operators. So the mixnet does not route yet, by design. Until then, messages go through a mailbox host that cannot read them but sees IP addresses. Three independent operators change that.

### Open source

The network code is public under AGPL-3.0: [0x9Angel/gotham](https://github.com/0x9Angel/gotham). The app's code goes public with version 2.6.0, together with the 0.13.0 relays. A commercial licence exists for organisations that cannot use the AGPL.

### Side projects

* **Nyx**: a systems language in Rust with a Cranelift backend, affine types and lexical borrow checking.
* **Encrypted DNS client**: Oblivious DNS-over-HTTPS (RFC 9230) in Rust, with HPKE and a local stub resolver.

## Studies

* Bachelor in Cybersecurity, Ynov Toulouse (in progress).
* Bac Pro CIEL, with highest honours (2026).
* TryHackMe: Jr Penetration Tester path (December 2025), Web Fundamentals, Pre Security.
* CTFs whenever I can: pwn, crypto, web, forensics.

## How I Work

* **Measure before asserting.** If a README gives a test count, I ran the tests. If a threat model says a property holds, a test fails without it.
* **Name the residual.** My security registers have a "reduced" column, not just fixed and open. A fix that is real but partial is written up as partial.
* **A security fix is new code, and new code has new defects.** Patches get reviewed as adversarially as the original, because more than once the patch was the bug.
* **Refuse to claim what the deployment does not deliver.** The mixnet above is a good protocol on a network that cannot route yet, and I say so everywhere.

## Ask Me About

* **Offensive security**: web app pentesting (OWASP Top 10, business logic), infrastructure recon, Active Directory, Linux privilege escalation.
* **Cryptography in practice**: ratchets, Sphinx mixnets, post-quantum migration, constant-time pitfalls.
* **Rust for security tooling**: async with Tokio, parsers, fuzzing, lint policies that catch real bugs.
* **Linux**: Arch, systemd hardening (sandboxing, namespaces, seccomp).
* **CTF strategy**: always up for a team-up.

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
![Cranelift](https://img.shields.io/badge/Cranelift-F46623?style=for-the-badge&logo=webassembly&logoColor=white)

**Cryptography**

![X-Wing](https://img.shields.io/badge/X--Wing-1F6FEB?style=for-the-badge)
![ML-KEM-768](https://img.shields.io/badge/ML--KEM--768-1F6FEB?style=for-the-badge)
![Double Ratchet](https://img.shields.io/badge/Double%20Ratchet-1F6FEB?style=for-the-badge)
![Sphinx](https://img.shields.io/badge/Sphinx%20mixnet-1F6FEB?style=for-the-badge)
![Argon2id](https://img.shields.io/badge/Argon2id-1F6FEB?style=for-the-badge)
![HPKE](https://img.shields.io/badge/HPKE-1F6FEB?style=for-the-badge)

**Security & Infrastructure**

![Arch Linux](https://img.shields.io/badge/Arch%20Linux-1793D1?style=for-the-badge&logo=archlinux&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![nftables](https://img.shields.io/badge/nftables-EE0000?style=for-the-badge&logo=linux&logoColor=white)
![Wireshark](https://img.shields.io/badge/Wireshark-1679A7?style=for-the-badge&logo=wireshark&logoColor=white)
![Burp Suite](https://img.shields.io/badge/Burp%20Suite-FF6633?style=for-the-badge&logo=burpsuite&logoColor=white)
![QUIC](https://img.shields.io/badge/QUIC-005571?style=for-the-badge&logo=cloudflare&logoColor=white)
![Oracle Cloud](https://img.shields.io/badge/Oracle%20Cloud-F80000?style=for-the-badge&logo=oracle&logoColor=white)

## Run an Amon Relay

The network needs independent operators more than anything else. A small VPS with a public IP is enough, and a relay behind CGNAT works too, without port forwarding.

```sh
git clone https://github.com/0x9Angel/gotham-relay
cd gotham-relay
GOTHAM_OPERATOR=<your public nickname> GOTHAM_TIER=mix GOTHAM_ENROLL_TOKEN=<token> \
  sudo -E ./infra/scripts/install-relay.sh
```

Enrolment is closed for now: write to SoraCorporation@proton.me for a token. Read the [operator guide](https://github.com/0x9Angel/gotham-relay/blob/main/OPERATOR-GUIDE.md) and the [abuse FAQ](https://github.com/0x9Angel/gotham-relay/blob/main/ABUSE-FAQ.md) first: they say exactly what your machine would store and expose, including the parts that are not flattering.

## Get in Touch

* Security reports on Amon: SoraCorporation@proton.me, please, rather than a public issue.
* Everything else: the same address, or open an issue.

---

*Building the things I wish existed. Mostly in Rust, secure by default, and where it is not yet, the README says so.*
