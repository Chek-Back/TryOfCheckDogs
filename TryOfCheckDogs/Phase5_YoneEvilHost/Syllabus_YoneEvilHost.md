
# SYLLABUS — Kernel, Firmware, UEFI/Boot — Blocks & Deliverables (v1.1)

> **Start:** after completing Phase 4 + Capstone
> **Time commitment:** 5 h/day (Mon–Sat)
> **Methodology:** **PBR** (reproducible labs) + **PAD** (analysis & documentation)
> **Ethical scope:** **lab-only** (VMs and virtual firmware with OVMF). No real hardware unless vendor guides and **verified backups** are in place.
> **Note:** All exercises use **benign** payloads for training purposes.

---

## Pre-flight F5 (1 week)

**Goal:** prepare a safe, instrumented environment for kernel and firmware work.

**Checklist**

* Base VM snapshots (Windows/Linux) + clean OVMF images.
* Debug stacks: WinDbg KD + symbols; Linux `dmesg`, `ftrace`, `kprobes`; QEMU + OVMF/edk2.
* Firmware tools: UEFITool/UEFIExtract, CHIPSEC (**analysis mode**), sbctl/mokutil, fwupd (**read-only**).
* Tested rollback & restoration policies (NVRAM/OVMF + VM).

**PBR (pre-flight)**

* **PBR-BR.1:** Verify kernel debugging (Win/Linux) with a controlled “hello-world”.
* **PBR-BR.2:** Bring up QEMU+OVMF and extract volumes with UEFITool.
* **PBR-BR.3:** Risk register and recovery plan validated from a clean snapshot.

**PAD**

* **PAD-BR:** Pre-flight report (risks, mitigations, rollback).

**Success criteria**

* KD and kprobe/ftrace sessions reproducible; OVMF boot + volume extraction OK; rollback proven.

---

## F5-B1 — Linux Kernel (LKMs, kprobes/ftrace, telemetry)

**Duration:** 4 weeks · **Goal:** understand the LKM lifecycle and practice non-intrusive instrumentation with kprobes/kretprobes/ftrace; expose metrics via `/proc` or `sysfs`.

**Content**

* Minimal Kbuild/Kconfig; symbols/versioning; module signing (lab).
* Core structs at high level (`task_struct`, `files_struct`): *safe reads only*.
* kprobes/kretprobes, ftrace (didactic instrumentation).
* Metric export (`seq_file` in `/proc`, `sysfs`).
* Safety: avoid destructive hooks; pin to lab kernels.

**PBR**

* **PBR-B1.1:** LKM exposing process info (PID/cmdline) via `/proc/demo_lkm`.
* **PBR-B1.2:** Instrument one syscall with kprobes + controlled logging.
* **PBR-B1.3:** Perf/stability snapshot (perf + trace samples).

**PAD**

* **PAD-B1:** Module design, risks, test results, build guide.

**Success criteria**

* LKM loads/unloads cleanly (no oops); metrics reproducible across two lab kernels.

---

## F5-B2 — Windows Kernel Fundamentals (WDM/WDF, IOCTL/IRP, callbacks)

**Duration:** 5 weeks · **Goal:** build a benign driver that logs process/image events and exposes a simple IOCTL; debug in KD.

**Content**

* Driver model (WDM/WDF high level); IRP lifecycle.
* Symbolic devices/queues; lab security for device access.
* Callbacks: `PsSetCreateProcessNotifyRoutineEx`, `PsSetLoadImageNotifyRoutine` (didactic logging).
* IOCTL: minimal user→kernel interface; strict buffer validation.
* Telemetry: DbgPrint/trace basics.

**PBR**

* **PBR-B2.1:** Driver logging process/image creations to debugger.
* **PBR-B2.2:** Userland client invoking an IOCTL (counter/state).
* **PBR-B2.3:** Deploy/rollback script validated in VM.

**PAD**

* **PAD-B2:** Architecture, IRP flow, IOCTL security, tests.

**Success criteria**

* Stable driver (no bugcheck); IOCTL verified; clean uninstall/rollback.

---

## F5-B3 — “Rootkit” Techniques in Lab (safe & detectable)

**Duration:** 5 weeks · **Goal:** study historical/modern **hiding/monitoring** patterns and implement **benign, reversible, and detectable** PoCs in VM; emphasize **blue-side** detection.

**Content**

* **Linux:** didactic syscall/event filtering via kprobes/ftrace (no patching tables).
* **Windows:** process/image/registry callbacks; minifilter **concept** (logging) — no stealth file hiding.
* Modern constraints (PatchGuard, control-flow) and **pedagogical limits**.
* Blue validation mindset: detect your own PoCs.

**PBR**

* **PBR-B3.1:** Linux PoC: selective log of `open/exec` via kprobes; on/off through `sysfs`.
* **PBR-B3.2:** Windows PoC: non-disruptive registry/log filter toggled via IOCTL.
* **PBR-B3.3:** Blue validation: YARA/Sigma + KQL to detect your PoCs.

**PAD**

* **PAD-B3:** Full doc, risks, and **rollback guide**.

**Success criteria**

* PoCs are **reversible** and **measurably detectable** by your rules; no functional disruption.

---

## F5-B4 — UEFI Internals & Firmware Analysis (OVMF/QEMU)

**Duration:** 4 weeks · **Goal:** understand UEFI architecture (PEI/DXE/RT), analyze volumes/modules in OVMF, and instrument a benign DXE that logs an event.

**Content**

* UEFI phases, services, protocols; Secure Boot (high level).
* Tools: UEFITool/UEFIExtract, CHIPSEC (analysis), edk2 build.
* QEMU + OVMF boot; lab NVRAM variables; backups and restore.

**PBR**

* **PBR-B4.1:** Extract/inventory DXE modules in OVMF + dependency map.
* **PBR-B4.2:** Build a benign DXE that logs at boot in QEMU.
* **PBR-B4.3:** Secure Boot state report (keys, observed paths).

**PAD**

* **PAD-B4:** Step-by-step write-up with screenshots, risks, recovery.

**Success criteria**

* DXE logs at boot; VM stable; NVRAM/OVMF rollback verified.

---

## F5-B5 — Bootflow & Bootkit Practices (educational, VM-only)

**Duration:** 5 weeks · **Goal:** explore bootflow in VM and build a **harmless** module that modifies a benign boot parameter (banner/log), demonstrating Secure Boot mitigations and **blue** verification.

**Content**

* Bootflow: firmware→OS hand-off; historical hook points (conceptual).
* edk2 project structure; **lab** signing/notarization.
* Secure Boot chain of trust; effects of on/off.
* Blue evaluation: verify integrity and detect changes.

**PBR**

* **PBR-B5.1:** Harmless DXE/boot module that shows a banner/logs in DXE.
* **PBR-B5.2:** Measure impact with Secure Boot on/off; document differences.
* **PBR-B5.3:** Provisioning & restoration script for NVRAM/OVMF.

**PAD**

* **PAD-B5:** Risk report, mitigations, recovery procedure.

**Success criteria**

* Module loads **only** in lab; Secure Boot blocks as expected; guaranteed recovery.

---

## F5-CAP — Final Capstone (kernel + firmware + blue defense)

**Duration:** 3 weeks · **Goal:** integrate skills in VM: kernel telemetry (Linux **or** Windows) + benign DXE; add blue evaluation and a technical defense.

**Activities**

* Choose Route A (Linux LKM + benign DXE) or Route B (Windows driver + benign DXE).
* Run stability/perf/detectability tests with your blue dashboard.
* Prepare docs, build & rollback scripts, and the defense.

**Deliverables**

* `capstone-f5/` repo: code, scripts, reproducible README, evidence, and presentation.
* Applied & signed OPSEC/Legal checklist.

**Success criteria**

* Reproducible demo (no bricking), clear metrics/findings, convincing defense.

---

## Phase 5 — Grading rubric

* **A:** All PBR/PAD complete; stable, reversible PoCs; functional benign DXE; strong Capstone with blue validation and flawless rollback.
* **B:** ≥80% PBR/PAD; one unstable area but documented; functional Capstone.
* **C:** ≥60% PBR/PAD; partial reproducibility or weak blue validation.
* **Redo:** <60% or operational risk (no proven rollback).

---

## Dependencies & suggested order

Pre-flight → **B1 (Linux)** → **B2 (Windows)** → **B3 (Lab “rootkit” patterns, detectable)** → **B4 (UEFI)** → **B5 (Bootflow)** → **F5-CAP**.
