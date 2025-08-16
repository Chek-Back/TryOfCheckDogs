
> **Coverage:** 2025-08-14 → 2026-02-07
> **Time commitment:** 5 h/day (Mon–Sat)
> **Methodology:** **PBR** (reproducible labs) + **PAD** (analysis & docs)

---

# **0B05 — Linux/CLI/Bash & Ecosystem**

**Target:** 6 weeks · **Outcomes:** CLI fluency; PBR-0.1/0.2/0.3/0.4; PAD-0

### **Stack 1 — FHS, Users & Permissions**

**Week 0–1**: FHS; chmod/chown/umask; users/groups; ACL intro

* **PBR-0.1:** Incremental backup script w/ rotation + logs

### **Stack 2 — Text Processing (grep/sed/awk)**

**Week 1–2**: regex; cut/sort/uniq/tr/wc; sed/awk pipelines

* **PBR-0.2:** Log pipeline → normalized CSV (reproducible)

### **Stack 3 — Archiving/Sync & Scheduling**

**Week 3**: find/xargs; tar/*zip*; hashes; rsync; cron

* **PBR-0.3:** 7-day rotating backup (evidence + tests)

### **Stack 4 — Processes & Supervision**

**Week 4**: ps/top/htop; signals; watchdog & logging

* **PBR-0.4:** ACL lab (collab folder) + user tests

### **Stack 5 — Net/Packages & OPSEC-mini**

**Week 5**: ip/ss, DNS, /etc/hosts, traceroute; apt/dpkg; OPSEC minima

* **PAD-0:** B1 documentation & diagrams

---

# **1B04 — Toolchain, Debugging & Version Control**

**Target:** 4 weeks · **Outcomes:** Makefile template; ASan bug-fix; micro-benchmark; PAD-1

### **Stack 1 — Git & Build System**

**Week 0**: Git branches/PR hooks; Make targets/vars; CMake basics

* **PBR-1.1:** Generic Makefile template (+ tests)

### **Stack 2 — Sanitizers & Debugging**

**Week 1**: gcc/clang flags; ASan/UBSan/LeakSan; gdb/lldb; strace/ltrace

* **PBR-1.2:** Memory-bug hunt (ASan) → fix validated

### **Stack 3 — Testing & Profiling**

**Week 2**: core post-mortem; perf; automation of tests

* **PAD-1:** Failure report & build guide

### **Stack 4 — Micro-benchmarks & Reporting**

**Week 3**: methodology; memcpy/memmove (glibc vs custom); plots

* **PBR-1.3:** Comparative micro-benchmark (+ results)

---

# **2B05 — Systems C I (Memory, Pointers & I/O)**

**Target:** 8 weeks · **Outcomes:** hex-tools; mmap viewer; mini-strings lib; PAD-2

### **Stack 1 — Pointers & Strings**

**Week 0–1**: ptr arithmetic/const/restrict; function pointers; bounds

* **PBR-2.1:** Mini-strings library + unit tests

### **Stack 2 — Structs, Contracts & Testing**

**Week 1–2**: structs/unions/bitfields; errno; specs & coverage

* **PAD-2 (part):** specs & cases

### **Stack 3 — Hexdump & Low-level I/O**

**Week 2–3**: stdio vs syscalls; buffers; readv/writev

* **PBR-2.2:** Custom **hexdump** (+ tests)

### **Stack 4 — mmap & Binary Viewing**

**Week 3–4**: mmap protections; section viewing; safe parsing

* **PBR-2.3:** Mini binary viewer (mmap) + evidence

### **Stack 5 — Dynamic Memory & Networking Intro**

**Week 4–7**: malloc/calloc/realloc/free; UAF/DF detection; TCP/UDP; non-blocking + timeouts

* **PBR-2.4:** Simple echo client (robust errors)
* **PAD-2 (final):** threats & mitigations

---

# **3B04 — x86\_64/ABI/ASM**

**Target:** 4 weeks · **Outcomes:** asm routines; syscall wrappers; C↔asm integration; PAD-3

### **Stack 1 — Calling Convention & Stack**

**Week 0**: SysV x86\_64; prologue/epilogue; nested calls

* **PBR-3.1:** `memset/memcmp` in asm + cross-tests

### **Stack 2 — Syscalls & Wrappers (no libc)**

**Week 1**: syscall numbers; errno; inline asm

* **PBR-3.2:** `write/getpid` wrappers + tests

### **Stack 3 — C↔asm Integration & Benchmarks**

**Week 2**: structs by value; ABI alignment; benchmark automation

* **PAD-3:** ABI notes + results

### **Stack 4 — SysV vs Win x64 & Cleanup**

**Week 3**: diffs; refactors; finalize PAD-3

---

# **4B04 — Linking, Loading & Formats (ELF, PLT/GOT, LD\_PRELOAD)**

**Target:** 4 weeks · **Outcomes:** ELF parser; LD\_PRELOAD hook; relocation PoC; PAD-4

### **Stack 1 — ELF Basics & Parser**

**Week 0**: headers; sections vs segments; relocations; symbols

* **PBR-4.1:** Minimal ELF parser (+ tests)

### **Stack 2 — Linking & PLT/GOT**

**Week 1**: static/dynamic; PIC/PIE; PLT/GOT; ldd diagnostics

* **PAD-4 (part):** linking architecture

### **Stack 3 — Shared Libs & LD\_PRELOAD**

**Week 2**: .so build/export; symbol visibility; hook `open/fopen`

* **PBR-4.2:** LD\_PRELOAD hook (stable, non-breaking)

### **Stack 4 — rpath/runpath & Validation**

**Week 3**: patchelf; before/after symbol diffs; stability checks

* **PBR-4.3:** Controlled manual relocation PoC
* **PAD-4 (final):** symbol table + evidence

---

# **EX0B01 — F1 Express Module (in parallel)**

**Target:** 1 effective week (interleaved) · **Outcome:** OPSEC checklist applied across F1

* Compartmentalization; artifact control; `strip`; build metadata (`SOURCE_DATE_EPOCH`)
* **Deliverable:** Signed OPSEC checklist applied to all F1 repos

