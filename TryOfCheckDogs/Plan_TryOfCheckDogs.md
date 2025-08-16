PLAN — Try Of Check Dogs (TOCD)

    Author: Denis Pérez
    Last updated: 2025-08-10

1) Vision and goal

I aim to reach professional competence in Reverse Engineering and Malware Development. The expected outcome is a portfolio with verifiable projects: exploits and post-exploitation, implants with C2 and persistence, evasion techniques validated through telemetry, and documentation aligned with professional standards.
2) Route principles

    Hands-on first: every block includes reproducible labs (PBR) and technical documentation (PAD).

    Objective measurement: defensive baseline (Sysmon/ETW, YARA/Sigma, KQL) to prove evasion with data.

    Ethics and isolation: all work is done in an isolated lab with OPSEC/Legal controls.

    Realistic progression: from fundamentals to kernel/UEFI without artificial jumps.

3) Master schedule (real dates)

    TOCD Segment 1: 2025-08-14 → 2026-09-14
    Intensive self-study (5 h/day, Mon–Sat). PBR/PAD deliverables per block.

    Break: 2026-09-14 → 2026-09-20
    Six-day pause. Small BackLogs if needed to keep pace.

    Bug Bounty + University: 2026-09-21 → 2027-07-21
    First 9 months of university in parallel with bug hunting (4–5 h/day); TOCD in short BackLogs (6–8 h/week).

    TOCD resumes without pauses: from 2027-08-03 until all phases are complete.

    Estimated end of TOCD:

        Base (53 months): 2029-12-03

        With added modules (8A, 8B, 9B, 12A–C, OPSEC/Legal): 2030-01-18 → 2030-02-03

    The JHU master’s will start once I obtain a job that makes it sustainable, without interrupting TOCD.

4) Coordinated tracks

    TOCD (self-directed): custom curriculum focused on systems, RE, exploit dev, and evasion.

    University (TEP PUCMM): formal cybersecurity foundation. Start: 2026-09. Estimated duration: ~2 years (through 2028).

    Master’s (JHU): to be pursued after securing RE/maldev-related employment.

5) Phase structure (summary)

    Phase 1 — Systems and programming fundamentals
    Linux/CLI, C/C++, assembly, architecture. Goal: low-level fluency.

    Phase 2 — Applied analysis and RCE
    Applied reversing, payloads, and client-side surface.

    Phase 3 — Advanced RE and OS internals
    Userland and kernel internals, advanced exploit dev, integrative projects.

    Phase 4 — Evasion, persistence, and operations
    Anti-debug/anti-VM, unhooking, direct syscalls, hollowing, module stomping, C2, and covert operations.

        Block 8A (new): Initial Access and covert delivery (maldocs, LNK/HTA/JS, AMSI, LOLBins, WMI).

        Block 8B (new): Minimum Blue Track (Sysmon/ETW, YARA/Sigma, KQL) for baseline and validation.

        Block 9B (new): Implant crypto and Packer v2 (proper AEAD, key rotation, light mutation).

    Phase 5 — Advanced persistence and firmware
    Rootkits/bootkits, UEFI, and a final project with technical defense.

        Extensions 12A–C (new): macOS internals + EndpointSecurity; Linux EDR/eBPF; Android ARM64 + basic Frida.

    Express Module (new): OPSEC & Legal for secure builds, compartmentalization, and usage limits.

6) Time commitments

    Before university: 5 h/day, Mon–Sat, on TOCD.

    Bug Bounty + university (9 months): 4–5 h/day on bugs, TOCD via BackLogs of 6–8 h/week.

    From 2027-08-03: TOCD continues without pauses until completion (full pace).

7) Goals and KPIs

Technical goals

    Close each block’s PBR/PAD with reproducible evidence (screenshots, hashset, IOC list, report).

    Capstone with full chain: initial access → execution → persistence/rootkit → C2 → blue validation.

Progress KPIs

    Effective lab hours per week.

    Detection rate vs attempts in 8B (signal/noise).

    PBR/PAD closed per block and per phase.

    Public bug bounty cases during 2026–2027 (target: 1–2/month).

Financial goal

    Operating target: USD 18,000–36,000 during the bug bounty window (2026-09-21 → 2027-07-21) to support living expenses and studies.

    Cushion of 3–4 months’ expenses; logging and post-mortems for each case.

8) BackLogs during university

During the 9 months of bug bounty + university, I’ll maintain TOCD with weekly BackLogs of 6–8 h:

    Quick reviews of completed labs to avoid decay.

    Mini-exercises for 8A/8B (rule tuning, new delivery chains).

    Toolchain and documentation maintenance.

9) Risk management

    Academic overload: prioritize critical deliverables and limit TOCD to BackLogs.

    Income volatility: savings plan and steady bug bounty reporting pipeline.

    Scope drift: no new modules until 8A/8B/9B/12A–C are closed.

    Ethics/Legal: lab-only testing and explicit consent in controlled cases.

10) OPSEC and legal

    Campaign-level project compartmentalization.

    Metadata minimization (PDB/RSDS, timestamps, FileVersionInfo).

    Signing and artifact control where applicable.

    Usage policies and consent documentation.

11) Versioning and control

    Separate repos per phase/block.

    Issues and Milestones aligned to KPIs.

    Changelog/lab log with dated entries (ISO day and local time).

12) High-level calendar (summary)

    2025-08-14 → 2026-09-14: Continuous TOCD (5 h/day).

    2026-09-14 → 2026-09-20: Break (6 days).

    2026-09-21 → 2027-07-21: Bug Bounty + University (TOCD via BackLogs).

    From 2027-08-03: TOCD without pauses until completion (ETA 2029-12-03 / 2030-01-18 → 2030-02-03).

13) Expected outcome

By the end, I’ll have operational skills in RE/maldev, a portfolio of verifiable projects, evidence of measured evasion via telemetry, and professional-grade documentation, ready for a specialized role and the JHU master’s.
