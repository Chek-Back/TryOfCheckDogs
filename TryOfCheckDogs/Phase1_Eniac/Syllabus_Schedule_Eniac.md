> Coverage: **2025-08-14 → 2026-02-07**
> Time commitment: **5 h/day (Mon–Sat)**
> Methodology: **PBR** (reproducible labs) + **PAD** (analysis & documentation)

---

# **Quarter 1 (2025-08-14 → 2025-11-30)**

## **0B01 — Linux/CLI/Bash & Ecosystem**

### **Stack 0: CLI/Bash**

#### Week 0 — 2025-08-14 → 2025-08-16 (B1)

* **Thu 14 Aug** · VM setup and snapshots; FHS structure · **5 h**
* **Fri 15 Aug** · Bash basics: pipes, redirections, globs; aliases and profile · **5 h**
* **Sat 16 Aug** · Permissions: chmod/chown/umask; users/groups; ACL intro · **5 h**

#### Week 1 — 2025-08-18 → 2025-08-23 (B1)

* **Mon 18 Aug** · Deep FHS; layout of /etc, /var, /usr; quick search · **5 h**
* **Tue 19 Aug** · Permissions & ACLs: setfacl/getfacl with cases · **5 h**
* **Wed 20 Aug** · Text flow I: grep/regex; cut/sort/uniq/tr/wc · **5 h**
* **Thu 21 Aug** · Text flow II: sed/awk intro with pipelines · **5 h**
* **Fri 22 Aug** · PBR1 plan: incremental Backup Script spec · **5 h**
* **Sat 23 Aug** · PBR1 execution: Backup Script + rotating logs · **5 h**

#### Week 2 — 2025-08-25 → 2025-08-30 (B1)

* **Mon 25 Aug** · Advanced awk: grouping and summaries · **5 h**
* **Tue 26 Aug** · Advanced sed: block edits; backrefs · **5 h**
* **Wed 27 Aug** · Log pipeline: normalization and CSV · **5 h**
* **Thu 28 Aug** · Validation: datasets and edge tests · **5 h**
* **Fri 29 Aug** · PBR2 plan: reproducible log pipeline · **5 h**
* **Sat 30 Aug** · PBR2 execution and PAD-lite · **5 h**

#### Week 3 — 2025-09-01 → 2025-09-06 (B1)

* **Mon 01 Sep** · find/xargs patterns; prune; performance · **5 h**
* **Tue 02 Sep** · tar/gzip/bzip2/xz; integrity and hashes · **5 h**
* **Wed 03 Sep** · rsync modes; exclusions; protected --delete · **5 h**
* **Thu 04 Sep** · Cron and backup rotation; failure triage · **5 h**
* **Fri 05 Sep** · PBR3 plan: 7-day rotating incremental backup · **5 h**
* **Sat 06 Sep** · PBR3 execution and evidence · **5 h**

#### Week 4 — 2025-09-08 → 2025-09-13 (B1)

* **Mon 08 Sep** · Processes: ps/top/htop; states and hierarchy · **5 h**
* **Tue 09 Sep** · Signals: kill/nice/renice; nohup; jobs/bg/fg · **5 h**
* **Wed 10 Sep** · Supervision: watchdog scripts and logging · **5 h**
* **Thu 11 Sep** · Collaborative ACLs: team/ folder design · **5 h**
* **Fri 12 Sep** · PBR4 plan: ACL permissions lab · **5 h**
* **Sat 13 Sep** · PBR4 execution and user tests · **5 h**

#### Week 5 — 2025-09-15 → 2025-09-20 (B1)

* **Mon 15 Sep** · Basic networking: ip/ss, DNS, /etc/hosts, traceroute · **5 h**
* **Tue 16 Sep** · Package management: apt/dpkg; repos; basic pinning · **5 h**
* **Wed 17 Sep** · Minimal OPSEC: metadata, timestamps, SOURCE\_DATE\_EPOCH · **5 h**
* **Thu 18 Sep** · PAD B1: documentation and diagrams · **5 h**
* **Fri 19 Sep** · B1 consolidation and comprehensive review · **5 h**
* **Sat 20 Sep** · Buffer/reserve for demanding practice · **5 h**

---

## **1B01 — Toolchain, Debugging & Version Control**

### **Stack 1: Toolchain**

#### Week 6 — 2025-09-22 → 2025-09-27 (B2)

* **Mon 22 Sep** · Git workflow: branches, local PRs, pre-commit hooks · **5 h**
* **Tue 23 Sep** · Make: targets, variables, reusable templates · **5 h**
* **Wed 24 Sep** · CMake: minimal project and toolchains · **5 h**
* **Thu 25 Sep** · Binutils: readelf/objdump/nm/strings practical uses · **5 h**
* **Fri 26 Sep** · PBR5 plan: generic Makefile template · **5 h**
* **Sat 27 Sep** · PBR5 execution: Makefile + tests · **5 h**

#### Week 7 — 2025-09-29 → 2025-10-04 (B2)

* **Mon 29 Sep** · Compilers: -O\*, -g, -Wall/-Wextra/-Werror, LTO · **5 h**
* **Tue 30 Sep** · Sanitizers: ASan/UBSan/LeakSan; instrumentation · **5 h**
* **Wed 01 Oct** · Debugging with gdb/lldb and core dumps · **5 h**
* **Thu 02 Oct** · strace/ltrace comparison; selective tracing · **5 h**
* **Fri 03 Oct** · PBR6 plan: memory-bug hunt with ASan · **5 h**
* **Sat 04 Oct** · PBR6 execution: locate and fix leak/UB · **5 h**

#### Week 8 — 2025-10-06 → 2025-10-11 (B2)

* **Mon 06 Oct** · Debugging techniques: breakpoints, watchpoints · **5 h**
* **Tue 07 Oct** · Post-mortem core: analysis and root report · **5 h**
* **Wed 08 Oct** · Test automation with make and scripts · **5 h**
* **Thu 09 Oct** · perf and measurement: basic CPU profiles · **5 h**
* **Fri 10 Oct** · PAD B2: failure report and build guide · **5 h**
* **Sat 11 Oct** · Practice buffer: additional scenarios · **5 h**

#### Week 9 — 2025-10-13 → 2025-10-18 (B2)

* **Mon 13 Oct** · Micro-benchmarks: methodology and pitfalls · **5 h**
* **Tue 14 Oct** · memcpy/memmove: glibc vs custom · **5 h**
* **Wed 15 Oct** · Measurement & plots; interpreting noise · **5 h**
* **Thu 16 Oct** · Safe optimization and limits · **5 h**
* **Fri 17 Oct** · PBR7 plan: comparative micro-benchmark · **5 h**
* **Sat 18 Oct** · PBR7 execution + results · **5 h**

---

## **2B01 — Systems C I (start)**

### **Stack 2: Systems C**

#### Week 10 — 2025-10-20 → 2025-10-25 (B3)

* **Mon 20 Oct** · Pointers I: basics, arithmetic, const/restrict · **5 h**
* **Tue 21 Oct** · Pointers II: function pointers and callbacks · **5 h**
* **Wed 22 Oct** · Strings and buffers; bounds and safety · **5 h**
* **Thu 23 Oct** · Unit testing: lightweight C framework · **5 h**
* **Fri 24 Oct** · PBR8 plan: mini-strings library · **5 h**
* **Sat 25 Oct** · PBR8 execution: implementation and tests · **5 h**

#### Week 11 — 2025-10-27 → 2025-11-01 (B3)

* **Mon 27 Oct** · Structs/unions/bitfields; padding and alignment · **5 h**
* **Tue 28 Oct** · Safer strings API: contracts and errno · **5 h**
* **Wed 29 Oct** · Test coverage and edge cases · **5 h**
* **Thu 30 Oct** · Peer review (simulated) and refactoring · **5 h**
* **Fri 31 Oct** · Partial PAD B3: specifications and cases · **5 h**
* **Sat 01 Nov** · Practice buffer: library robustness · **5 h**

#### Week 12 — 2025-11-03 → 2025-11-08 (B3)

* **Mon 03 Nov** · hexdump: design, offsets, ASCII, formatting · **5 h**
* **Tue 04 Nov** · I/O: stdio vs syscalls; open/read/write · **5 h**
* **Wed 05 Nov** · Buffers and performance; readv/writev intro · **5 h**
* **Thu 06 Nov** · Validation with sanitizers and valgrind · **5 h**
* **Fri 07 Nov** · PBR9 plan: custom hexdump · **5 h**
* **Sat 08 Nov** · PBR9 execution: hexdump + tests · **5 h**

#### Week 13 — 2025-11-10 → 2025-11-15 (B3)

* **Mon 10 Nov** · Dynamic memory: malloc/calloc/realloc/free · **5 h**
* **Tue 11 Nov** · Ownership and simple arenas; safe patterns · **5 h**
* **Wed 12 Nov** · Detecting UAF/double-free with sanitizers · **5 h**
* **Thu 13 Nov** · Lightweight fuzzing of the hexdump · **5 h**
* **Fri 14 Nov** · PBR9 refinement and documentation · **5 h**
* **Sat 15 Nov** · Buffer/fixes per fuzzing · **5 h**

#### Week 14 — 2025-11-17 → 2025-11-22 (B3)

* **Mon 17 Nov** · Binary parsing: headers and validations · **5 h**
* **Tue 18 Nov** · mmap I: mapping and protecting regions · **5 h**
* **Wed 19 Nov** · mmap II: section viewer and limits · **5 h**
* **Thu 20 Nov** · Errors and systematic errno handling · **5 h**
* **Fri 21 Nov** · PBR10 plan: mini binary viewer with mmap · **5 h**
* **Sat 22 Nov** · PBR10 execution: viewer with evidence · **5 h**

#### Week 15 — 2025-11-24 → 2025-11-29 (B3)

* **Mon 24 Nov** · TCP/UDP sockets intro and blocking · **5 h**
* **Tue 25 Nov** · Non-blocking and timeouts; select/poll intro · **5 h**
* **Wed 26 Nov** · Simple echo client; robust error handling · **5 h**
* **Thu 27 Nov** · Local network tests in VM · **5 h**
* **Fri 28 Nov** · PAD B3: threats and mitigations · **5 h**
* **Sat 29 Nov** · Networking practice buffer · **5 h**

---

# **Quarter 2 (2025-12-01 → 2026-02-07)**

## **3B01 — Systems C I (wrap-up)**

### **Stack 2: Systems C**

#### Week 16 — 2025-12-01 → 2025-12-06 (B3)

* **Mon 01 Dec** · B3 full review: utilities integration · **5 h**
* **Tue 02 Dec** · Sanitizers & valgrind cleanup · **5 h**
* **Wed 03 Dec** · Final test coverage · **5 h**
* **Thu 04 Dec** · Packaging and local CI · **5 h**
* **Fri 05 Dec** · Close PAD B3 · **5 h**
* **Sat 06 Dec** · Buffer for demanding practice · **5 h**

#### Week 17 — 2025-12-08 → 2025-12-13 (B3)

* **Mon 08 Dec** · Buffer week: recovery and reinforcement · **5 h**
* **Tue 09 Dec** · Selected advanced cases · **5 h**
* **Wed 10 Dec** · Documentation and examples · **5 h**
* **Thu 11 Dec** · OPSEC checklist applied to repos · **5 h**
* **Fri 12 Dec** · Simulated external review · **5 h**
* **Sat 13 Dec** · Close B3 · **5 h**

---

## **4B01 — x86\_64/ABI/ASM**

### **Stack 3: x86\_64/ABI/asm**

#### Week 18 — 2025-12-15 → 2025-12-20 (B4)

* **Mon 15 Dec** · x86\_64 registers, calls, prologue/epilogue · **5 h**
* **Tue 16 Dec** · Stack frames, spill/fill, preservation · **5 h**
* **Wed 17 Dec** · Nested calls and common pitfalls · **5 h**
* **Thu 18 Dec** · Hands-on with simple functions · **5 h**
* **Fri 19 Dec** · PBR11 plan: memset/memcmp in asm · **5 h**
* **Sat 20 Dec** · PBR11 execution + cross-tests · **5 h**

#### Week 19 — 2025-12-22 → 2025-12-27 (B4)

* **Mon 22 Dec** · Syscalls: numbers, syscall, errno · **5 h**
* **Tue 23 Dec** · Minimal wrappers without libc · **5 h**
* **Wed 24 Dec** · Errors and return paths · **5 h**
* **Thu 25 Dec** · Inline asm in C · **5 h**
* **Fri 26 Dec** · PBR12 plan: write/getpid wrappers · **5 h**
* **Sat 27 Dec** · PBR12 execution with tests · **5 h**

#### Week 20 — 2025-12-29 → 2026-01-03 (B4)

* **Mon 29 Dec** · C+asm integration: structs by value · **5 h**
* **Tue 30 Dec** · ABI alignment and checks · **5 h**
* **Wed 31 Dec** · Comparative routine benchmarks · **5 h**
* **Thu 01 Jan** · Benchmark automation · **5 h**
* **Fri 02 Jan** · PAD B4: ABI notes + results · **5 h**
* **Sat 03 Jan** · Assembly practice buffer · **5 h**

#### Week 21 — 2026-01-05 → 2026-01-10 (B4)

* **Mon 05 Jan** · Windows x64 vs SysV: differences · **5 h**
* **Tue 06 Jan** · Review and cleanup of examples · **5 h**
* **Wed 07 Jan** · Refactor wrappers and asm · **5 h**
* **Thu 08 Jan** · Close PAD B4 · **5 h**
* **Fri 09 Jan** · Demanding buffer · **5 h**
* **Sat 10 Jan** · Close B4 · **5 h**

---

## **5B01 — Linking, Loading & Formats (ELF, PLT/GOT, LD\_PRELOAD)**

### **Stack 4: ELF/Linking**

#### Week 22 — 2026-01-12 → 2026-01-17 (B5)

* **Mon 12 Jan** · ELF: header and sections vs segments · **5 h**
* **Tue 13 Jan** · Relocations and symbols · **5 h**
* **Wed 14 Jan** · Tools: readelf/objdump hands-on · **5 h**
* **Thu 15 Jan** · Minimal ELF parser design · **5 h**
* **Fri 16 Jan** · PBR13 plan: ELF parser · **5 h**
* **Sat 17 Jan** · PBR13 execution + tests · **5 h**

#### Week 23 — 2026-01-19 → 2026-01-24 (B5)

* **Mon 19 Jan** · Static/dynamic linking; PIC/PIE · **5 h**
* **Tue 20 Jan** · PLT/GOT and lazy binding · **5 h**
* **Wed 21 Jan** · ldd and dependency diagnostics · **5 h**
* **Thu 22 Jan** · Parser validation against binaries · **5 h**
* **Fri 23 Jan** · Partial PAD B5: linking architecture · **5 h**
* **Sat 24 Jan** · Parser practice buffer · **5 h**

#### Week 24 — 2026-01-26 → 2026-01-31 (B5)

* **Mon 26 Jan** · Shared libraries and symbol visibility · **5 h**
* **Tue 27 Jan** · Building .so and exports · **5 h**
* **Wed 28 Jan** · LD\_PRELOAD: hooking fopen/open · **5 h**
* **Thu 29 Jan** · Stability tests and side effects · **5 h**
* **Fri 30 Jan** · PBR14 plan: LD\_PRELOAD hook · **5 h**
* **Sat 31 Jan** · PBR14 execution + evidence · **5 h**

#### Week 25 — 2026-02-02 → 2026-02-07 (B5)

* **Mon 02 Feb** · rpath/runpath and patchelf · **5 h**
* **Tue 03 Feb** · Controlled manual relocation PoC · **5 h**
* **Wed 04 Feb** · Before/after symbol comparisons · **5 h**
* **Thu 05 Feb** · PAD B5: symbol table + evidence · **5 h**
* **Fri 06 Feb** · Minimal OPSEC checklist applied to F1 · **5 h**
* **Sat 07 Feb** · F1 closure and evaluation/rubric · **5 h**

