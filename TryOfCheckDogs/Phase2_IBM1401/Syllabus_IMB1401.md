PENSUM — Applied Analysis and RCE — Blocks and Deliverables

    Estimated coverage: ~03/2026 → ~07/2026 (adjustable based on Phase 1 progress)
    Planned dedication: 5 h/day (Mon–Sat)
    Methodology: PBR (reproducible labs) + PAD (analysis and documentation)

Vision

Consolidate applied reversing and the first userland execution paths. Here I learn to understand real binaries (static/dynamic), unpack simple layers, and build loaders that stage payloads in memory using classic injection techniques while accounting for modern mitigations.

Phase 2 outputs

    Reversing report for a real binary (with light obfuscation) and a reproducible unpack.

    PE parser and custom analysis utilities.

    Userland loader with at least two execution techniques.

    Intro lab process hollowing PoC.

    Documentation discipline and evidence packaged for bug bounty.

Relation to future modules

    After Block 8, insert 8A (Initial Access) and 8B (Minimum Blue Track) before moving into deep Evasion/Obfuscation (Block 9 and 9B).

Block 6 — Applied Reversing I: tooling, methodology, and basic unpacking

Duration: 6 weeks
Goal: master a static/dynamic pipeline with Ghidra/IDA and x64dbg/WinDbg, identify trivial anti-analysis, and perform manual single-layer unpacking (UPX or similar) with minimal IAT reconstruction.

Content

    Tools: Ghidra/IDA (free), rizin/Cutter, x64dbg/WinDbg.

    Static: strings/signatures, control-flow graph (CFG), calling conventions, struct recovery, common patterns.

    Dynamic: breakpoints, memory map, dump & patch, basic relocations; common debugger pitfalls.

    Simple anti-analysis: IsDebuggerPresent, PEB BeingDebugged, time checks; basic bypasses.

    Packers 101: UPX and variants; finding the OEP; IAT reconstruction via tools or custom scripts.

    Support scripting: Python for small utilities (parsers, decoders) and dump automation.

PBR

    Reversing report for a small binary with obfuscated strings: key function map, flow, and decision points.

    Manual unpack of a packed sample (UPX or similar): clean dump and reconstructed IAT; hash comparison and debugger load.

    String/config decoding script (simple XOR/RC4) with unit tests.

PAD

    Step-by-step methodology, screenshots, checksums before/after, issues and mitigations.

Success criteria

    Executable dump without crashes, functional IAT, and feasible static analysis on the result.

    Clear report reproducible by third parties using your repo/lab.

Block 7 — Deep PE, Windows API, and in-memory loaders

Duration: 5 weeks
Goal: understand PE at a practical level (headers, sections, imports/exports, relocations, TLS) and build loaders that execute payloads in memory, starting with benign shellcode and progressing to basic manual mapping.

Content

    PE: DOS/NT headers, sections vs segments, imports/exports, relocations, TLS callbacks; PE vs ELF differences.

    Windows processes/threads/memory: VirtualAlloc{Ex}, WriteProcessMemory, Create{Remote}Thread, VirtualProtect and variants.

    Minimal loader: allocation and copy of payload, permission changes, controlled jump.

    Basic manual mapping: load a DLL in memory without LoadLibrary (selected import resolution, essential relocations, no advanced TLS).

    Safety and common bugs: permissions, offsets, alignment, silent crashes.

    Inspection tools: Process Hacker, PE-bear, PE-sieve for lab validation.

PBR

    PE parser: print key headers, sections, and imports; simple integrity checks.

    Benign shellcode loader in a local process (not remote) with error handling and cleanup.

    Intro manual map of a minimal DLL and execution of an exported function.

PAD

    Loader design, memory diagrams, risks, and tests with robust error handling.

Success criteria

    Stable loader that runs benign payloads without external AV in the lab.

    Functional manual map for a controlled DLL with execution evidence.

Block 8 — Userland execution paths and modern mitigations

Duration: 5 weeks
Goal: implement 2–3 classic userland injection/execution techniques and understand the impact of DEP/ASLR/CFG and handle-management policies. Prepare the ground for Evasion/Obfuscation and the 8A Initial Access module.

Content

    Classic injection: CreateRemoteThread + LoadLibrary.

    APC queueing (including early-bird) and synchronization considerations.

    Intro process hollowing and differences vs module stomping.

    PPID spoofing and relevant CreateProcess options for staging in lab.

    Light obfuscation: dynamic API resolution by hash, string hiding.

    Mitigations: DEP/ASLR/CFG, lab signing/antimalware; common detection surfaces.

    Intro to syscalls for basic operations (no deep unhooking yet; that comes later).

PBR

    Multi-mode loader: technique selected via CLI (at least CRT+LL and APC) with controlled logging.

    Hollowing PoC against a lab binary with evidence and safe rollback.

    Trace comparison: run each technique under your checklist and document artifact deltas.

PAD

    Analysis of encountered mitigations, detection surfaces, and improvement plan for Phase 3/8A/8B.

Success criteria

    Two techniques working reproducibly in the lab.

    Comparative report with evidence and complete checklists.

Express Module F2 — Automation and auxiliary tooling

Duration: 1 week (in parallel, spread across B6–B8)
Goal: accelerate analysis and testing with custom Python/C utilities.

Content

    Parsing scripts (PE/ELF) and string/config extractors.

    Test harness for loaders (in/out, logs, timers).

    Test dataset generation and evidence repos.

Deliverable

    Versioned tools/ folder with documented scripts and basic tests.

Phase 2 grading rubric

    A: Reversing report with clean unpack, usable PE parser, loader with ≥2 techniques, stable hollowing PoC, reproducible documentation.

    B: ≥80% of PBR/PAD, one unstable technique or incomplete parser, sufficient documentation.

    C: ≥60% of PBR/PAD, partial reproducibility issues.

    Redo: <60% or severe instability in loaders/injection.

Bridge to Phase 3 and modules 8A/8B

    With B8 you finish with controlled in-memory execution.

    8A will add realistic Initial Access (maldocs, LNK/HTA/JS, AMSI, LOLBins, WMI)

    8B will measure your techniques via telemetry (Sysmon/ETW, YARA/Sigma, KQL).

    Phase 3 goes deeper into internals and userland/kernel exploitation, building on your loaders.
