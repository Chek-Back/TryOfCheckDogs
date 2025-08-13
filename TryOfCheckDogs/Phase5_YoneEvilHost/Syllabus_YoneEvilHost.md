PENSUM — Kernel, Firmware, UEFI/Boot — Blocks and Deliverables (v1.0)

    Start: after completing Phase 4 and its Capstone
    Planned dedication: 5 h/day (Mon–Sat)
    Methodology: PBR (reproducible labs) + PAD (analysis and documentation)
    Ethical scope: lab-only (VMs and virtual firmware with OVMF). No real hardware without vendor guides and verified backups.
    Note: All exercises use benign payloads for training purposes.

Pre-flight F5 (1 week)

Goal: prepare a safe environment for kernel and firmware work.

Checklist

    Base VM snapshots (Windows/Linux) + clean OVMF images.

    WinDbg KD and symbols for Windows; dmesg, ftrace, kprobes for Linux; QEMU + OVMF/edk2 for UEFI.

    Firmware tooling: UEFITool/UEFIExtract, CHIPSEC (analysis mode), sbctl/mokutil (Linux), fwupd (read-only).

    Tested rollback and restoration policies.

PBR

    Verify kernel debugging (Win/Linux) with a controlled hello-world.

    Bring up QEMU+OVMF and extract volumes with UEFITool.

    Risk document and recovery plan.

F5-B1 — Advanced Linux Kernel: LKMs, kprobes/ftrace, and telemetry

Duration: 4 weeks
Goal: understand the module lifecycle and practice non-intrusive instrumentation with kprobes/kretprobes/ftrace; expose metrics via /proc or /sys.

Content

    Minimal Kbuild/Kconfig, symbols, versioning, module signing.

    Core structures (task_struct, files_struct) at a high level; safe reads.

    kprobes/kretprobes and ftrace for didactic instrumentation.

    Metric export (seq_file in /proc, sysfs).

    Safety: avoid destructive hooks; test against lab kernels.

PBR

    LKM exposing process info (PID, cmdline) via /proc/demo_lkm.

    Instrument a selected syscall with kprobes and controlled logging.

    Performance and stability report using perf/traces.

PAD

    Module design, risks, test results, and build guide.

Success criteria

    LKM loads/unloads cleanly, no oops; reproducible metrics.

F5-B2 — Windows Kernel fundamentals: WDM/WDF, IOCTL/IRP, and callbacks

Duration: 5 weeks
Goal: build a benign driver that logs process/image events and exposes a simple IOCTL; debug in KD.

Content

    Driver model (WDM/WDF at a high level) and the IRP lifecycle.

    Symbolic devices and queues; access security in lab.

    Callbacks: PsSetCreateProcessNotifyRoutineEx, PsSetLoadImageNotifyRoutine (didactic logging).

    IOCTL: minimal user-to-kernel interface; buffer validation.

    Telemetry: debugger messages and basic event tracing.

PBR

    Driver that logs process/image creations and emits to the debugger.

    Userland client consuming an IOCTL and receiving a counter/state.

    Deployment/rollback script with VM tests.

PAD

    Architecture, IRP flow, IOCTL security, and test results.

Success criteria

    Stable driver, no bugcheck; IOCTL functional and verified.

F5-B3 — Lab rootkit techniques (safe, multi-OS)

Duration: 5 weeks
Goal: study historical and modern patterns for hiding/monitoring in userland/kernel, implementing benign and easily reversible PoCs in VM.

Content

    Linux: didactic syscall interception with kprobes/ftrace; demonstrate event filtering without altering functional behavior.

    Windows: process/image/registry callbacks, minimal filters (minifilter concept) for controlled logging.

    Modern considerations (PatchGuard, control flow) and pedagogical limits.

    Anti-analysis and detection: how to identify your own PoCs from the blue side.

PBR

    Linux PoC that selectively logs open/exec via kprobes with on/off toggles through sysfs.

    Windows PoC that applies a non-disruptive registry/log filter with IOCTL toggles.

    Blue validation: YARA/Sigma rules and KQL queries to detect your PoCs.

PAD

    Documentation, risks, and full rollback guide.

Success criteria

    Reversible, measurable PoCs detectable by your own rules.

F5-B4 — UEFI internals and firmware analysis (OVMF/QEMU)

Duration: 4 weeks
Goal: understand UEFI architecture (PEI/DXE/RT), analyze volumes and modules in OVMF, and instrument a benign DXE that logs an event.

Content

    UEFI architecture: phases, services, protocols; high-level Secure Boot.

    Tools: UEFITool/UEFIExtract, chipsec_util (analysis mode), edk2 build.

    Boot flow in QEMU with OVMF; lab NVRAM variables.

    Safety: limits, NVRAM backups, guaranteed rollback.

PBR

    Extract and inventory DXE modules in OVMF and map dependencies.

    Build a benign DXE driver that logs a message during boot in QEMU.

    Secure Boot report: VM state, keys, and observed execution paths.

PAD

    Write-up with steps, screenshots, and risks.

Success criteria

    DXE loads and logs at boot; VM remains stable; rollback verified.

F5-B5 — Bootflow and bootkit practices in VM (educational)

Duration: 5 weeks
Goal: explore the full bootflow in a virtual environment and build an educational module that modifies a benign boot parameter (e.g., 
log telemetry or display a banner), demonstrating Secure Boot mitigations.

Content

    Bootflow: firmware to OS hand-off; study of hook points (historical view).

    edk2: project structure, build, and signing for lab environments.

    Secure Boot and trust chains; effects of enabling/disabling policies.

    Blue evaluation: detecting changes and verifying integrity.

PBR

    Build a harmless boot module that shows a banner/logs in DXE.

    Measure impact with Secure Boot on/off and document differences.

    Provisioning and restoration script for NVRAM/OVMF.

PAD

    Risk report, mitigations, and recovery procedure.

Success criteria

    Module loads only in the lab context; Secure Boot blocks execution when it should; recovery guaranteed.

F5-CAP — Final Capstone: Kernel/firmware chain with technical defense

Duration: 3 weeks
Goal: integrate skills in a VM scenario: kernel telemetry (Linux or Windows) + benign boot component in OVMF; blue evaluation and technical defense.

Activities

    Choose Route A (Linux LKM + benign DXE) or Route B (Windows driver + benign DXE).

    Run stability, performance, and detectability tests using your blue dashboard.

    Prepare documentation, build and rollback scripts, and the technical defense.

Deliverables

    capstone-f5/ repo with code, scripts, reproducible README, evidence, and presentation.

    Applied and signed OPSEC/Legal checklist.

Success criteria

    Reproducible VM demonstration, no bricking; clear metrics and findings; convincing defense.

Phase 5 — Grading rubric

    A: PBR/PAD complete; stable, reversible PoCs; functional benign DXE; strong Capstone with blue validation and flawless rollback.

    B: ≥80% PBR/PAD; one unstable component but documented; functional Capstone.

    C: ≥60% PBR/PAD; partial reproducibility or weak blue validation.

    Redo: <60% or operational risk (no proven rollback).

Dependencies and suggested order

    Pre-flight F5

    F5-B1 (Linux)

    F5-B2 (Windows)

    F5-B3 (benign rootkit PoCs)

    F5-B4 (UEFI)

    F5-B5 (Bootflow/edk2 + Secure Boot)

    F5-CAP

Outcome

Phase 5 closes TOCD with skills in kernel observability and development (Linux/Windows) and operational understanding of UEFI/bootflow in virtual labs, 
plus a Capstone that integrates kernel + firmware with defensive validation, professional documentation, and safe recovery.
