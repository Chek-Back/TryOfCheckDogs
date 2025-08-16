
# SYLLABUS — Phase 3 (Start) — Blocks & Deliverables

> **Coverage:** 2026-08 → 2026-09-14
> **Time commitment:** 5 h/day (Mon–Sat)
> **Methodology:** **PBR** (reproducible labs) + **PAD** (analysis & documentation) · Lab-only under OPSEC/Legal

## Vision

Enter userland internals and introductory userland exploitation: understand how processes live (PEB/TEB, modules, heaps, regions), how memory is laid out, and how loaders interact. Close this segment with a didactic, **lab-only** exploit using basic ROP and a written analysis of modern mitigations.

## Stage outputs

* Logbook + internal maps (PEB/TEB, modules, heaps, regions) for a controlled process.
* Minimal utilities to enumerate modules and memory regions.
* Educational userland exploit with introductory ROP, **reproducible and documented**.
* Mitigations report (DEP/ASLR/CFG): scope, observations, and limits.

---

## F3-B1 — Process & Memory Internals (userland, Windows with ELF parallels)

**Duration:** 3 weeks · **Goal:** understand process/thread anatomy (PEB/TEB), memory layout, modules, heaps, regions; practice inspection with debuggers and utilities.

**Prereqs & tooling**
Phase 2 (B6–B8) completed. WinDbg/x64dbg, Process Hacker, VMMap/`procmap`, Ghidra, PE-bear; `readelf/objdump` for ELF parallels.

**Content**

* **Core structures:** PEB/TEB, process parameters, Ldr module lists, high-level TLS.
* **Memory layout:** region types (image/heap/stack/private), protections, reserve vs commit.
* **Modules:** load order & dependencies; **ELF parallels** (PLT/GOT) documented as contrast.
* **Heaps:** creation & typical allocation patterns *(no heap exploitation yet)*.
* **Signals/exceptions:** SEH/VEH overview to prepare B2.
* **Inspection method:** breakpoints, structure queries, module/region maps, evidence logging.

**PBR**

* **PBR-1.1:** **Process map** — script to inventory modules, regions, and permissions; export JSON/CSV.
* **PBR-1.2:** **PEB/TEB walk** — extract image path, args, module list (API or debugger reads).
* **PBR-1.3:** **TLS callback demo** — identify callbacks in a lab DLL and evidence their load-time execution.

**PAD**

* **PAD-1:** Layout diagrams, debugger screenshots, PE vs ELF loading/resolution comparison; reproducible steps with versioned scripts.

**Success criteria**

* Inventory script works on **2** lab processes with consistent output.
* Evidence of safe PEB/TEB reads and a TLS callback executing in a controlled environment.

---

## F3-B2 — Userland Exploitation I: Stack Overflow & Basic ROP (educational)

**Duration:** 2 weeks · **Goal:** build a **didactic** exploit against a vulnerable lab app using basic ROP. Work **within** DEP/ASLR constraints via **documented, controlled assumptions** (e.g., known addresses in non-PIE build or a minimal info-leak), and explain limits.

**Prereqs & tooling**
F3-B1 completed. Symbol-enabled builds, debuggers, cyclic/pattern tools, simple gadget finders on **self-built** binaries.

**Content**

* **Mitigations review:** DEP/ASLR/CFG (userland impact).
* **Classic lab vuln:** overflow conditions in symbolized targets.
* **Basic ROP:** gadget discovery in self-built binaries; chains to adjust registers/permissions or call existing APIs.
* **Educational strategy:** change page permissions in a test region (e.g., `VirtualProtect`) or call present functions with safe args.
* **Minimal telemetry:** process events & behavior logs in lab.

**PBR**

* **PBR-2.1:** **Educational exploit** — controlled overflow + basic ROP achieving an observable, safe effect.
* **PBR-2.2:** **Mitigation analysis** — how DEP/ASLR/CFG shaped the chain and which **lab assumptions** enabled it.
* **PBR-2.3:** **Hardening post-mortem** — builds/configs that neutralize the lab exploit.

**PAD**

* **PAD-2:** Technical report: threat model, assumptions, step-by-step, evidence (screens/logs), and legal/ethics checklist.

**Success criteria**

* Reproducible exploit, no system hangs, adequate logs & screenshots.
* Report enables a third party to replicate in the same lab.

---

## Express Module F3 — Bug-Bounty Prep (pre-window)

**Duration:** 3–5 days (in parallel with F3-B2) · **Goal:** finalize workflow for the 2026-09-21 window.

**Content & deliverables**

* **Playbook:** reporting templates, severity, duplicate handling, comms.
* **Scope:** list of programs (authorized only) + boundaries checklist.
* **Evidence pipeline:** capture, sensitive data obfuscation, versioning.
* **Schedule & metrics:** 4–5 h daily blocks, breaks, personal KPIs.
* **Deliverables:** reporting templates, `evidence/` skeleton, target list, weekly schedule & metrics.

---

## Deliverables by **2026-09-14**

* Scripts/tools: process inventory, basic PEB/TEB extraction, TLS demo.
* Educational userland exploit with basic ROP + evidence.
* **PAD-1** and **PAD-2** complete (internals + exploit + hardening).
* Bug-bounty playbook ready for **2026-09-21**.

## Phase 3 (Start) — Grading rubric

* **A:** PBR & PAD complete; stable, documented exploit; scripts work on >1 process; playbook ready.
* **B:** ≥80% PBR/PAD; minor polishing; scripts partially complete but useful.
* **C:** ≥60% PBR/PAD; weak reproducibility or documentation.
* **Redo:** <60% or practices without evidence/clear ethical scope.

---

# PENSUM — Phase 3 (Post-Bug-Bounty Continuation) — Blocks & Deliverables

> **Coverage:** from 2027-08-03 through Phase 3 end
> **Time commitment:** 5 h/day (Mon–Sat) · **Methodology:** PBR + PAD
> **Prereqs:** Phase 1 complete; Phase 2 (B6–B8) complete; **Phase 3 (Start)** complete (internals + basic ROP).
> **Ethics:** lab-only; vulnerable drivers/binaries are didactic artifacts.

## Vision

Complete advanced RE/OS internals and elevate userland exploitation (info-leak + ROP/JOP, Win/Linux heap). Prepare kernel work and operations for Phase 4 with a full-chain Capstone: userland execution → controlled local elevation (vulnerable lab driver) → hardening + technical defense.

## Phase outputs

* Utilities to inspect handles, memory regions, modules, and key events.
* **Two** userland exploits (Win & Linux) with didactic mitigation bypass.
* RW primitive via a vulnerable **lab** driver and local elevation to `NT AUTHORITY\\SYSTEM`.
* Full documentation and Capstone defense.

---

## F3-B3 — Advanced Windows Internals (MM, Object Manager, ETW, Threads/APC)

**Duration:** 4 weeks · **Goal:** understand MM (VADs), Object Manager/handles, scheduler/threads/APC, and capture minimal ETW signals.

**Content**

* **Memory Manager:** VADs, protections, reserve/commit; working-set view (high level).
* **Object Manager & handles:** object types, duplication, inheritance, common leaks.
* **Threads & APCs:** queues (incl. early-bird), synchronization.
* **ETW intro:** providers for process/image/thread/loader events.
* **Tooling:** WinDbg (symbols), Process Hacker, VMMap, ETW tools.

**PBR**

* **PBR-3.1:** **Handle-map** enumerator with type/process filters → CSV.
* **PBR-3.2:** **Region-map** with permissions and code/data heuristics.
* **PBR-3.3:** **APC-demo** (benign function) with logs.
* **PBR-3.4:** **ETW-capture** (minimal) and short analysis.

**PAD**

* **PAD-3:** Report with diagrams, evidence, limits & risks.

**Success criteria**

* Stable tools on **2** lab processes; readable, reusable ETW trace.

---

## F3-B4 — Userland Exploitation II: Info-Leak & Applied ROP/JOP (Win/Linux)

**Duration:** 4 weeks · **Goal:** build userland exploits with info-leaks to defeat ASLR and chain ROP/JOP to handle DEP/CFG in didactic scenarios.

**Content**

* Info-leaks: OOB reads, printed pointers, simple side-channels.
* ROP/JOP: chain construction, alignment pitfalls, bridge functions.
* Mitigations: DEP/ASLR/CFG and Linux parallels (RELRO/PIE).
* Exploit hygiene: reliability, cleanup, minimal telemetry.

**PBR**

* **PBR-4.1:** **Windows** exploit (leak + ROP) calling an observable API, no crash.
* **PBR-4.2:** **Linux** exploit (leak + chain) invoking `mprotect`-like behavior.
* **PBR-4.3:** **Harness** for automated pass/fail, timings, logs.

**PAD**

* **PAD-4:** Write-ups with chain diagrams, gadgets, offsets, and encountered mitigations.

**Success criteria**

* ≥80% reproducibility in VM; harness emits automatic evidence.

---

## F3-B5 — Heap Exploitation (Windows LFH vs Linux glibc) — Lab

**Duration:** 6 weeks · **Goal:** practice UAF (Win) and tcache/fastbin poisoning (Linux) with didactic builds; show mitigations.

**Content**

* **Windows:** LFH, grooming, UAF → function-ptr/vtable overwrite (observable).
* **Linux (glibc):** fastbins/tcache (educational), consolidation, controlled collisions.
* **Defenses:** hardened rebuilds; validate fixes with ASan/UBSan.

**PBR**

* **PBR-5.1:** **UAF (Win)** PoC controlling a function pointer in lab app.
* **PBR-5.2:** **tcache/fastbin (Linux)** PoC to observable effect.
* **PBR-5.3:** **Mitigations** — rebuild/config that neutralizes PoCs.

**PAD**

* **PAD-5:** Primitives, heap graphs, grooming steps.

**Success criteria**

* Stable, documented PoCs; mitigation verifiable via rebuild/config.

---

## F3-B6 — Kernel/Driver Fundamentals (Windows) + Local Elevation — Lab

**Duration:** 5 weeks · **Goal:** set up KD, understand IOCTL/IRP; obtain a controlled RW primitive via a vulnerable **lab** driver and perform a local elevation (educational).

**Content**

* Drivers (WDM/WDF high level), devices, IOCTL, IRP.
* KD setup: symbols & reliable connection.
* Vulnerable drivers (lab): arbitrary RW, truncations, etc.
* RW → token stealing or benign credential tweak *(VM only)*; strict snapshots.

**PBR**

* **PBR-6.1:** **IOCTL client** for the lab driver.
* **PBR-6.2:** **RW primitive** validated with tests.
* **PBR-6.3:** **Elevation to SYSTEM** in VM + rollback evidence.

**PAD**

* **PAD-6:** Driver architecture, IRP flow, exploit design, rollback steps.

**Success criteria**

* Reproducible elevation in VM; no lasting effects after snapshot revert.

---

## F3-CAP — Phase 3 Capstone: Full Chain (userland → SYSTEM) — Lab

**Duration:** 2 weeks · **Goal:** integrate userland exploit (B4/B5) with IOCTL client + RW primitive (B6) for end-to-end elevation; defend the design.

**Activities & deliverables**

* Prepare userland PoC; integrate IOCTL client & RW primitive.
* Hardening & countermeasures: mitigated builds that neutralize the chain.
* Evidence: timing logs, harness, checksums, short demo.
* **Deliverable:** `capstone-f3/` with code, scripts, reproducible README, evidence, and technical defense.

**Success criteria**

* End-to-end chain reproducible in VM; convincing defense of choices, risks, and mitigations.

---

## Phase 3 (Complete) — Grading rubric

* **A:** All PBR/PAD + Capstone complete; stable exploits/PoCs; useful utilities; solid defense.
* **B:** ≥80% PBR/PAD; functional Capstone needing polish; sufficient docs.
* **C:** ≥60% PBR/PAD; partial reproducibility or weak evidence.
* **Redo:** <60% or missing technical defense.

---

## Bridge to Phase 4

With Phase 3 closed: insert **8A/8B** before deep Evasion/Obfuscation (B9) to **measure and improve** chains; then proceed to Phase 4 (evasion, persistence, covert C2), using the Capstone as your operational base.
