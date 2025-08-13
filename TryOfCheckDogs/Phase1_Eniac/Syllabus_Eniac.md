PENSUM — Fundamentals — Blocks and Deliverables

    Coverage: 2025-08-14 → ~02/2026
    Planned dedication: 5 h/day (Mon–Sat)
    Methodology: PBR (reproducible labs) + PAD (analysis and documentation)

Vision

Build low-level fluency in Linux/CLI, systems C, x86_64/ABI and binary formats (ELF/PE) using a professional toolchain (Git, Make/CMake, debuggers and profilers). Phase 1 outcomes include in-house utilities, mastery of C memory and pointers, practical understanding of linking/loading, and basic binary analysis skills.

Phase 1 global deliverables

    8–12 PBRs completed with their corresponding PADs

    1 system utility in C with a generic Makefile and local CI

    1 simple hexdump/patcher

    1 userland hooking demo (LD_PRELOAD)

    Lab logbook and minimal OPSEC checklist

Block 1 — Linux/CLI/Bash and ecosystem

Duration: 6 weeks
Goal: operate confidently in the console, manipulate files/text, manage permissions and processes, and work safely in an isolated lab.

Content

    FHS and permissions: chmod/chown/chgrp, umask, ACLs

    Text flow: pipes, redirection, grep, basic regex, sed, awk, cut, sort, uniq, tr, wc

    File management: find, xargs, tar, gzip, rsync

    Processes and signals: ps, top/htop, kill, nice/renice, nohup, jobs/bg/fg

    Basic networking: ip addr/route, ss, ping, traceroute, /etc/hosts, DNS

    Packaging (Debian/Ubuntu): repos, apt, dpkg

    Lab hygiene: snapshots, users/groups, minimal OPSEC hygiene (metadata, timestamps; PDB/RSDS on Windows only conceptually)

PBR

    Incremental backup script with verification and rotating logs

    Log-processing pipeline with filters and CSV summary

    Collaborative permissions lab (project/group) with ACLs and test cases

PAD

    Report including the VM’s FHS layout, permission tables, and pipeline flow diagrams

Success criteria

    Scripts use set -Eeuo pipefail, are commented, and handle errors

    Reproducibility: make lab-b1 provisions sample data and executes pipelines

Block 2 — Toolchain, debugging, and version control

Duration: 4 weeks
Goal: compile, link, and debug professionally; instrument diagnostics and measure performance.

Content

    Git and workflow: branches, local PRs, hooks, semantic tagging

    Make/CMake: targets, dependencies, variables, reusable templates

    Compilers: gcc/clang, -O{0,1,2,3}, -g, -Wall -Wextra -Werror, LTO

    Sanitizers: Address/UB/Leak; -fsanitize and assertions

    Debugging and tracing: gdb/lldb, strace/ltrace, core dumps

    Profiling: perf, time, basic counters

    Binary utilities: readelf, objdump, nm, strings

PBR

    Generic Makefile template with build/test/clean/asan/ubsan targets

    Memory-bug hunt in C using ASan and gdb with core dump

    Micro-benchmark comparing memcpy/memmove vs custom versions

PAD

    Failure report with traces, root cause, and documented fix

    Quick guide to your build template

Success criteria

    Warning-free builds with -Wall -Wextra -Werror

    Reproducibility: make asan runs tests and fails on UB presence

Block 3 — Systems C I: memory, pointers, and I/O

Duration: 8 weeks
Goal: master memory and pointers, low-level I/O, and safe patterns in C.

Content

    Pointers, arithmetic, const, restrict, function pointers

    Structures, unions, and bitfields; alignment and padding

    Dynamic memory: malloc/calloc/realloc/free, ownership, simple arenas

    Errors and errno; function contracts and preconditions

    I/O: stdio vs syscalls (open/read/write), buffers, mmap

    Binary files and safe parsing

    Intro to TCP/UDP sockets and blocking vs non-blocking

    Security: bounds, off-by-one, format, double-free, use-after-free; mitigation strategies

PBR

    Custom hexdump with offset and ASCII support

    Safe string library (subset) with tests

    Mini binary viewer (header + first sections) using mmap

PAD

    Function specs, contracts, and test cases

    Threat report and mitigations for your utilities

Success criteria

    Automated tests covering common failures

    Clean sanitizers and valgrind free of leaks in planned scenarios

Block 4 — x86_64 architecture and ABI; practical assembly

Duration: 4 weeks
Goal: understand how functions are called, how the stack behaves, and how to invoke syscalls.

Content

    Registers and SysV x86_64 calling convention; prologue/epilogue; nested calls

    Stack frames, spill/fill, register preservation

    System calls: numbers, syscall, errors, and errno

    Inline asm in C; C ↔ asm integration

    Windows x64 ABI vs SysV (conceptual differences)

PBR

    Assembly implementation of memset/memcmp with cross-tests against C

    Minimal syscall wrapper (write, getpid) without libc

    Mixed C+asm program passing structures, verifying ABI

PAD

    ABI notes with stack diagrams

    Comparative benchmarks of your routines

Success criteria

    Binaries pass tests and show repeatable performance deltas

Block 5 — Linking, loading, and formats (ELF, PLT/GOT, LD_PRELOAD)

Duration: 4 weeks
Goal: understand how the loader resolves symbols and how to intercept calls in userland.

Content

    ELF: header, sections vs segments, relocations, symbols

    Static/dynamic linking; PIC/PIE; PLT/GOT and lazy binding

    Tools: ldd, patchelf, objdump, readelf

    Shared libraries: creation and symbol visibility

    LD_PRELOAD: non-invasive hooking of standard functions

    PE vs ELF (high level) to prepare future transition

PBR

    Minimal ELF parser listing sections and symbols

    Shared library that hooks fopen/open to log access (LD_PRELOAD)

    Manual relocation PoC: controlled rpath/runpath change using patchelf

PAD

    Linking architecture report for your binaries

    Symbol tables before/after hooking with evidence

Success criteria

    Functional hook without breaking basic target apps

    Parser passes test cases with sample binaries

Express Module F1 — Minimal lab OPSEC

Duration: 1 week (in parallel, spread across block endings)
Goal: avoid metadata leaks and keep reproducibility.

Content

    Project-level compartmentalization, artifact control, and symbol stripping (strip)

    Metadata: SOURCE_DATE_EPOCH, timestamps, FileVersionInfo (conceptual)

    Artifact usage policies and minimal documentation

Deliverable

    OPSEC checklist signed and applied to all Phase 1 repos

Phase 1 grading rubric

    A: All PBR/PAD completed; sanitizers and valgrind clean; functional hooking; clear docs; one-command reproducibility.

    B: ≥80% PBR/PAD; minor sanitizer issues; sufficient documentation.

    C: ≥60% PBR/PAD; partial reproducibility; test coverage gaps.

    Redo: <60% or critical security/stability failures.
