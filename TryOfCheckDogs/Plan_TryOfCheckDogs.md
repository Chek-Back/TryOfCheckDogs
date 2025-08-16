# PLAN — Try Of Check Dogs (TOCD)

> **Author:** Denis Pérez
> **Last updated:** 2025-08-16

---

## 1) Vision & Goal

Achieve professional competence in **Reverse Engineering** and **Malware Development**. The expected outcome is a portfolio of verifiable projects: exploits and post-exploitation, C2 implants with persistence, evasion techniques validated via telemetry, and documentation aligned with professional standards.

---

## 2) Route Principles

* **Hands-on first:** every block includes reproducible labs (**PBR**) and technical documentation (**PAD**).
* **Objective measurement:** defensive baseline (Sysmon/ETW, YARA/Sigma, KQL) to prove evasion with data.
* **Ethics & isolation:** all work is performed in an isolated lab under **OPSEC/Legal** controls.
* **Realistic progression:** from fundamentals to kernel/UEFI without artificial jumps.

---

## 3) Master Schedule (real dates)

* **TOCD Segment 1:** **2025-08-14 → 2026-09-14**
  Intensive self-study (5 h/day, Mon–Sat). PBR/PAD deliverables per block.
* **Break:** **2026-09-14 → 2026-09-20**
  Six-day pause. Small backlogs if needed to maintain pace.
* **Bug Bounty + University:** **2026-09-21 → 2027-07-21**
  First 9 months of university in parallel with bug hunting (4–5 h/day); TOCD via short **backlogs** (6–8 h/week).
* **TOCD resumes without pauses:** **from 2027-08-03** until all phases are complete.
* **Estimated TOCD end:**

  * Base (53 months): **2029-12-03**
  * With added modules (8A, 8B, 9B, 12A–F, OPSEC/Legal): **between 2030-01-18 and 2030-02-03**

> The **JHU** master’s will start once I secure a job that makes it sustainable, without interrupting TOCD.

---

## 4) Coordinated Tracks

1. **TOCD (self-directed):** custom, progressive curriculum focused on systems, RE, exploit dev, and evasion.
2. **University (TEP PUCMM):** formal cybersecurity foundation. Start: **2026-09**. Estimated duration: \~2 years (through 2028).
3. **Master’s (JHU):** to be pursued after securing RE/maldev-related employment.

---

## 5) Phase Structure (summary)

* **Phase 1 — Systems & Programming Fundamentals**
  Linux/CLI, C/C++, assembly, architecture. Goal: low-level fluency.
* **Phase 2 — Applied Analysis & RCE**
  Applied reversing, payloads, and client-side surface.
* **Phase 3 — Advanced RE & OS Internals**
  Userland and kernel internals, advanced exploit dev, integrative projects.
* **Phase 4 — Evasion, Persistence & Operations**
  Anti-debug/anti-VM, unhooking, direct syscalls, hollowing, module stomping, C2, and covert operations.

  * **Block 8A (new):** Initial Access & covert delivery (maldocs, LNK/HTA/JS, AMSI, LOLBins, WMI).
  * **Block 8B (new):** Minimum Blue Track (Sysmon/ETW, YARA/Sigma, KQL) for baseline & validation.
  * **Block 9B (new):** Implant crypto & Packer v2 (proper AEAD, key rotation, light mutation).
* **Phase 5 — Advanced Persistence & Firmware**
  Rootkits/bootkits, UEFI, and a final project with technical defense.

  * **Extensions 12A–F (new):** macOS internals + EndpointSecurity; Linux EDR/eBPF; Android ARM64 + basic Frida.
* **Express Module (new):** **OPSEC/Legal** for secure builds, compartmentalization, and usage limits.

---

## 6) Time Commitments

* **Before university:** 5 h/day, Mon–Sat, on TOCD.
* **Bug Bounty + university (9 months):** 4–5 h/day on bugs; TOCD via backlogs of 6–8 h/week.
* **From 2027-08-03:** TOCD continues without pauses until completion (full pace).

---

## 7) Goals & KPIs

**Technical goals**

* Close each block’s PBR/PAD with reproducible evidence (screenshots, hashes, IOC list, report).
* Capstone with full chain: initial access → execution → persistence/rootkit → C2 → Blue validation.

**Progress KPIs**

* Effective lab hours per week.
* Detection rate vs attempts in 8B (signal/noise).
* PBR/PAD closed per block and per phase.
* Public bug bounty cases during 2026–2027 (target: 1–2/month).

**Financial goal**

* Operating target: **USD 8,000–18000,000** during the bug bounty window (2026-09-21 → 2027-07-21) to support living expenses and studies.
* Cushion of 3–4 months’ expenses; logging and post-mortems for each case.

---

## 8) Backlogs During University

During the 9 months of bug bounty + university, I’ll keep TOCD moving with weekly backlogs of 6–8 h:

* Quick reviews of completed labs to avoid skill decay.
* Mini-exercises for 8A/8B (rule tuning, new delivery chains).
* Toolchain and documentation maintenance.

---

## 9) Risk Management

* **Academic overload:** prioritize critical deliverables and limit TOCD to backlogs.
* **Income volatility:** savings plan and a steady bug bounty reporting pipeline.
* **Scope drift:** no new modules until 8A/8B/9B/12A–C are closed.
* **Ethics/Legal:** lab-only testing and explicit consent in controlled cases.

---

## 10) OPSEC & Legal

* Campaign-level project compartmentalization.
* Metadata minimization (PDB/RSDS, timestamps, FileVersionInfo).
* Signing and artifact control where applicable.
* Usage policies and consent documentation.

---

## 11) Versioning & Control

* Separate repos per phase/block.
* Issues and Milestones aligned to KPIs.
* Changelog/lab log with dated entries (ISO 8601 format and local time).

---

## 12) High-Level Calendar (summary)

* **2025-08-14 → 2026-09-14:** Continuous TOCD (5 h/day).
* **2026-09-14 → 2026-09-20:** Break (6 days).
* **2026-09-21 → 2027-07-21:** Bug Bounty + University (TOCD via backlogs).
* **From 2027-08-03:** TOCD without pauses until completion (ETA 2029-12-03 / 2030-01-18 → 2030-02-03).

---

## 13) Expected Outcome

By the end, I’ll have operational RE/maldev skills, a portfolio of verifiable projects, evidence of measured evasion via telemetry, 
and professional-grade documentation—ready for a specialized role and the JHU master’s.
