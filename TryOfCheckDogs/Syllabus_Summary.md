PENSUM — Phase and Quarter Overview (TOCD)

    Base timeline: start 2025-08-14 · estimated end 2029-12-03 (base) / 2030-01-18 → 2030-02-03 (with additional modules)
    Cross-cutting methodology: PBR (reproducible labs) + PAD (analysis and documentation) · OPSEC/Legal enforced · Blue validation (8B) where applicable.

1) Phase summary (brief description)

Phase 1 — Systems and programming fundamentals
Linux/CLI, Bash, toolchain (Git/Make, debuggers, sanitizers), systems C (memory, pointers, I/O), x86_64/ABI and basic assembly, linking/loading (ELF, PLT/GOT), LD_PRELOAD. Outcome: low-level operational fluency and in-house utilities.

Phase 2 — Applied analysis and first execution paths (RCE)
Applied reversing (static/dynamic), initial anti-analysis, basic manual unpack; deep PE, in-memory loaders (benign shellcode/local, introductory manual mapping); userland injection (CRT+LL, APC, basic hollowing) and mitigations (DEP/ASLR/CFG). Outcome: reversing report, PE parser, loader with ≥2 techniques.

Phase 3 — Advanced RE and OS internals + userland exploitation
Process internals (PEB/TEB, regions, TLS), ROP/JOP with info-leak (Win/Linux), didactic heap exploitation (LFH vs glibc), kernel/driver fundamentals on Windows (IOCTL/IRP) and local elevation in VM. Outcome: 2 userland exploits, RW primitive via a vulnerable driver, and Capstone F3 (userland → SYSTEM in lab).

Phase 4 — Evasion, persistence, and C2 operations
8A Initial Access (maldocs, LNK/HTA/JS, AMSI, LOLBins/WMI) · 8B Blue Track (Sysmon/ETW, YARA/Sigma, KQL) · Userland evasion (anti-analysis, dynamic resolution, direct syscalls, APC/module-stomping) · 9B Crypto/packer v2 (AEAD, light mutation) · Multi-OS persistence (Win/Linux/macOS) · C2 with realistic traffic profile and covert lab operations. Outcome: validated operational chain and Capstone F4 (96 h in lab with blue evaluation).

Phase 5 — Kernel, firmware, and boot (final)
Linux kernel (LKMs, kprobes/ftrace), Windows kernel (callbacks, IOCTL/IRP), lab-only rootkit-style PoCs (reversible and detectable), UEFI/OVMF and a benign DXE, bootflow and Secure Boot on/off comparison. Outcome: Capstone F5 integrating kernel + firmware with technical defense and tested rollback.
2) Quarter overview (4 months per time block)

    Legend: F1–F5 = phase; Bx = block; CAP = Capstone; (8A/8B/9B/12A–C) = added modules

No.	Period (YYYY-MM)	Main content	Milestones & deliverables
C1	2025-08 → 2025-11	F1: B1 Linux/CLI/Bash · B2 Toolchain · start of B3 Systems C	Scripting & toolchain PBRs; C utility with Makefile
C2	2025-12 → 2026-03	F1: finish B3 · B4 x86_64/ABI/asm · B5 ELF/PLT/GOT/LD_PRELOAD	LD_PRELOAD hook, ELF parser, clean sanitizers
C3	2026-04 → 2026-07	F2: B6 Reversing/Unpack · B7 PE/Loaders · B8 Injection & mitigations	Reversing report, PE parser, loader with ≥2 techniques
C4	2026-08 → 2026-11	F3 (start until 09-14): B1 Userland internals · B2 Basic ROP exploit. TOCD pause 09-14 → Bug Bounty + Uni (from 09-21)	Educational userland exploit with ROP and PAD; BackLogs start
C5	2026-12 → 2027-03	TOCD paused: Bug Bounty + Uni · reinforcement BackLogs	4 mini-challenges/week, light evidence
C6	2027-04 → 2027-07	TOCD paused (until 07-21): Bug Bounty + Uni · BackLogs	Public cases and productivity metrics
C7	2027-08 → 2027-11	F3: B3 Windows Internals (MM/OBJ/ETW/APC) · start of B4 ROP/JOP with info-leak	Handle/region tools; APC demo; Win exploit in progress
C8	2027-12 → 2028-03	F3: finish B4 (Win/Linux) · B5 Heap (LFH vs glibc) · start of B6 Kernel/driver & elevation	Linux exploit with mprotect; heap PoCs; IOCTL client
C9	2028-04 → 2028-07	F3: finish B6 · CAP F3 (userland→SYSTEM) · F4 pre-flight · 8A/8B	Full F3 chain; blue baseline and 2 delivery chains
C10	2028-08 → 2028-11	F4: B1 Evasion I · B2 Evasion II · 9B Crypto/Packer v2	Loader with dynamic resolution and validated packer v2
C11	2028-12 → 2029-03	F4: B3 Persistence (Win/Linux/macOS) · B4 C2 and traffic profiling	Verified persistence; 72 h C2 profile
C12	2029-04 → 2029-07	F4: B5 Covert operations · CAP F4 (96 h)	Operational playbook and technical defense
C13	2029-08 → 2029-11	F5: Pre-flight · B1 Linux kernel (LKMs/kprobes) · start of B2 Windows kernel (IOCTL/IRP)	Stable LKM and metrics; Windows driver in progress
C14	2029-12 → 2030-03	F5: finish B2 · B3 benign rootkit PoCs · B4 UEFI/OVMF (DXE) · B5 Bootflow · CAP F5	Benign DXE, Secure Boot comparison, kernel+firmware capstone
3) Blocks by phase (short list)

F1: B1 Linux/CLI · B2 Toolchain/Debugging · B3 Systems C I · B4 x86_64/ABI/asm · B5 ELF/PLT/GOT/LD_PRELOAD · (Minimal OPSEC)

F2: B6 Reversing/Unpack · B7 PE/In-memory loaders · B8 Userland injection and mitigations

F3: B1 Userland internals · B2 Basic ROP exploit · B3 Windows Internals (MM/OBJ/ETW/APC) · B4 Userland exploit II (info-leak + ROP/JOP Win/Linux) · B5 Heap exploitation (LFH vs glibc) · B6 Kernel/driver & elevation · CAP F3

F4: 8A Initial Access · 8B Blue Track · B1 Evasion I · B2 Evasion II · 9B Crypto/Packer v2 · B3 Persistence (Win/Linux/macOS) · B4 C2 and traffic profile · B5 Covert operations · CAP F4 · (Extensions: 12A macOS, 12B Linux EDR/eBPF, 12C Android ARM64/Frida)

F5: Pre-flight · B1 Linux kernel (LKMs/kprobes) · B2 Windows kernel (IOCTL/IRP/callbacks) · B3 Benign rootkit PoCs (lab) · B4 UEFI/OVMF (DXE) · B5 Bootflow & Secure Boot · CAP F5
4) Macro deliverables per phase

    F1: C utilities, ELF parser, LD_PRELOAD hook, docs and tests.

    F2: reversing report with unpack, PE parser, loader with ≥2 techniques.

    F3: two userland exploits (Win/Linux), RW primitive, and Capstone F3.

    F4: delivery chains (8A), blue baseline (8B), evasive loader with crypto/packer v2, measured persistence and C2, Capstone F4.

    F5: benign LKM and Windows driver, reversible rootkit-style PoCs, benign DXE and Secure Boot comparison, Capstone F5.

5) Calendar notes

    TOCD pause: 2026-09-14 → 2027-08-02. During this period: Bug Bounty + University and reinforcement BackLogs (6–8 h/week).

    TOCD resumes without pauses: from 2027-08-03 until program completion.

6) Conventions and metrics

    Every block closes with PBR + PAD and reproducible evidence.

    Validation with Blue panel where applicable (8B from Phase 4 onward).

    KPIs: effective lab hours/week, PBR/PAD closed, detection rate vs attempts, stability of PoCs/implants.
