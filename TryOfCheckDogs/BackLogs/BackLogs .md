BackLogs — Segment 1 (F1–F2 + F3-start)

Mini-challenge pack for the Bug Bounty period (v1.0)

    Usage: weekly reinforcement (6–8 h) during 2026-09-21 → 2027-07-21
    Scope: content from Phase 1, Phase 2, and Phase 3 (start)
    Format: 15–60 min katas with acceptance criteria and minimal evidence (PBR-lite + PAD-lite)

Ground rules

    Timeboxing: S = 15 min, M = 30 min, L = 45 min, XL = 60 min. If it doesn’t land, log the blocker and move on.

    Minimum evidence (per challenge): script/command or PoC, output/artifact, 1–3 screenshots, 3–5 lines of lessons learned.

    Repository: everything goes under backlogs/YY-WW/<challenge-ID>/ with a short README.md and optional Makefile.

    OPSEC/Legal: isolated lab only, your own binaries or didactic samples; never third-party executables outside the lab.

Suggested folder layout

backlogs/
  2026-W39/
    B1-CLI-01/
      README.md
      run.sh | run.py | Makefile
      evidence/
        out.txt
        screenshot_1.png
        hash.txt
    B2-TOOL-02/
    ...

Two-week cycle (template)

    Week A (4 h): 1 challenge from each category: CLI, Toolchain, C, ELF/PE.

    Week B (4 h): Reversing/Unpack, Loaders, Internals/ROP, Free review.

    Close each week with one single report Wxx-summary.md (max 200 words).

Mini-challenge catalog

    Each entry includes: ID · Title · Effort · Prereq · Task · Acceptance criteria · Deliverables

1) Linux/CLI/Bash

B1-CLI-01 · Log pipeline with severity summary · S
Prereq: grep/sed/awk.
Task: given samples/syslog.log, generate sev,count CSV.
Acceptance: summary.csv is correct and reproducible with make run.
Deliverables: script, CSV, 1 screenshot.

B1-CLI-02 · Incremental copy with rotation · M
Prereq: tar/rsync, dates.
Task: back up ~/project to ~/bk/ with 7-day rotation.
Acceptance: three consecutive runs show only changes.
Deliverables: script, log, hash listing.

B1-CLI-03 · Collaborative permissions with ACL · M
Prereq: chmod/setfacl.
Task: team/ folder for lab group with read-only for guests.
Acceptance: tests with 3 users simulate rules.
Deliverables: playbook, screenshots.

B1-CLI-04 · IOC list filter · S
Task: normalize indicators (IPs/domains/SHA256) into a single TSV.
Acceptance: TSV is deduplicated and sorted.
Deliverables: script + TSV.

B1-CLI-05 · Local DNS recon · S
Task: resolve 10 domains and map ASNs (domains.txt).
Acceptance: domain,ip,asn table.
Deliverables: script, CSV.

B1-CLI-06 · Smart text-diff · M
Task: generate a diff that ignores spaces and dates.
Acceptance: report with 3 test cases.
Deliverables: script, fixtures, README.

B1-CLI-07 · Cron process watchdog · M
Task: script that restarts a process if it dies.
Acceptance: test with a dummy process.
Deliverables: script, log.

B1-CLI-08 · Error-count one-liner · S
Task: count occurrences by pattern across 3 files.
Acceptance: stable, ordered output.
Deliverables: command, out.
2) Toolchain/Debugging

B2-TOOL-01 · Minimal Makefile template · S
Task: targets build/test/asan/clean.
Acceptance: make asan runs tests and fails on UB.
Deliverables: Makefile + test.

B2-TOOL-02 · Leak hunt with ASan · M
Task: locate and fix a leak in leaky.c.
Acceptance: ASan clean.
Deliverables: diff + log.

B2-TOOL-03 · strace vs ltrace · M
Task: compare syscalls and libraries for a binary.
Acceptance: comparison table with 5 observations.
Deliverables: outputs and summary.

B2-TOOL-04 · Post-mortem core dump · M
Task: reproduce a crash and extract a backtrace.
Acceptance: root cause identified.
Deliverables: core, commands, notes.

B2-TOOL-05 · memcpy micro-benchmark · S
Task: measure 3 variants.
Acceptance: simple chart and conclusions.
Deliverables: code + PNG.
3) Systems C

B3-C-01 · Custom hexdump · M
Task: offsets, ASCII at right.
Acceptance: matches a known sample.
Deliverables: binary, tests.

B3-C-02 · Mini-strings library · M
Task: x_strlcpy/strnlen_s and tests.
Acceptance: coverage >80%.
Deliverables: lib + tests.

B3-C-03 · Safe binary parser · L
Task: read a simple header with checks.
Acceptance: rejects corrupted inputs.
Deliverables: code + corpus.

B3-C-04 · mmap section viewer · L
Task: map a file and list regions.
Acceptance: works on 3 binaries.
Deliverables: tool + screenshots.

B3-C-05 · Minimal TCP client · M
Task: connect, send, correct timeout handling.
Acceptance: tests with echo server.
Deliverables: code + log.

B3-C-06 · Parser fuzzing (honggfuzz/AFL) · XL
Task: run for 20 min and fix any crash.
Acceptance: crash-free at the end.
Deliverables: corpus + fix.

B3-C-07 · errno and contracts · S
Task: function with pre/post conditions.
Acceptance: error-path tests pass.
Deliverables: code + tests.
4) x86_64/ABI/asm

B4-ASM-01 · memset in asm · M
Acceptance: passes comparative suite.
Deliverables: asm + bench.

B4-ASM-02 · Syscall wrapper · M
Task: write, getpid without libc.
Acceptance: correct output and valid errno.
Deliverables: code + README.

B4-ASM-03 · C↔asm structs · M
Task: pass a struct by value.
Acceptance: consistency on both sides.
Deliverables: code + tests.
5) ELF/PE/Linking

B5-ELF-01 · Minimal ELF parser · M
Acceptance: lists sections and symbols.
Deliverables: tool + test binaries.

B5-ELF-02 · LD_PRELOAD hook · L
Task: intercept open/fopen.
Acceptance: access log without breaking the process.
Deliverables: .so + demo.

B5-ELF-03 · PLT/GOT inspection · M
Task: show entries for 3 functions.
Acceptance: evidence with objdump/readelf.
Deliverables: script + screenshots.

B5-PE-04 · PE header dump · M
Task: print DOS/NT/sections.
Acceptance: matches PE-bear.
Deliverables: tool + diff.

B5-PE-05 · TLS callback detect · M
Task: locate and print callbacks.
Acceptance: demo on a lab DLL.
Deliverables: script + evidence.
6) Reversing/Unpack

B6-REV-01 · XOR-obfuscated strings · S
Task: decoder and validation.
Acceptance: complete, clean list.
Deliverables: script + output.

B6-REV-02 · Manual UPX unpack · L
Task: dump + basic IAT repair.
Acceptance: runs and opens in Ghidra without major errors.
Deliverables: dump + guide.

B6-REV-03 · Breakpoint traps · M
Task: bypass IsDebuggerPresent and simple timing checks.
Acceptance: stable x64dbg session.
Deliverables: notes + symbols.

B6-REV-04 · Initial CFG · S
Task: extract CFG and flag critical functions.
Acceptance: 3 annotated findings.
Deliverables: PNG + markdown.
7) Loaders/Userland execution

B7-LOD-01 · Local shellcode loader · M
Acceptance: benign execution with cleanup.
Deliverables: code + logs.

B7-LOD-02 · Basic manual map · L
Acceptance: minimal DLL executes an export.
Deliverables: code + evidence.

B7-LOD-03 · Dual mode (CRT+LL / APC) · L
Acceptance: CLI selector and logs.
Deliverables: binary + README.

B7-LOD-04 · Comparative traces · M
Task: compare artifacts of 2 techniques.
Acceptance: table and conclusions.
Deliverables: report.
8) Internals/ROP (educational)

B8-ROP-01 · Basic gadget hunt · M
Task: list 10 useful gadgets in your own binary.
Acceptance: table with offsets and a working demo for 1 gadget.
Deliverables: script + notes.

B8-ROP-02 · Register setter ROP · L
Task: chain that sets a key register and verification.
Acceptance: consistent state in the debugger.
Deliverables: PoC + screenshots.

B8-ROP-03 · DEP awareness · M
Task: document DEP’s impact on your PoC and a safe alternative.
Acceptance: clear, reproducible comparison.
Deliverables: short report.

# PAD-lite (template)
-
## Challenge <ID> — <Title>
## Objective
## Key steps
## Evidence
out.txt / screenshot(s)
## Lessons
3–5 bullets
- 


Control metrics (weekly)

    Challenges completed (target: 4/week)

    Effective time (target: 6–8 h/week)

    Open/closed blockers

    “Signal vs noise” in PoCs (when applicable)

Cycle close-out (biweekly)

    Wxx-summary.md with: what worked, what didn’t, next 4 challenges, and 1 automation idea for tooling.

Final note

This pack does NOT replace TOCD progression. It keeps hands, memory, and judgment sharp during the Bug Bounty window without opening new fronts. 
Adjust difficulty based on fatigue and academic load.
