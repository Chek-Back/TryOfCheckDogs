
# SYLLABUS — Phase 4 Bridge & Full Phase 4 — Blocks & Deliverables (v1.1)

> **Start:** immediately after closing Phase 3 (post-2027-08-03)
> **Time commitment:** 5 h/day (Mon–Sat)
> **Methodology:** **PBR** (reproducible labs) + **PAD** (analysis & documentation)
> **Ethical scope:** **lab-only**, under explicit **OPSEC/Legal** controls. Training purposes only.
> 
---

## Bridge to Phase 4 (pre-flight, 1–2 weeks)

**Purpose:** ensure technical/operational continuity before evasion/persistence/C2.

**Checklist**

* **Freeze F3:** tag stable tool/exploit versions; clean VM snapshots.
* **Blue baseline (8B placeholder):** update Sysmon/ETW, Sigma/YARA, KQL; export an initial dashboard.
* **C2 selection:** choose channel (HTTP(S)/DNS/TCP) and minimal profiles; beacon templates with controlled jitter.
* **Test environment:** VM matrix by OS/patch level; reproducible users/policies.
* **OPSEC/Legal:** review build policies, metadata hygiene, compartmentalization, and explicit lab consent.

**PBR (pre-flight)**

* **PBR-BR.1:** Compatibility matrix (OS, patches, tools) with evidence.
* **PBR-BR.2:** Exportable Blue dashboard (screens + versioned rules/queries).
* **PBR-BR.3:** Blank C2 connectivity PoC (chosen channel, stable heartbeat, **no** operational payload).

**PAD**

* **PAD-BR:** Pre-flight report with risks and mitigations.

---

## Phase 4 — Vision & expected outputs

**Vision:** build an end-to-end covert operational chain: **8A Initial Access → Evasion/Obfuscation → Persistence → C2 → 8B Blue Validation**, with optional extensions on macOS/Linux EDR and Android. Close with a **Capstone** covert operation in lab.

**Expected outputs**

* Stable implant/loader with **measured** evasion.
* **Two** persistence methods **per OS** verified.
* Documented C2 profile exercised in a realistic lab scenario.
* Defensive rules/queries and before/after comparative evaluation.

---

## 8A — Initial Access & Covert Delivery (1–2 weeks)

**Objective:** build **two** reproducible delivery chains that open a C2 session with low telemetry signal.

**Content (high-level)**

* Modern maldocs (VBA/XLM 4.0), Trust Center, code signing (lab).
* Shortcuts/hosted: **LNK**, **HTA**, **JS/JScript**, COM Scriptlets; Mark-of-the-Web.
* **AMSI** (operational view): userland hooking limits; lab-legal alternatives.
* **LOLBins/WMIC/WMI:** controlled execution in lab.

**PBR**

* **PBR-8A.1:** End-to-end maldoc chain → C2.
* **PBR-8A.2:** End-to-end LNK/HTA (or JS) chain → C2.

**PAD**

* **PAD-8A:** Evidence, IOC list, and plausible defensive mitigations.

---

## 8B — Minimal Blue Track (1 week)

**Objective:** quantitative baseline and a practical dashboard to validate bypass.

**Content**

* Core Sysmon/ETW providers.
* Minimal YARA/Sigma rules with tuning.
* Essential KQL queries.

**PBR**

* **PBR-8B.1:** 48-hour baseline + versioned rules/queries.

**PAD**

* **PAD-8B:** Before/after report for the 8A chains.

---

## F4-B1 — Evasion I: anti-analysis & detection surface (3 weeks)

**Objective:** reduce loader/implant signal in userland.

**Content**

* Intro to anti-debug/anti-VM and pedagogical limits.
* **Dynamic API resolution** and name hashing.
* **String/config obfuscation**.
* **Direct syscalls** (SSN resolution; avoid aggressive unhooking details).
* Sleep/time management and common artifacts.

**PBR**

* **PBR-B1.1:** Loader with dynamic resolution + obfuscated strings.
* **PBR-B1.2:** Telemetry comparison vs 8B baseline (before/after).

**PAD**

* **PAD-B1:** Detection surfaces affected and residual risks.

---

## F4-B2 — Evasion II: advanced userland injection (3 weeks)

**Objective:** implement **two** additional techniques with a better noise profile.

**Content**

* **APC early-bird**, **thread-less**, **module stomping** (didactic view).
* Process creation options: **PPID spoofing** and relevant flags.
* Permission handling and post-execution cleanup.

**PBR**

* **PBR-B2.1:** Two techniques selectable via CLI.
* **PBR-B2.2:** Comparative artifact table vs 8B baseline.

**PAD**

* **PAD-B2:** Trade-offs per technique + lab operational guidance.

---

## 9B — Implant crypto & Packer v2 (2 weeks)

**Objective:** harden comms and packaging with **AEAD** and light mutation.

**Content**

* **AEAD** (AES-GCM or ChaCha20-Poly1305): nonces, rotation, session keys.
* Config sealing and key pinning.
* **Packer v2:** instruction substitution, light flattening, import-hash noise.
* Compatibility/performance harness.

**PBR**

* **PBR-9B.1:** Integrate minimal crypto + packer v2 into an existing implant.

**PAD**

* **PAD-9B:** Test & security report (failures, mitigations, performance).

---

## F4-B3 — Cross-platform persistence (Windows/Linux/macOS) (3 weeks)

**Objective:** establish and verify **two** persistence methods **per OS** in lab.

**Content**

* **Windows:** Run keys/RunOnce, Scheduled Tasks, Services, WMI permanent consumers, AppInit\_DLLs/IFEO *(lab)*.
* **Linux:** systemd user services, `cron.d`, shell profiles; **LD\_PRELOAD** notes *(controlled)*.
* **macOS:** LaunchAgents/LaunchDaemons, LoginItems; signing/notarization *(lab)*.

**PBR**

* **PBR-B3.1:** Two verified methods per OS with boot/execution evidence.

**PAD**

* **PAD-B3:** Risk table, typical detections, safe rollback steps.

---

## F4-B4 — Covert C2 & traffic profiling (3 weeks)

**Objective:** design and operate a C2 profile with realistic traffic patterns in lab.

**Content**

* Client profiles: **jitter**, intervals, sizes, headers.
* Basic client mimicry (UA, routes, timings).
* **JA3/JA3S** and TLS fingerprint considerations (high-level).
* Channel options: **HTTP(S)/DNS/TCP**; boundaries and risks.
* Lab infrastructure rotation.

**PBR**

* **PBR-B4.1:** Documented C2 profile measured against Blue baseline.
* **PBR-B4.2:** 72-hour run with logs + signal-vs-noise report.

**PAD**

* **PAD-B4:** Comms OPSEC & contingency plan.

---

## F4-B5 — Covert ops & controlled movement (lab) (2 weeks)

**Objective:** execute minimal operational tasks without obvious signals in lab.

**Content**

* Controlled system/inventory collection.
* **WMI/PSRemoting** in test environment with clear limits.
* Artifact cleanup & rollback.
* TTP documentation mapped to **ATT\&CK**.

**PBR**

* **PBR-B5.1:** Playbook of **5** operational tasks with evidence + Blue evaluation.

**PAD**

* **PAD-B5:** Risk report and containment measures.

---

## Extensions 12A–12F (optional)

**12A — macOS Internals + EndpointSecurity (1 week)**
*Objective:* understand macOS security pipeline; build minimal event PoCs via EndpointSecurity.
**PBR-12A.1:** simple loader; **PBR-12A.2:** event PoC; build guide.
**PAD-12A:** notes on notarization/ad-hoc, TCC, and limits.

**12B — Linux Hardening/EDR & eBPF (1 week)**
*Objective:* grasp common Linux defenses and lab evasion tactics.
**PBR-12B.1:** simulated detections & evasion; basic Falco/eBPF rules.
**PAD-12B:** findings & tuning report.

**12C — Android ARM64 + Frida (basic) (1 week)**
*Objective:* introduce mobile surface with a trivial hook in a test app.
**PBR-12C.1:** simple hook; **PAD-12C:** lab notes & risks.

**12D — Hardware RE basics (1–2 weeks)**
UART/JTAG/SWD with OpenOCD/Black Magic; **CH341A** for SPI flash; 8-channel logic analyzer.
**PBR-12D.1:** sample firmware dump/restore with verified rollback.
**PAD-12D:** safe wiring guide + risk checklist.

**12E — Bus sniffers & firmware pipeline (1 week)**
Python decoders for UART/I²C/SPI; hashing/compare scripts; validation harness.
**PBR-12E.1:** reproducible `dump → verify → restore` pipeline in VM.
**PAD-12E:** evidence & usage limits.

**12F — Glitching/FPGA lite (1–2 weeks)**
ChipWhisperer-Lite or iCE40 for controlled PoCs.
**PBR-12F.1:** educational PoC with guaranteed rollback.
**PAD-12F:** risks & mitigations.

---

## Express Module — OPSEC/Legal (3–5 days)

**Objective:** reduce IOCs and operational risk.
**Content:** compartmentalized environments, reproducible signing, secret handling, metadata minimization.
**Deliverable:** checklist applied across all Phase 4 repos.

---

## F4-CAP — Phase 4 Capstone: integrated covert operation (2–3 weeks)

**Objective:** chain **8A → Evasion (B1/B2) → Persistence (B3) → C2 (B4) → Blue Evaluation (8B)** over **96 h** in lab, with ATT\&CK mapping and a technical defense.

**Activities**

* Prepare implant/loader with **packer v2** and integrated crypto.
* Execute 8A delivery chain and establish persistence.
* Operate C2 using the defined profile and B5 tasks.
* Measure signal vs noise with the Blue dashboard and tune.

**Deliverables**

* `capstone-f4/` repo with code, scripts, reproducible `README`.
* Evidence (logs, screenshots, hashsets), tuned rules/queries, **technical defense** (slides/brief).

**Success criteria**

* Chain reproducible for **96 h** in lab, measurable signal reduction vs baseline, convincing defense.

---

## Rubric — Phase 4

* **A:** All PBR/PAD complete; stable implant/loader; verified persistence; measured C2 profile; strong Capstone with data-driven improvements.
* **B:** ≥80% PBR/PAD; one unstable component but documented; functional Capstone.
* **C:** ≥60% PBR/PAD; partial reproducibility or weak blue validation.
* **Redo:** <60% or lack of evidence/defense.

---

## Dependencies & suggested order

1. Bridge (pre-flight)
2. **8A → 8B**
3. **F4-B1 → F4-B2**
4. **9B** (crypto/packer v2)
5. **F4-B3 → F4-B4 → F4-B5**
6. **Extensions 12A–12F** (as hardware/interest allow)
7. **OPSEC/Legal** (review & sign)
8. **F4-CAP**

---

## Outcome

Phase 4 delivers a complete operational chain with implant/loader, **measured** evasion, verifiable persistence, and a C2 profile with realistic traffic—plus your own defensive rules/queries. This becomes the direct foundation for **Phase 5** (kernel/firmware).
