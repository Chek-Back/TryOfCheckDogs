
> Estimated coverage: **\~03/2026 → \~07/2026**
> Commitment: **5 h/day (Mon–Sat)**
> Methodology: **PBR** (reproducible labs) + **PAD** (analysis & documentation)

---

# **0B04 — Applied Reversing I: Tools, Methodology & Basic Unpack**

Target duration: **6 weeks**. Outcomes: reversing report, manual one-layer unpack with reconstructed IAT, string/config decoder.

### **Stack 1 — Static Flow (mind-map & triage)**

**Week 0**

* Ghidra/rizin: strings, signatures, CFG, and calling conventions
* First function/dependency map

**Week 1**

* Struct recovery and basic typing
* **PBR-0.1**: Reversing report design (outline + evidence)

### **Stack 2 — Dynamic Flow & Trivial Anti-Analysis**

**Week 2**

* x64dbg/WinDbg: breakpoints, memory map, dumps
* Simple anti-debug (`IsDebuggerPresent`, PEB flags) and effect logging
* **PBR-0.2**: Reproducible dynamic session (dataset + notes)

### **Stack 3 — Packers 101 & Minimal IAT**

**Week 3**

* UPX and variants; OEP discovery without “magic recipes”
* Basic IAT reconstruction with lab tools

**Week 4**

* Dump validation (load in debugger + hashes)
* **PBR-0.3**: Manual unpack of lab sample (clean dump + IAT)

### **Stack 4 — Supporting Scripting & Documentation**

**Week 5**

* Python: string/config decoder (simple XOR/RC4) with tests
* **PBR-0.4**: Working decoder + minimal test suite
* **PAD-0**: methodology, checksums, issues & mitigations

---

# **1B04 — Deep PE, Windows API & In-Memory Loaders**

Target duration: **5 weeks**. Outcomes: usable PE parser, stable local loader, introductory manual mapping.

### **Stack 1 — PE Fundamentals + Parser**

**Week 0**

* PE DOS/NT headers, sections, imports/exports, reloc/TLS
* **PBR-1.1**: Parser that lists headers, sections, and imports + basic verification

### **Stack 2 — Local Loader (benign shellcode)**

**Week 1**

* VirtualAlloc/Protect, payload copy, controlled jump, cleanup
* **PBR-1.2**: Local loader with error handling and rollback

### **Stack 3 — Basic Manual Mapping (minimal DLL)**

**Week 2**

* Selective import resolution, essential relocs, entrypoint
* **PBR-1.3**: Manual map of a minimal DLL and exported function execution

### **Stack 4 — Stability, Inspection & PAD**

**Week 3**

* PE-sieve / Process Hacker / PE-bear to validate artifacts

**Week 4**

* **PAD-1**: loader design, memory diagrams, risks & tests

---

# **2B04 — Userland Execution Paths & Modern Mitigations**

Target duration: **5 weeks**. Outcomes: multi-mode loader, lab hollowing PoC, trace comparison vs mitigations.

### **Stack 1 — Classic Injection (CRT + LoadLibrary)**

**Week 0**

* CRT+LL mode design, controlled logging, cleanup
* **PBR-2.1**: Working CRT+LL mode (lab)

### **Stack 2 — APC Queueing**

**Week 1**

* APC/early-bird; synchronization and common failure points
* **PBR-2.2**: Operational APC mode with evidence

### **Stack 3 — Introductory Hollowing**

**Week 2**

* Differences vs module stomping; rollback checklist
* **PBR-2.3**: Hollowing PoC against a lab binary

### **Stack 4 — Mitigations & Comparison**

**Week 3**

* DEP/ASLR/CFG, PPID spoofing, and common detection surfaces

**Week 4**

* **PBR-2.4**: Technique-by-technique trace comparison
* **PAD-2**: mitigation analysis and improvement plan

---

# **EX0B01 — Express Module F2 (in parallel with 0B04–2B04)**

Duration: **1 effective week** split into 1–2 h slots. Outcomes: `tools/` with scripts and a harness.

### **Stack 1 — Automation & Auxiliary Tooling**

**Weeks 0–15 (interleaved slots)**

* Parsing scripts (PE), string/config extractors
* Loader harness (in/out, logs, timers) and test datasets
* **PBR-EX.1**: Versioned & tested `tools/`
* **PAD-EX**: short usage notes and limits

---

## **Phase 2 Evaluation Rubric**

* **A:** Reversing report with clean unpack; usable PE parser; loader with ≥2 techniques; stable hollowing PoC; reproducible documentation.
* **B:** ≥80% PBR/PAD; one unstable technique or limited parser.
* **C:** ≥60% PBR/PAD; partial reproducibility.
* **Redo:** <60% or severe instability.

> Necessary (but boring) note: all of this lives in **lab VMs** with **benign** payloads and your own telemetry. Never target real systems. If you break something, let it be your VM—with a snapshot.

---

# **3B02 — Phase 2 → Phase 3 Bridge (technical close-out & warm-up)**

Target duration: **2 weeks**. Everything in **lab**, **benign** payloads, snapshots ready.

### **Stack 1 — Phase 2 Close-out & “Audit-Ready” Evidence**

**Week 0 — 2026-06-08 → 2026-06-13**

* **Mon 08 Jun** · Clean re-run of **PBR-1.2** (local loader) and **PBR-2.1** (CRT+LL) in a fresh VM · **5 h**
* **Tue 09 Jun** · Capture baseline telemetry (Process Hacker/PE-sieve) and export CSV · **5 h**
* **Wed 10 Jun** · Minimal refactor: error handling and deterministic logs · **5 h**
* **Thu 11 Jun** · Curated evidence: hashes, versions, traces, and environment notes · **5 h**
* **Fri 12 Jun** · **PBR-3.1** Phase 2 evidence pack (loader + CRT+LL) · **5 h**
* **Sat 13 Jun** · **PAD-3 (partial)**: reproducibility checklist + lessons learned · **5 h**

**Week 1 — 2026-06-15 → 2026-06-20**

* **Mon 15 Jun** · Re-run **PBR-2.2** (APC) and **PBR-2.3** (hollowing) with trace scripts · **5 h**
* **Tue 16 Jun** · Technique artifact comparison (tables and diffs) · **5 h**
* **Wed 17 Jun** · Repo cleanup: `tools/`, `scripts/`, datasets, and concise READMEs · **5 h**
* **Thu 18 Jun** · Reproducibility audit by an “imaginary third party” · **5 h**
* **Fri 19 Jun** · **PBR-3.2** “Ready-to-hand-off” package (repos + evidence) · **5 h**
* **Sat 20 Jun** · **PAD-3 (final)**: Phase 2 summary, gaps, and Phase 3 roadmap · **5 h**

---

### **Stack 2 — Phase 3 Warm-Up (userland internals & exploitation harness)**

**Week 0 — 2026-06-08 → 2026-06-13**

* **Mon 08 Jun** · WinDbg/x64dbg: symbols configured and session checklist · **5 h**
* **Tue 09 Jun** · PEB/TEB and memory layout: quick notes and cheat sheets · **5 h**
* **Wed 10 Jun** · Skeletons for **region-map** and **handle-map** (userland) · **5 h**
* **Thu 11 Jun** · Lab targets selected for F3-B1/B2 · **5 h**
* **Fri 12 Jun** · **PBR-3.3** “Warm-up F3” kit (scripts + docs) · **5 h**
* **Sat 13 Jun** · Technical buffer for adjustments · **5 h**

**Week 1 — 2026-06-15 → 2026-06-20**

* **Mon 15 Jun** · Basic harness for **educational ROP** (pattern/cyclic) · **5 h**
* **Tue 16 Jun** · Write-up templates for Phase 3 (PAD structure) · **5 h**
* **Wed 17 Jun** · Test plan for lab info-leaks (slow & steady) · **5 h**
* **Thu 18 Jun** · Cross-validation: symbol loading and scripts in a clean VM · **5 h**
* **Fri 19 Jun** · **PBR-3.4** Phase 3 enablement: one-command bootstrapping · **5 h**
* **Sat 20 Jun** · High-rigor buffer: dry-run of an F3-B1 session · **5 h**

---

## **Bridge Deliverables**

* **PBR-3.1** Phase 2 evidence pack (loader + CRT+LL)
* **PBR-3.2** “Ready-to-hand-off” package (repos + traces + README)
* **PBR-3.3** “Warm-up F3” kit (region/handle-map skeletons, symbols, cheat sheets)
* **PBR-3.4** Auto-bootstrapped Phase 3 environment (scripts + minimal datasets)
* **PAD-3** Bridge report: Phase 2 status, risks, and Phase 3 entry plan

## **Exit Criteria for Phase 3**

* **All** Phase 2 techniques reproducible in a clean VM.
* Repos with minimal documentation and startup scripts.
* Symbols and harnesses ready for F3-B1/B2—no setup drama.
