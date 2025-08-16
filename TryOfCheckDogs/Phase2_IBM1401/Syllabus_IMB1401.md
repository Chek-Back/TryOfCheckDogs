
# SYLLABUS — Applied Analysis & RCE (Phase 2) — Blocks & Deliverables

> **Estimated coverage:** \~03/2026 → \~07/2026 *(adjust to Phase 1 finish)*
> **Time commitment:** 5 h/day (Mon–Sat)
> **Methodology:** **PBR** (reproducible labs) + **PAD** (analysis & documentation) · OPSEC/Legal applied *(lab-only, benign payloads)*

## Vision

Consolidate applied reversing and first userland execution paths. You’ll analyze real binaries (static/dynamic), perform single-layer manual unpacking with minimal IAT reconstruction, and build memory loaders that use classic injection techniques—while understanding modern mitigations.

## Phase 2 — Global Outputs

* Reversing report for a real binary (light obfuscation) with **reproducible** unpack.
* **PE parser** + auxiliary analysis utilities.
* Userland loader with **≥2** execution techniques.
* Intro **process hollowing** PoC in lab.
* Disciplined documentation (PAD) + curated evidence for bug bounty.

## Relation to other phases/modules

* Close **B8** with controlled in-memory execution.
* **Phase 3** follows (internals & exploitation, userland→kernel).
* **8A/8B** are inserted **before Phase 4** as the pre-flight for evasion/C2 (Initial Access + Minimum Blue Track).

---

## 0B04 — Applied Reversing I: Tooling, Methodology & Basic Unpacking

**Duration:** 6 weeks · **Goal:** master a static/dynamic pipeline (Ghidra/IDA Free, rizin/Cutter, x64dbg/WinDbg), handle trivial anti-analysis, and perform single-layer manual unpacking (e.g., UPX) with minimal **IAT** reconstruction.

**Content**

* **Static:** strings/signatures, CFG, calling conventions, struct recovery, common patterns.
* **Dynamic:** breakpoints, memory map, dump & patch, basic relocations; debugger pitfalls.
* **Anti-analysis (intro):** `IsDebuggerPresent`, PEB `BeingDebugged`, timing checks; safe bypasses in lab.
* **Packers 101:** UPX/variants; OEP discovery; minimal **IAT** reconstruction (tooling or scripts).
* **Support scripting:** Python for parsers/decoders and dump automation.

**PBR**

* **PBR-0.1:** Reversing report (small binary w/ obfuscated strings): function map, flows, decision points.
* **PBR-0.2:** Manual unpack (UPX or similar): **clean dump** + reconstructed **IAT**; hash comparison; debugger loads.
* **PBR-0.3:** String/config decoder (simple XOR/RC4) with unit tests.

**PAD**

* **PAD-0:** Methodology (step-by-step), screenshots, before/after checksums, issues & mitigations.

**Success criteria**

* Executable dump without crashes; **functional IAT**; feasible static analysis on the result.
* Report is reproducible by third parties using your repo/lab.

---

## 1B04 — Deep PE, Windows API & In-Memory Loaders

**Duration:** 5 weeks · **Goal:** understand **PE** in practice (headers, sections, imports/exports, relocations, TLS) and build loaders that execute benign payloads in memory, progressing to **basic manual mapping**.

**Content**

* **PE fundamentals:** DOS/NT headers, **sections**, imports/exports, relocations, TLS callbacks. *(Use “sections”; “segments” are ELF terminology.)*
* **Proc/threads/memory API:** `VirtualAlloc{Ex}`, `WriteProcessMemory`, `Create{Remote}Thread`, `VirtualProtect` (and variants).
* **Minimal loader:** allocate & copy payload, set permissions, controlled jump, cleanup & error handling.
* **Basic manual map:** load a **minimal DLL** without `LoadLibrary` (selective import resolution, essential relocations, no advanced TLS).
* **Safety & bugs:** permissions/offsets/alignment; avoiding silent crashes.
* **Inspection:** Process Hacker, PE-bear, PE-sieve for validation.

**PBR**

* **PBR-1.1:** **PE parser**: print key headers, sections, imports; simple integrity checks.
* **PBR-1.2:** Benign shellcode loader in **local** process with cleanup & robust errors.
* **PBR-1.3:** Intro **manual map** of a minimal DLL + execution of an exported function.

**PAD**

* **PAD-1:** Loader design, memory diagrams, risks, and tests with strong error handling.

**Success criteria**

* Stable loader that runs benign payloads in lab (no external AV reliance).
* Functional manual map for a controlled DLL with clear execution evidence.

---

## 2B04 — Userland Execution Paths & Modern Mitigations

**Duration:** 5 weeks · **Goal:** implement 2–3 classic userland techniques and understand DEP/ASLR/CFG and handle/process policies; prepare ground for evasion and **8A**.

**Content**

* **Classic injection:** `CreateRemoteThread` + `LoadLibrary`.
* **APC queueing:** including early-bird; synchronization/failure points.
* **Process hollowing (intro)** vs module stomping (differences & trade-offs).
* **Staging options:** PPID spoofing; relevant `CreateProcess` flags (lab only).
* **Light obfuscation:** dynamic API resolution by hash; string hiding.
* **Mitigations & surfaces:** DEP/ASLR/CFG, signing, antimalware, common detection surfaces.
* **Syscalls (intro):** for basic ops only (no deep unhooking in Phase 2).

**PBR**

* **PBR-2.1:** Multi-mode loader (CLI selector: **CRT+LL** / **APC**) with controlled logging.
* **PBR-2.2:** **Hollowing PoC** against a lab binary with evidence & **safe rollback**.
* **PBR-2.3:** **Trace comparison**: artifact deltas per technique under a fixed checklist.

**PAD**

* **PAD-2:** Analysis of encountered mitigations, detection surfaces, and improvement plan toward **Phase 3** / **8A/8B**.

**Success criteria**

* At least **two** techniques work reproducibly in the lab.
* Comparative report with full evidence and checklists.

---

## EX0B01 — Express Module F2 (in parallel to 0B04–2B04)

**Duration:** \~1 effective week (1–2 h slots) · **Goal:** accelerate analysis/testing with custom utilities.

**Content & Deliverable**

* Parsing scripts (PE/ELF), string/config extractors.
* Loader harness (in/out, logs, timers) + test dataset.
* **PBR-EX.1:** Versioned `tools/` folder with documented scripts & basic tests.
* **PAD-EX:** Short usage notes & limits.

---

## Phase 2 — Grading Rubric

* **A:** Reversing report with clean unpack; **usable PE parser**; loader with **≥2** techniques; stable hollowing PoC; reproducible docs.
* **B:** ≥80% PBR/PAD; one unstable technique or limited parser; documentation sufficient.
* **C:** ≥60% PBR/PAD; partial reproducibility.
* **Redo:** <60% or severe instability in loaders/injection.
