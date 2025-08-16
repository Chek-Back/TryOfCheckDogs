
# Phase 2 — Applied Analysis & Early Execution Paths (RCE)

> Coverage: **\~03/2026 → \~07/2026**
> Commitment: **5 h/day (Mon–Sat)**
> Methodology: **PBR** (reproducible labs) + **PAD** (analysis & documentation) · OPSEC/Legal applied

## Table of Contents

1. [Phase Objective](#phase-objective)
2. [Scope & Expected Outcomes](#scope--expected-outcomes)
3. [Blocks & Content](#blocks--content)

   * [B6: Applied Reversing I + Unpack](#b6-applied-reversing-i--unpack)
   * [B7: Deep PE & In-Memory Loaders](#b7-deep-pe--in-memory-loaders)
   * [B8: Userland Execution Paths & Mitigations](#b8-userland-execution-paths--mitigations)
   * [Express Module F2: Automation & Tooling](#express-module-f2-automation--tooling)
4. [Global Deliverables](#global-deliverables)
5. [Success Criteria](#success-criteria)
6. [Bridge to Phase 3 & Modules 8A/8B](#bridge-to-phase-3--modules-8a8b)

---

## Executive Summary

**Purpose.** Consolidate **applied reversing** (static/dynamic), practice **manual unpacking** of a simple layer with minimal **IAT** reconstruction, and build **in-memory loaders** (local shellcode, basic manual mapping). Add **userland injection** techniques (**CRT+LoadLibrary**, **APC**, introductory **hollowing**) with attention to modern mitigations (**DEP/ASLR/CFG**).

**Outcomes on Completion.**

* Reversing report on a real binary (light obfuscation) with a **reproducible unpack**.
* A custom **PE parser** and supporting analysis utilities.
* A **userland loader** with **≥2 techniques** (e.g., CRT+LL and APC) and a lab **process hollowing** PoC.
* Disciplined documentation (PAD) and evidence prepared for bug bounty work.

---

## Blocks & Content

### B6: Applied Reversing I + Unpack

* **Content:** Static/dynamic pipeline (Ghidra/IDA, x64dbg/WinDbg), simple anti-analysis (`IsDebuggerPresent`, PEB `BeingDebugged`, timing checks), **UPX/packers 101**, OEP discovery, **IAT** reconstruction.
* **PBR:** (1) Reversing report with function map; (2) **Manual unpack** with clean dump + working IAT; (3) String/config decoder script (simple XOR/RC4).
* **PAD:** Step-by-step method, before/after checksums, and mitigations.

### B7: Deep PE & In-Memory Loaders

* **Content:** DOS/NT headers, sections, imports/exports, relocations, **TLS**; process/memory API (`VirtualAlloc{Ex}`, `WriteProcessMemory`, `Create{Remote}Thread`, `VirtualProtect`); **minimal loader** and basic **manual mapping**.
* **PBR:** (1) **PE parser** (headers, sections, imports); (2) **Benign shellcode loader** in the **local** process with cleanup and error handling; (3) Intro **manual map** of a minimal DLL.
* **PAD:** Loader design, memory diagrams, risks, and test plan.

### B8: Userland Execution Paths & Mitigations

* **Content:** `CreateRemoteThread + LoadLibrary`, **APC** (incl. early-bird), basic **process hollowing** vs module stomping, **PPID spoofing**; light obfuscation (dynamic API resolution by hash, hidden strings); impact of **DEP/ASLR/CFG**.
* **PBR:** (1) **Multi-mode loader** (CLI selector: CRT+LL / APC) with logging; (2) **Hollowing PoC** against a lab binary with safe rollback; (3) **Trace & artifact comparison** across techniques.
* **PAD:** Analysis of mitigations, detection surfaces, and improvement plan.

### Express Module F2: Automation & Tooling

* **Content:** Parsing scripts (PE/ELF), string/config extractors, **test harness** for loaders, synthetic datasets, and evidence repos.
* **Deliverable:** Versioned `tools/` folder with scripts and basic tests.

---

## Global Deliverables

* Reversing report with a clean, reproducible **unpack**.
* Functional **PE parser** + auxiliary utilities.
* **Userland loader** with **≥2 techniques** and a stable **hollowing** PoC (lab).
* **PBR + PAD** completed per block; versioned evidence (logs, screenshots, hash sets).

---

## Success Criteria

* Executable dump with no crashes, working **IAT**, and viable static analysis.
* **Stable loader** that runs benign payloads in the lab and a **functional manual map** for a controlled DLL.
* Two **reproducible** injection techniques with artifact comparison.
* Clear documentation reproducible by third parties using your repo/lab.

---

## Bridge to Phase 3 & Modules 8A/8B

* Close B8 with **controlled in-memory execution**.
* Insert **8A (Initial Access)** and **8B (Blue Track minimum)** before evasion/crypto (B9/9B).
* **Phase 3** goes deeper into internals (PEB/TEB, regions, TLS), **ROP/JOP**, and introduces kernel/driver topics—reusing your loaders as a foundation.

