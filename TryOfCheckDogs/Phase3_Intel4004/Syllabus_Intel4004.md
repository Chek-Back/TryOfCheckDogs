PENSUM — (start) — Blocks and Deliverables

    Coverage: 2026-08 → 2026-09-14
    Planned dedication: 5 h/day (Mon–Sat)
    Methodology: PBR (reproducible labs) + PAD (analysis and documentation)
    Note: practice strictly in an isolated lab with OPSEC/Legal controls.

Phase 3 (start) — Vision

Enter userland internals and introductory userland exploitation with a focus on truly understanding how processes live, how memory is managed, and how loaders interact. This segment ends with an educational exploit (lab environment) using basic ROP plus an analysis of modern mitigations.

Stage outputs

    Logbook and map of internals (PEB/TEB, modules, heaps, regions) for a controlled process.

    Minimal utilities (scripts/tools) to enumerate modules and memory regions.

    Educational userland exploit with introductory ROP, reproducible and documented.

    Mitigations report (DEP/ASLR/CFG) observed and scope limitations.

F3-B1 — Process and memory internals (userland, Windows/ELF parallels)

Duration: 3 weeks
Goal: understand the anatomy of a process and thread: PEB/TEB, memory layout, modules, heaps, regions, and lifecycles; practice inspection with debuggers and utilities.

Prereqs: Phase 2 complete (B6–B8: applied reversing and loaders).
Tools: WinDbg/x64dbg, Process Hacker, VMMap/procmap equivalent, Ghidra, PE-bear, readelf/objdump for ELF parallels.

Content

    Key structures: PEB/TEB, process parameters, module list (Ldr), high-level TLS.

    Memory layout: regions (image, heap, stack, private), protections and permissions, reserve vs commit.

    Modules: load order, dependencies, and basic resolution (with PLT/GOT parallels on ELF).

    Heaps: creation and general use; allocation patterns to observe (without heap exploitation yet).

    Signals and exceptions: overview (SEH/VEH) to prepare F3-B2.

    Inspection methodology: breakpoints, structure queries, module/region maps, evidence logging.

PBR

    Process map: automatically generate (custom script) an inventory of modules, regions, and permissions for a controlled process; export to JSON/CSV.

    PEB/TEB walk: extract relevant fields (image path, arguments, module list) via APIs or controlled debugger reads.

    TLS callback demo: identify presence/order of callbacks in a lab DLL and evidence their execution at load.

PAD

    Report with layout diagrams, debugger screenshots, and a PE vs ELF loading/resolution comparison.

    Logbook with reproducible steps and versioned scripts.

Success criteria

    Inventory script working on 2 lab processes with consistent output.

    Evidence of PEB/TEB reads and a TLS callback executing in a controlled environment.

F3-B2 — Userland exploitation I: stack overflow and basic ROP (educational)

Duration: 2 weeks
Goal: build and document an educational exploit against a vulnerable lab app, using introductory ROP to bypass DEP/ASLR at a didactic level, with clear ethical scope and scenario limits.

Prereqs: F3-B1 complete.
Tools: Symbol-enabled compilers, debuggers, pattern generators, utilities to locate gadgets in self-built binaries.

Content

    Mitigation review: DEP/ASLR/CFG at a high level and their userland impact.

    Classic stack vulns in lab binaries and exploitation conditions.

    Basic ROP: gadget hunting in self-built binaries, simple chains for register/permission adjustments and control-flow redirection.

    Educational strategies: change page permissions in a controlled memory region before jumping to benign code, or call already-present functions with safe arguments.

    Minimal telemetry: record process events and behavior in the lab exploit.

PBR

    Educational exploit: controlled overflow with basic ROP achieving an observable, safe effect in lab (e.g., invoke an observable function or adjust permissions in a test region).

    Mitigation analysis: document how DEP/ASLR shaped the chain and which lab assumptions enabled the exercise.

    Hardening post-mortem: propose build or configuration changes that neutralize the lab exploit.

PAD

    Technical report with exploit narrative: threat model, assumptions, steps, evidence (screens/logs), and limitations.

    Legal/ethics checklist applicable to the scenario.

Success criteria

    Reproducible exploit, no system hangs, with sufficient logs and screenshots.

    Report that enables a third party to replicate in the same lab.

Express Module F3 — Bug bounty prep (pre-window)

Duration: 3–5 days (in parallel with F3-B2)
Goal: finalize the workflow for the bug bounty window starting 2026-09-21.

Content

    Reporting playbook: templates, severity, duplicates, communication.

    Daily recon and triage: checklists and boundaries (authorized programs only).

    Evidence pipeline: how to capture, obfuscate sensitive data, and version findings.

    Personal schedule: 4–5 h daily blocks, breaks, and metrics.

Deliverables

    Reporting template and evidence/ folder with standard structure.

    List of target programs within policy.

    Weekly schedule and productivity metrics.

Deliverables by 2026-09-14

    Scripts/tools: process inventory, basic PEB/TEB extraction, TLS demo utilities.

    Educational userland exploit with basic ROP and evidence.

    PADs complete (internals + exploit + hardening).

    Bug bounty playbook ready to use as of 2026-09-21.

Phase 3 (start) — Grading rubric

    A: PBR and PAD complete; stable, documented exploit; scripts working on more than one process; playbook ready.

    B: ≥80% of PBR/PAD; exploit with minor polishing needed; partial but useful scripts.

    C: ≥60% of PBR/PAD; weak reproducibility or insufficient documentation.

    Redo: <60% or practices without evidence/clear ethical scope.

PENSUM — (post–Bug Bounty continuation) — Blocks and Deliverables

    Coverage: from 2027-08-03 through the end of Phase 3
    Planned dedication: 5 h/day (Mon–Sat)
    Methodology: PBR (reproducible labs) + PAD (analysis and documentation)
    Prereqs: Phase 1 complete, Phase 2 complete (B6–B8), Phase 3 (start) complete (userland internals + basic ROP).
    Ethics/OPSEC: practice only in an isolated lab; vulnerable drivers and binaries must be didactic lab artifacts.

Vision

Complete advanced RE and OS internals and bring userland exploitation to a serious level (info-leak, stronger ROP/JOP, Windows/Linux heap). Prepare the ground for kernel and operations in Phase 4 with a full-chain Capstone: userland execution → controlled local elevation (BYOVD/vuln driver) → hardening and oral defense.

Phase outputs

    In-house utilities to inspect handles, memory regions, modules, and key events.

    2 userland exploits (1 Windows, 1 Linux) with didactic mitigation bypass.

    RW primitive PoC via a vulnerable lab driver and local elevation to NT AUTHORITY\SYSTEM.

    Full technical documentation, mitigations checklist, and Capstone defense.

F3-B3 — Advanced Windows Internals (MM, Object Manager, ETW, threads/APC)

Duration: 4 weeks
Goal: understand critical subsystems (Memory Manager, Object Manager, Scheduler/Threads) and capture minimal signals with ETW to instrument your own analyses.

Content

    Memory Manager: VADs, protections, reserve/commit; high-level working sets.

    Object Manager and handle tables: object types, duplication, inheritance, typical leaks.

    Threads and APCs: queues, early-bird, synchronization.

    ETW intro: relevant providers (processes, images, threads, loaders).

    Tools: WinDbg (symbols), Process Hacker, VMMap, ETW tooling.

PBR

    Handle map: enumerator with filtering by type and process; export CSV.

    Region map: region map with permissions and code/data heuristics.

    APC demo: PoC executing a benign function via APC in lab, with logs.

    ETW capture: minimal trace of process/image creation and brief analysis.

PAD

    Report with diagrams and evidence; limits and risks.

Success criteria

    Stable tools on 2 different lab processes; readable, reusable ETW trace.

F3-B4 — Userland exploitation II: info-leak and applied ROP/JOP (Win/Linux)

Duration: 4 weeks
Goal: build userland exploits with information leaks to defeat ASLR and chain ROP/JOP to handle DEP/CFG in didactic scenarios.

Content

    Common info-leaks: out-of-bounds reads, printed pointers, basic side channels.

    ROP/JOP: chain construction with gadgets, alignment pitfalls, bridge functions.

    Mitigations: DEP/ASLR/CFG/RELRO (Linux parallels) and real impact.

    Exploit hygiene: reliability, cleanup, and minimal telemetry.

PBR

    Windows userland exploit with info-leak + ROP that invokes an observable API without crashing.

    Linux userland exploit (lab binary) with leak and a chain that calls mprotect or equivalent.

    Harness for automated testing per exploit (pass/fail, timings, logs).

PAD

    Write-ups with chain diagrams, gadgets, offsets, and mitigations encountered.

Success criteria

    Reproducible exploits ≥80% in a controlled environment; harness produces automatic evidence.

F3-B5 — Heap exploitation (Windows LFH vs Linux glibc) in lab

Duration: 6 weeks
Goal: understand current heap models and practice UAF, tcache/fastbin poisoning (Linux), and vtable/func-ptr overwrite (Windows) in didactic versions.

Content

    Windows: LFH concepts, simple grooming, UAF patterns, function pointer/vtable overwrite in lab apps.

    Linux (glibc): educational-level fastbins/tcache, consolidation, controlled bin collisions.

    Limitations: scenarios with fixed builds/versions for teaching purposes, always in VM.

    Defenses: hardened builds, ASan/UBSan to validate fixes.

PBR

    UAF PoC (Win) that gains control over a function pointer in a lab app.

    tcache/fastbin PoC (Linux) with controlled pointer overwrite to an observable effect.

    Mitigations: rebuild with security options and show neutralization of the PoC.

PAD

    Documentation with primitives, heap graph, and grooming steps.

Success criteria

    Stable, documented PoCs; mitigation verifiable via rebuild/config.

F3-B6 — Kernel and driver fundamentals (Windows) + local elevation in lab

Duration: 5 weeks
Goal: set up a kernel debugging environment and understand the IOCTL/IRP cycle in drivers; obtain a controlled RW primitive via a vulnerable lab driver and perform an educational local elevation.

Content

    Driver model (high-level WDM/WDF), devices, IOCTL, IRP.

    Debug environment: WinDbg kernel (KD), symbols, connection.

    Vulnerable lab drivers: arbitrary read/write, integer truncation, etc.

    RW primitive → token stealing or benign credential patch in a lab VM.

    Safety: strict limits and snapshot restoration.

PBR

    IOCTL client for a lab driver (enumerate and invoke controls).

    RW primitive working and validated with tests.

    Local elevation to SYSTEM in lab VM (educational) with evidence and rollback.

PAD

    Report with driver architecture, IRP flow, exploit design, and rollback steps.

Success criteria

    Reproducible elevation in VM, no permanent effects after snapshot revert.

F3-CAP — Phase 3 Capstone: Full chain (userland → SYSTEM) in lab

Duration: 2 weeks
Goal: integrate skills: obtain userland execution with your own exploit and chain local elevation using the RW primitive from a vulnerable lab driver. Defend the solution in a technical presentation.

Activities

    Prepare userland PoC (from B4/B5) as the first link.

    Integrate IOCTL client and RW primitive (B6) to escalate to SYSTEM.

    Hardening and countermeasures: build mitigated binaries and show neutralization.

    Evidence: timing logs, harness, checksums, short demo video.

Deliverables

    capstone-f3/ repo with code, scripts, reproducible README.md, evidence, and technical defense (slides or doc).

Success criteria

    End-to-end chain reproducible in VM; convincing defense explaining technical choices, risks, and mitigations.

Phase 3 (complete) — Grading rubric

    A: All PBR/PAD and Capstone complete; stable exploits/PoCs; useful utilities; solid defense.

    B: ≥80% of PBR/PAD; functional Capstone with polishing needed; sufficient documentation.

    C: ≥60% of PBR/PAD; partial reproducibility or weak evidence.

    Redo: <60% or missing technical defense.

Bridge to Phase 4

With Phase 3 closed:

    Insert 8A/8B before deep Evasion/Obfuscation (B9) to measure and improve your chains.

    Then proceed to Phase 4: evasion, persistence, rootkits/bootkits, and covert C2, using Capstone experience as the operational base.
