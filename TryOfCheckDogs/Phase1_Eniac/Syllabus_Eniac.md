
# SYLLABUS — Fundamentals (Phase 1) — Blocks & Deliverables

> **Coverage:** 2025-08-14 → 2026-02-07
> **Time commitment:** 5 h/day (Mon–Sat)
> **Methodology:** **PBR** (reproducible labs) + **PAD** (analysis & documentation) · OPSEC/Legal applied

## Vision

Build low-level fluency in Linux/CLI, professional toolchains (Git, Make/CMake, debuggers/profilers), Systems C (memory, pointers, I/O), x86\_64/ABI & practical assembly, and linking/loading with ELF (plus high-level PE parallels). Outcomes include in-house utilities, disciplined debugging, and basic binary analysis.

## Phase 1 — Global Deliverables

* **12–15 PBRs** completed with their corresponding **PADs**
* **1** system utility in C with a generic Makefile and local CI
* **1** custom **hexdump** (optional: patcher feature)
* **1** userland hooking demo via **LD\_PRELOAD**
* Lab logbook + minimal OPSEC checklist applied

---

## 0B01 — Linux/CLI/Bash & Ecosystem

**Duration:** 6 weeks · **Goal:** console fluency; file/text pipelines; permissions/processes; safe lab ops.

**Content**

* FHS & permissions: `chmod/chown/chgrp`, `umask`, **ACLs**
* Text flow: pipes, redirection, `grep`, regex (basic), `sed/awk`, `cut/sort/uniq/tr/wc`
* File management: `find`, `xargs`, `tar`, `gzip/xz`, `rsync`
* Processes & signals: `ps`, `top/htop`, `kill`, `nice/renice`, `nohup`, jobs (`bg/fg`)
* Basic networking: `ip` addr/route, `ss`, `ping`, `traceroute`, `/etc/hosts`, DNS
* Packaging (Debian/Ubuntu): repos, `apt`, `dpkg`
* Lab hygiene: snapshots; users/groups; minimal OPSEC hygiene (metadata, timestamps; **PDB/RSDS** mentioned conceptually only)

**PBR**

* **PBR-0.1:** Incremental backup script with verification + rotating logs
* **PBR-0.2:** Log-processing pipeline → normalized CSV
* **PBR-0.3:** Collaborative permissions lab (project/group) with ACLs + tests

**PAD**

* **PAD-0:** VM FHS map, permission tables, pipeline diagrams

**Success criteria**

* Scripts use `set -Eeuo pipefail`, include comments, and handle errors
* **Reproducibility:** `make lab-b1` provisions sample data and executes pipelines cleanly

---

## 1B01 — Toolchain, Debugging & Version Control

**Duration:** 4 weeks · **Goal:** compile/link/debug professionally; instrument diagnostics; measure performance.

**Content**

* Git & workflow: branches, local PRs, hooks, semantic tagging
* Make/CMake: targets, deps, variables, reusable templates
* Compilers: `gcc/clang`, `-O{0,1,2,3}`, `-g`, `-Wall -Wextra -Werror`, LTO
* Sanitizers: Address/Undefined/Leak (`-fsanitize=*`) + assertions
* Debugging & tracing: `gdb/lldb`, `strace/ltrace`, core dumps
* Profiling: `perf`, `time`, basic counters
* Binutils: `readelf`, `objdump`, `nm`, `strings`

**PBR**

* **PBR-1.1:** Generic Makefile template (build/test/clean/asan/ubsan)
* **PBR-1.2:** Memory-bug hunt in C using **ASan** + `gdb`/core dump
* **PBR-1.3:** Micro-benchmark: `memcpy/memmove` vs custom

**PAD**

* **PAD-1:** Failure report (traces, root cause, documented fix) + quick build-template guide

**Success criteria**

* Warning-free builds (`-Wall -Wextra -Werror`)
* **Reproducibility:** `make asan` runs tests and **fails** on UB as expected

---

## 2B01 — Systems C I: Memory, Pointers & I/O

**Duration:** 8 weeks · **Goal:** master memory & pointers, low-level I/O, and safe patterns in C.

**Content**

* Pointers & arithmetic; `const`/`restrict`; function pointers
* Structs/unions/bitfields; alignment & padding
* Dynamic memory: `malloc/calloc/realloc/free`; ownership; simple arenas
* Errors & `errno`; function contracts & pre/postconditions
* I/O: stdio vs syscalls (`open/read/write`), buffers, `mmap`
* Binary files & safe parsing
* Intro to TCP/UDP sockets; blocking vs non-blocking
* Security: bounds, off-by-one, format, double-free, UAF; mitigations

**PBR**

* **PBR-2.1:** Custom **hexdump** (offset + ASCII)
* **PBR-2.2:** Safe mini-strings library (subset) with tests
* **PBR-2.3:** Mini binary viewer (header + first sections) using `mmap`

**PAD**

* **PAD-2:** Function specs & contracts; test cases; threat report + mitigations

**Success criteria**

* Automated tests cover common failures/edges
* Sanitizers clean; `valgrind` shows **no leaks** in planned scenarios

---

## 4B01 — x86\_64/ABI & Practical Assembly

**Duration:** 4 weeks · **Goal:** understand function calls/stack behavior and invoke syscalls.

**Content**

* Registers & SysV x86\_64 calling convention; prologue/epilogue; nested calls
* Stack frames; spill/fill; callee/caller preservation
* System calls: numbers, `syscall`, error paths, `errno`
* Inline asm in C; C ↔ asm integration
* Windows x64 ABI vs SysV (conceptual contrasts)

**PBR**

* **PBR-4.1:** `memset/memcmp` in asm with cross-tests vs C
* **PBR-4.2:** Minimal syscall wrappers (`write`, `getpid`) without libc
* **PBR-4.3:** Mixed C+asm program passing structs (ABI validation)

**PAD**

* **PAD-4:** ABI notes with stack diagrams + comparative micro-benchmarks

**Success criteria**

* Binaries pass tests; benchmark deltas are repeatable and documented

---

## 5B01 — Linking, Loading & Formats (ELF, PLT/GOT, LD\_PRELOAD)

**Duration:** 4 weeks · **Goal:** understand loader symbol resolution and non-intrusive userland interception.

**Content**

* ELF: header; sections vs segments; relocations; symbols
* Static/dynamic linking; PIC/PIE; PLT/GOT; lazy binding
* Tools: `ldd`, `patchelf`, `objdump`, `readelf`
* Shared libraries: creation & symbol visibility
* **LD\_PRELOAD:** non-invasive hooking of standard functions
* PE vs ELF (high level) to prep future transitions

**PBR**

* **PBR-5.1:** Minimal **ELF parser** listing sections & symbols
* **PBR-5.2:** Shared library hook for `fopen/open` (LD\_PRELOAD) with logging
* **PBR-5.3:** Manual relocation PoC: controlled `rpath/runpath` change via `patchelf`

**PAD**

* **PAD-5:** Linking architecture report; before/after symbol tables with evidence

**Success criteria**

* Functional hook that does **not** break basic target apps
* Parser passes tests against sample binaries

---

## EX0B01 — Express Module: Minimal Lab OPSEC (parallel, \~1 week total)

**Goal:** avoid metadata leaks and preserve reproducibility.

**Content**

* Project compartmentalization; artifact control; `strip` where appropriate
* Reproducible metadata: `SOURCE_DATE_EPOCH`, timestamps (concepts), FileVersionInfo (conceptual)
* Artifact usage policies + minimal docs

**Deliverable**

* **OPSEC checklist** signed and applied to all Phase 1 repos

---

## Phase 1 — Grading Rubric

* **A:** All PBR/PAD complete; sanitizers & `valgrind` clean; functional LD\_PRELOAD hook; clear docs; one-command reproducibility
* **B:** ≥80% PBR/PAD; minor sanitizer issues; sufficient documentation
* **C:** ≥60% PBR/PAD; partial reproducibility; test-coverage gaps
* **Redo:** <60% or critical security/stability failures
