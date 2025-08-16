
# Phase 1 — Systems & Programming Fundamentals

> Coverage: **2025-08-14 → \~02/2026**
> Time commitment: **5 h/day (Mon–Sat)**
> Methodology: **PBR** (reproducible labs) + **PAD** (analysis & documentation) · OPSEC/Legal applied

## Table of Contents

1. [Phase objective](#phase-objective)
2. [Scope & expected outcomes](#scope--expected-outcomes)
3. [Blocks & content](#blocks--content)

   * [B1: Linux/CLI/Bash & ecosystem](#b1-linuxclibash--ecosystem)
   * [B2: Toolchain, debugging & version control](#b2-toolchain-debugging--version-control)
   * [B3: Systems C I (memory, pointers & io)](#b3-systems-c-i-memory-pointers--io)
   * [B4: x86\_64, ABI & practical assembly](#b4-x86_64-abi--practical-assembly)
   * [B5: Linking, loading & formats (ELF/PLT-GOT/LD\_PRELOAD)](#b5-linking-loading--formats-elfplt-gotld_preload)
4. [Global deliverables](#global-deliverables)
5. [Success criteria](#success-criteria)

---

## Executive summary

**Purpose.** Build real low-level fluency: operate Linux comfortably from the console, use a professional toolchain (Git, Make/CMake, debuggers and sanitizers), write secure and performant **C**, understand **x86\_64 architecture** and its **ABI**, and grasp how binaries are **linked and loaded** (**ELF**, **PLT/GOT**). The phase closes with a userland **hooking** demo via `LD_PRELOAD` and home-grown analysis utilities.

**End-of-phase outcomes.**

* Practical command of memory, pointers, and I/O in C.
* Ability to compile, debug, and profile to professional standards.
* Understanding of the ABI and syscalls; C↔asm integration.
* Ability to read ELF binaries, use PLT/GOT, and build shared libraries.
* Real tools delivered: `hexdump`/patcher, `mmap`-based binary viewer, ELF parser, and an `LD_PRELOAD` hook.
* Reproducible evidence (PBR + PAD) and a minimal OPSEC checklist applied.

---

## Blocks & content

### B1: Linux/CLI/Bash & ecosystem

* FHS, permissions/ACLs, users and processes; text pipelines with `grep/sed/awk`; `find/xargs`, `tar/gzip/rsync`; basic networking (`ip/ss`, DNS).
* **PBR:** rotating incremental backup; log-processing pipeline; ACL permissions lab.
* **PAD:** report on FHS, permissions, and pipelines.

### B2: Toolchain, debugging & version control

* Git (branches, hooks), Make/CMake; `gcc/clang` and flags; sanitizers (ASan/UBSan/Leak); `gdb/lldb`, `strace/ltrace`, `perf`; binutils (`readelf/objdump/nm/strings`).
* **PBR:** generic Makefile; memory-bug hunt with ASan; `memcpy/memmove` micro-benchmark.
* **PAD:** failure analysis report and build guide.

### B3: Systems C I (memory, pointers & I/O)

* Pointers and function pointers; structs/bitfields; dynamic memory and contracts; stdio vs syscalls; `mmap`; safe binary parsing; intro to sockets; secure patterns.
* **PBR:** custom `hexdump`; mini-strings library with tests; `mmap` binary viewer.
* **PAD:** specifications, test cases, and threat/mitigation notes.

### B4: x86\_64, ABI & practical assembly

* SysV x86\_64 calling convention; stack frames; syscalls; inline asm and C↔asm calls; high-level differences vs Windows x64.
* **PBR:** `memset/memcmp` in asm; syscall wrappers without libc; mixed C+asm program validating the ABI.
* **PAD:** ABI notes and benchmarks.

### B5: Linking, loading & formats (ELF/PLT-GOT/LD\_PRELOAD)

* ELF (headers, sections/segments, relocations, symbols); static/dynamic linking; PIC/PIE; PLT/GOT; `ldd`, `patchelf`.
* **PBR:** minimal ELF parser; **hook** for `open/fopen` via `LD_PRELOAD`; controlled relocation PoC (`rpath/runpath`).
* **PAD:** linking architecture and symbol tables before/after.

---

## Global deliverables

* **8–12 PBRs** closed with their **PADs**.
* 1 system utility in C with a generic Makefile and local CI.
* 1 simple **hexdump/patcher**.
* 1 userland **hooking** demo (`LD_PRELOAD`).
* Lab logbook and **minimal OPSEC checklist**.

---

## Success criteria

* Warning-free builds with `-Wall -Wextra -Werror`; clean sanitizers and `valgrind`.
* PBRs reproducible with a single command (`make <target>`), versioned evidence, and clear PADs.
* Functional `LD_PRELOAD` hook and an ELF parser that passes test cases.

