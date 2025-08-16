
# SYLLABUS — Phase 4 Bridge & Full Phase 4 — Blocks & Deliverables (v1.2)

> **Start:** right after closing Phase 3 (post-2027-08-03)
> **Time commitment:** 5 h/day (Mon–Sat)
> **Methodology:** **PBR** (reproducible labs) + **PAD** (analysis & documentation)
> **Ethical scope:** lab-only under explicit OPSEC/Legal controls. Training purposes only.

---

## Bridge to Phase 4 (Pre-flight · 1–2 weeks)

**Purpose:** ensure technical/operational continuity before evasion/persistence/C2.

**Checklist**

* **Freeze F3:** tag stable tool/exploit versions; clean VM snapshots.
* **Blue baseline (8B placeholder):** update Sysmon/ETW, Sigma/YARA, KQL; export an initial dashboard.
* **C2 selection:** choose channel (HTTP(S)/DNS/TCP) + minimal profiles; beacon templates with controlled jitter.
* **Test environment:** VM matrix by OS/patch level; reproducible users/policies.
* **OPSEC/Legal:** review build policies, metadata hygiene, compartmentalization, explicit lab consent.

**PBR (pre-flight)**

* **PBR-BR.1:** Compatibility matrix (OS, patches, tools) with evidence.
* **PBR-BR.2:** Exportable Blue dashboard (screens + versioned rules/queries).
* **PBR-BR.3:** Blank C2 connectivity PoC (chosen channel, stable heartbeat, no operational payload).

**PAD**

* **PAD-BR:** Pre-flight report (risks, mitigations, rollback plan).

**Success criteria**

* Matrix reproducible from a clean snapshot; baseline dashboard renders; C2 heartbeat stable ≥24 h.

---

## Phase 4 — Vision & Expected Outputs

**Vision:** build an end-to-end covert operational chain: **8A Initial Access → Evasion (B1/B2) → Persistence (B3) → C2 (B4) → 8B Blue Validation**, with optional extensions (macOS/Linux EDR/Android). Close with a **Capstone** covert operation in lab.

**Expected outputs**

* Stable implant/loader with **measured** evasion.
* Two **verified** persistence methods per OS.
* Documented C2 profile exercised in a realistic lab scenario.
* Defensive rules/queries and a before/after evaluation.

---

## 8A — Initial Access & Covert Delivery (1–2 weeks)

**Objective:** build **two** reproducible delivery chains that open a C2 session with low telemetry signal.

**Content (high level)**

* Modern maldocs (VBA/XLM 4.0), Trust Center, **lab** code signing.
* Shortcuts/hosted: LNK, HTA, JS/JScript, COM Scriptlets; Mark-of-the-Web (MotW).
* AMSI (operational view): userland-hooking limits; lab-legal alternatives.
* LOLBins/WMIC/WMI: controlled execution in lab.

**PBR**

* **PBR-8A.1:** End-to-end **maldoc** chain → C2.
* **PBR-8A.2:** End-to-end **LNK/HTA (or JS)** chain → C2.

**PAD**

* **PAD-8A:** Evidence, IOC list, plausible defensive mitigations.

**Success criteria**

* Both chains reproducible from clean VM; beacon established; evidence versioned.

---

## 8B — Minimal Blue Track (1 week)

**Objective:** produce a quantitative baseline and a practical dashboard to validate bypass.

**Content**

* Core Sysmon/ETW providers; minimal YARA/Sigma (tuned); essential KQL queries.

**PBR**

* **PBR-8B.1:** 48-hour **baseline** + versioned rules/queries.

**PAD**

* **PAD-8B:** Before/after report for the 8A chains.

**Success criteria**

* Baseline + post-run diffs visible (events, detections, noise level).

---

## F4-B1 — Evasion I: Anti-analysis & Detection Surface (3 weeks)

**Objective:** reduce loader/implant signal in userland.

**Content**

* Intro anti-debug/anti-VM (pedagogical limits).
* Dynamic API resolution + name hashing.
* String/config obfuscation.
* Direct syscalls (SSN resolution; avoid aggressive unhooking).
* Sleep/time management; common artifacts.

**PBR**

* **PBR-B1.1:** Loader with dynamic resolution + obfuscated strings.
* **PBR-B1.2:** Telemetry comparison vs **8B** baseline (before/after).

**PAD**

* **PAD-B1:** Detection surfaces affected + residual risks.

**Success criteria**

* Measurable reduction in events/detections vs baseline with functional parity.

---

## F4-B2 — Evasion II: Advanced Userland Injection (3 weeks)

**Objective:** implement **two** additional techniques with a better noise profile.

**Content**

* Early-bird APC, thread-less patterns (didactic), module stomping (high level).
* Process creation options: PPID spoofing & relevant flags.
* Permission handling and post-execution cleanup.

**PBR**

* **PBR-B2.1:** Two techniques selectable via CLI.
* **PBR-B2.2:** Comparative artifact table vs **8B** baseline.

**PAD**

* **PAD-B2:** Trade-offs per technique + lab-operational guidance.

**Success criteria**

* Both techniques reproducible; artifact deltas documented and repeatable.

---

## 9B — Implant Crypto & Packer v2 (2 weeks)

**Objective:** harden comms and packaging with AEAD and light mutation.

**Content**

* AEAD (AES-GCM or ChaCha20-Poly1305): nonces, rotation, session keys.
* Config sealing & key pinning.
* Packer v2: instruction substitution, light flattening, import-hash noise.
* Compatibility/performance harness.

**PBR**

* **PBR-9B.1:** Integrate minimal crypto + packer v2 into an existing implant.

**PAD**

* **PAD-9B:** Test & security report (failures, mitigations, performance).

**Success criteria**

* Functional implant end-to-end; perf overhead & compatibility measured.

---

## F4-B3 — Cross-platform Persistence (Windows/Linux/macOS) (3 weeks)

**Objective:** establish and verify **two** persistence methods **per OS** in lab.

**Content**

* **Windows:** Run keys/RunOnce, Scheduled Tasks, Services, WMI permanent consumers, AppInit\_DLLs/IFEO *(lab only)*.
* **Linux:** systemd user services, cron.d, shell profiles; **LD\_PRELOAD** notes (controlled).
* **macOS:** LaunchAgents/LaunchDaemons, LoginItems; lab signing/notarization.

**PBR**

* **PBR-B3.1:** Two verified methods per OS with boot/execution evidence.

**PAD**

* **PAD-B3:** Risk table, typical detections, safe rollback steps.

**Success criteria**

* Survive reboot; clean rollback; detections vs stealth documented.

---

## F4-B4 — Covert C2 & Traffic Profiling (3 weeks)

**Objective:** design and operate a C2 profile with realistic patterns.

**Content**

* Client profiles: jitter, intervals, sizes, headers.
* Basic mimicry (User-Agent, paths, timings).
* JA3/JA3S & TLS fingerprint considerations (high level).
* Channel options: HTTP(S)/DNS/TCP; boundaries and risks.
* Lab infrastructure rotation.

**PBR**

* **PBR-B4.1:** Documented C2 profile measured against Blue baseline.
* **PBR-B4.2:** 72-hour run with logs + signal-vs-noise report.

**PAD**

* **PAD-B4:** Comms OPSEC & contingency plan.

**Success criteria**

* Stable 72-h run; quantifiable signal reduction without functionality loss.

---

## F4-B5 — Covert Ops & Controlled Movement (lab) (2 weeks)

**Objective:** execute minimal operational tasks without obvious signals.

**Content**

* Controlled system/inventory collection.
* WMI/PSRemoting in test env with clear limits.
* Artifact cleanup & rollback.
* TTP documentation mapped to **ATT\&CK**.

**PBR**

* **PBR-B5.1:** Playbook of **5** operational tasks with evidence + Blue evaluation.

**PAD**

* **PAD-B5:** Risk report and containment measures.

**Success criteria**

* Tasks reproducible; artifacts minimized and accounted for in Blue dashboard.

---

## Extensions 12A–12F (optional)

**12A — macOS Internals + EndpointSecurity (1 week)**
*Objective:* understand macOS security pipeline; build minimal event PoCs via EndpointSecurity.
**PBR-12A.1:** simple loader · **PBR-12A.2:** event PoC · **PAD-12A:** build/signing (ad-hoc), TCC, limits.

**12B — Linux Hardening/EDR & eBPF (1 week)**
*Objective:* grasp common Linux defenses and lab evasion tactics.
**PBR-12B.1:** simulated detections & evasion; basic Falco/eBPF rules · **PAD-12B:** findings & tuning.

**12C — Android ARM64 + Frida (basic) (1 week)**
*Objective:* introduce mobile surface with a trivial hook in a test app.
**PBR-12C.1:** simple hook · **PAD-12C:** lab notes & risks.

**12D — Hardware RE basics (1–2 weeks)**
UART/JTAG/SWD with OpenOCD/Black Magic; **CH341A (SPI flash programmer)**; **8-channel logic analyzer**.
**PBR-12D.1:** sample firmware dump/restore with verified rollback · **PAD-12D:** safe wiring guide + risk checklist.

**12E — Bus Sniffers & Firmware Pipeline (1 week)**
Python decoders for UART/I²C/SPI; hashing/compare scripts; validation harness.
**PBR-12E.1:** reproducible **dump → verify → restore** pipeline (VM) · **PAD-12E:** evidence & usage limits.

**12F — Glitching/FPGA lite (1–2 weeks)**
ChipWhisperer-Lite or iCE40 for controlled PoCs.
**PBR-12F.1:** educational PoC with guaranteed rollback · **PAD-12F:** risks & mitigations.

---

## Express Module — OPSEC/Legal (3–5 days)

**Objective:** reduce IOCs and operational risk.
**Content:** compartmentalized envs, reproducible signing, secret handling, metadata minimization.
**Deliverable:** checklist applied across all Phase 4 repos.

---

## F4-CAP — Phase 4 Capstone: Integrated Covert Operation (2–3 weeks)

**Objective:** chain **8A → Evasion (B1/B2) → Persistence (B3) → C2 (B4) → Blue Evaluation (8B)** over **96 h** in lab, with ATT\&CK mapping and a technical defense.

**Activities**

* Prepare implant/loader with packer v2 + integrated crypto.
* Execute 8A delivery chain and establish persistence.
* Operate C2 using the defined profile + B5 tasks.
* Measure signal vs noise with the Blue dashboard and tune.

**Deliverables**

* `capstone-f4/` repo with code, scripts, reproducible README.
* Evidence (logs, screenshots, hashsets), tuned rules/queries, technical defense (slides/brief).

**Success criteria**

* Chain reproducible for **96 h** in lab; measurable signal reduction vs baseline; convincing defense.

---

## Rubric — Phase 4

* **A:** All PBR/PAD complete; stable implant/loader; verified persistence; measured C2; strong Capstone with data-driven improvements.
* **B:** ≥80% PBR/PAD; one unstable component but documented; functional Capstone.
* **C:** ≥60% PBR/PAD; partial reproducibility or weak Blue validation.
* **Redo:** <60% or lack of evidence/defense.

---

## Dependencies & Suggested Order

1. **Bridge (pre-flight)** → 2) **8A** → 3) **8B** → 4) **F4-B1** → 5) **F4-B2** → 6) **9B** →
2. **F4-B3** → 8) **F4-B4** → 9) **F4-B5** → 10) **Extensions 12A–12F** (optional/parallel) → 11) **OPSEC/Legal review** → 12) **F4-CAP**

---

## Outcome

Phase 4 delivers a **complete operational chain**—implant/loader, **measured evasion**, **verifiable persistence**, 
and a **realistic C2 profile**—plus your own defensive rules/queries and a documented Blue evaluation. This is the direct foundation for **Phase 5** (kernel/firmware).
