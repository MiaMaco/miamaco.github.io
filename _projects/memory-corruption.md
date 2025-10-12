---
title: "Memory Corruption: Buffer Overflow & Format String Attacks"
date: 2025-10-12
summary: "Explored buffer overflow and format string vulnerabilities in 32-bit Linux binaries using controlled POCs."
tags: [memory-corruption, x86, buffer-overflow, format-string, gdb]
layout: default
---

## Overview

This project explores classic memory corruption vulnerabilities — specifically **buffer overflow** and **format string** attacks — by building proof-of-concept exploits for intentionally vulnerable 32-bit binaries.

Stack protections (ASLR, stack canaries, etc.) were disabled to allow low-level exploitation for educational purposes only.

> ⚠️ **Note:** All demonstrations are for defensive research and educational use. No functional exploit payloads are published.

---

## Tools & Setup

- Target: 32-bit Linux binaries
- Compiler: `gcc -m32 -fno-stack-protector -z execstack`
- Tools: `gdb`, `pwndbg`, `objdump`, `ltrace`, `strace`, `readelf`

---

## What I Did

- Identified vulnerable code patterns (unsafe buffer handling, unvalidated format strings)
- Analyzed memory layout using `gdb` and crafted stack diagrams
- Built controlled proof-of-concept exploits
- Documented key exploitation principles and mitigations

---

## Lessons Learned

- Buffer overflows and format string vulnerabilities can be exploited when protections are disabled
- Modern systems use multiple defenses (stack canaries, ASLR, NX) to prevent real-world exploitation
- Secure coding practices and validation are critical for memory safety

---

## Repository

[🔗 GitHub Repo (Sanitized Source)](https://github.com/yourusername/memory-corruption-demo)

