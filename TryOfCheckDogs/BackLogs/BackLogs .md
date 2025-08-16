
# Backlogs — Segment 1 (F1–F2 + F3-Start)

**Mini-challenge pack for the Bug Bounty period (v1.1)**

**Usage window:** 2026-09-21 → 2027-07-21
**Weekly budget:** 6–8 h/week (time-boxed)
**Scope:** content from **Phase 1**, **Phase 2**, and **Phase 3 (Start)**
**Format:** 15–60 min katas with acceptance criteria and minimal evidence (**PBR-lite + PAD-lite**)

## Ground rules

* **Effort key:** `S=15m`, `M=30m`, `L=45m`, `XL=60m`. If it doesn’t land, **log the blocker and move on**.
* **Minimum evidence (per challenge):** script/command or PoC, output/artifact, **1–3 screenshots**, **3–5 lines** of lessons learned.
* **Repository layout:** `backlogs/YY-WW/<challenge-id>/` with a short `README.md` and optional `Makefile`.
* **OPSEC/Legal:** **lab-only**, benign samples or self-built binaries. No third-party executables outside the lab; outbound DNS/HTTP only if explicitly allowed by lab policy (no scanning).

## Two-week cadence (template)

* **Week A (6–8 h):** pick **1 challenge** from each category → **CLI**, **Toolchain**, **C**, **ELF/PE**. Mix S/M/L to reach 6–8 h.
* **Week B (6–8 h):** pick **1 challenge** from each category → **Reversing/Unpack**, **Loaders**, **Internals/ROP**, **Free review**.
* **Weekly close-out:** one report `Wxx-summary.md` (≤200 words).

> Tip: Prefer breadth (4 areas/semana) y rota IDs a lo largo del periodo.

---

## Mini-challenge catalog

Each entry includes: **ID · Title · Effort · Prereq · Task · Acceptance · Deliverables**

### 1) Linux/CLI/Bash

* **B1-CLI-01** · Log pipeline with severity summary · **S**
  **Prereq:** grep/sed/awk · **Task:** from `samples/syslog.log`, produce `sev,count` CSV · **Acceptance:** `summary.csv` correct; `make run` reproducible · **Deliverables:** script, CSV, 1 screenshot.
* **B1-CLI-02** · Incremental copy with rotation · **M**
  **Prereq:** tar/rsync, dates · **Task:** backup `~/project` to `~/bk/` with 7-day rotation · **Acceptance:** 3 runs show only deltas · **Deliverables:** script, log, hash list.
* **B1-CLI-03** · Collaborative permissions with ACL · **M**
  **Prereq:** chmod/setfacl · **Task:** `team/` for lab group + read-only guests · **Acceptance:** tests with 3 users simulate rules · **Deliverables:** playbook, screenshots.
* **B1-CLI-04** · IOC list filter · **S**
  **Prereq:** — · **Task:** normalize IPs/domains/SHA256 into one TSV · **Acceptance:** TSV deduped & sorted · **Deliverables:** script + TSV.
* **B1-CLI-05** · Local DNS recon · **S**
  **Prereq:** dig/host + lab policy · **Task:** resolve 10 domains and map ASNs from `domains.txt` · **Acceptance:** `domain,ip,asn` CSV · **Deliverables:** script, CSV. *(Outbound DNS only; no scans.)*
* **B1-CLI-06** · Smart text-diff · **M**
  **Prereq:** diff/awk · **Task:** diff ignoring spaces/dates · **Acceptance:** report with 3 fixtures · **Deliverables:** script, fixtures, README.
* **B1-CLI-07** · Cron process watchdog · **M**
  **Prereq:** cron · **Task:** restart a process if it dies · **Acceptance:** works with dummy target · **Deliverables:** script, log.
* **B1-CLI-08** · Error-count one-liner · **S**
  **Prereq:** — · **Task:** count pattern occurrences across 3 files · **Acceptance:** stable, ordered output · **Deliverables:** command + output.

### 2) Toolchain / Debugging

* **B2-TOOL-01** · Minimal Makefile template · **S**
  **Prereq:** make · **Task:** targets `build/test/asan/clean` · **Acceptance:** `make asan` runs tests and **detects UB** in the fixture · **Deliverables:** Makefile + test.
* **B2-TOOL-02** · Leak hunt with ASan · **M**
  **Prereq:** gcc/clang + ASan · **Task:** fix leak in `leaky.c` · **Acceptance:** ASan clean · **Deliverables:** diff + log.
* **B2-TOOL-03** · strace vs ltrace · **M**
  **Prereq:** strace/ltrace · **Task:** compare syscalls vs libs for a binary · **Acceptance:** table + **5 observations** · **Deliverables:** outputs + summary.
* **B2-TOOL-04** · Post-mortem core dump · **M**
  **Prereq:** ulimit, gdb/lldb · **Task:** reproduce crash & backtrace · **Acceptance:** root cause identified · **Deliverables:** core, commands, notes.
* **B2-TOOL-05** · memcpy micro-benchmark · **S**
  **Prereq:** C toolchain · **Task:** measure 3 variants · **Acceptance:** simple chart + conclusions · **Deliverables:** code + PNG.

### 3) Systems C

* **B3-C-01** · Custom hexdump · **M**
  **Prereq:** stdio · **Task:** offsets + ASCII right column · **Acceptance:** matches known sample · **Deliverables:** binary, tests.
* **B3-C-02** · Mini-strings library · **M**
  **Prereq:** unit test harness · **Task:** `x_strlcpy/strnlen_s` + tests · **Acceptance:** coverage >80% · **Deliverables:** lib + tests.
* **B3-C-03** · Safe binary parser · **L**
  **Prereq:** file I/O · **Task:** read header with checks · **Acceptance:** rejects corrupted corpus · **Deliverables:** code + corpus.
* **B3-C-04** · `mmap` section viewer · **L**
  **Prereq:** POSIX I/O · **Task:** map file, list regions · **Acceptance:** works on 3 binaries · **Deliverables:** tool + screenshots.
* **B3-C-05** · Minimal TCP client · **M**
  **Prereq:** sockets · **Task:** connect/send with timeouts · **Acceptance:** echo server tests pass · **Deliverables:** code + log.
* **B3-C-06** · Parser fuzzing (honggfuzz/AFL) · **XL**
  **Prereq:** fuzz tool · **Task:** 20 min fuzz + fix any crash · **Acceptance:** crash-free end state · **Deliverables:** corpus + fix.
* **B3-C-07** · `errno` & contracts · **S**
  **Prereq:** — · **Task:** function with pre/post conditions · **Acceptance:** error-path tests pass · **Deliverables:** code + tests.

### 4) x86\_64 / ABI / asm

* **B4-ASM-01** · `memset` in asm · **M**
  **Prereq:** assembler + C harness · **Acceptance:** passes comparative suite · **Deliverables:** asm + bench.
* **B4-ASM-02** · Syscall wrapper · **M**
  **Prereq:** Linux x86\_64 · **Task:** `write/getpid` w/o libc · **Acceptance:** correct output + valid `errno` · **Deliverables:** code + README.
* **B4-ASM-03** · C↔asm structs · **M**
  **Prereq:** ABI basics · **Task:** pass struct by value · **Acceptance:** consistent on both sides · **Deliverables:** code + tests.

### 5) ELF / PE / Linking

* **B5-ELF-01** · Minimal ELF parser · **M**
  **Prereq:** objdump/readelf · **Acceptance:** lists sections & symbols · **Deliverables:** tool + test bins.
* **B5-ELF-02** · `LD_PRELOAD` hook · **L**
  **Prereq:** shared libs · **Task:** hook `open/fopen` · **Acceptance:** access log, no breakage · **Deliverables:** `.so` + demo.
* **B5-ELF-03** · PLT/GOT inspection · **M**
  **Prereq:** binutils · **Task:** show 3 function entries · **Acceptance:** evidence with objdump/readelf · **Deliverables:** script + screenshots.
* **B5-PE-04** · PE header dump · **M**
  **Prereq:** PE basics · **Task:** print DOS/NT/sections · **Acceptance:** matches PE-bear · **Deliverables:** tool + diff.
* **B5-PE-05** · TLS callback detect · **M**
  **Prereq:** PE parsing · **Task:** locate/print callbacks · **Acceptance:** demo on lab DLL · **Deliverables:** script + evidence.

### 6) Reversing / Unpack

* **B6-REV-01** · XOR-obfuscated strings · **S**
  **Prereq:** Python · **Task:** decoder + validation · **Acceptance:** complete, clean list · **Deliverables:** script + output.
* **B6-REV-02** · Manual UPX unpack · **L**
  **Prereq:** x64dbg/UPX · **Task:** dump + basic IAT repair · **Acceptance:** runs; opens in Ghidra w/o major errors · **Deliverables:** dump + guide.
* **B6-REV-03** · Breakpoint traps · **M**
  **Prereq:** x64dbg · **Task:** bypass `IsDebuggerPresent` & simple timing · **Acceptance:** stable session · **Deliverables:** notes + symbols.
* **B6-REV-04** · Initial CFG · **S**
  **Prereq:** Ghidra/Cutter · **Task:** extract CFG + flag critical funcs · **Acceptance:** 3 annotated findings · **Deliverables:** PNG + markdown.

### 7) Loaders / Userland execution

* **B7-LOD-01** · Local shellcode loader · **M**
  **Prereq:** Win API · **Acceptance:** benign execution + cleanup (**local process only**) · **Deliverables:** code + logs.
* **B7-LOD-02** · Basic manual map · **L**
  **Prereq:** PE/relocs · **Task:** minimal DLL export runs · **Acceptance:** evidence of execution (**self-map/local**) · **Deliverables:** code + screenshots.
* **B7-LOD-03** · Dual mode (CRT+LL / APC) · **L**
  **Prereq:** CreateRemoteThread/APC · **Task:** CLI selector + logs · **Acceptance:** both modes functional (lab) · **Deliverables:** binary + README.
* **B7-LOD-04** · Comparative traces · **M**
  **Prereq:** baseline checklist · **Task:** compare 2 techniques · **Acceptance:** artifact table + conclusions · **Deliverables:** report.

### 8) Internals / ROP (educational)

* **B8-ROP-01** · Basic gadget hunt · **M**
  **Prereq:** own binary + objdump · **Task:** list 10 gadgets · **Acceptance:** table w/ offsets + 1 working demo · **Deliverables:** script + notes.
* **B8-ROP-02** · Register-setter ROP · **L**
  **Prereq:** debugger + symbols · **Task:** chain sets key register · **Acceptance:** consistent state in debugger · **Deliverables:** PoC + screenshots.
* **B8-ROP-03** · DEP awareness · **M**
  **Prereq:** build flags · **Task:** document DEP impact + safe alternative · **Acceptance:** clear, reproducible comparison · **Deliverables:** short report.

---

## PAD-lite (template)

```
Challenge — <Title>
Objective
Key steps (bullets)
Evidence
  - out.txt / screenshots (1–3)
Lessons learned
  - 3–5 bullets
```

## Control metrics (weekly)

* Challenges completed (**target: 4/week**).
* Effective time (**target: 6–8 h/week**).
* Open/closed blockers.
* “Signal vs noise” in PoCs (when applicable).

## Cycle close-out (biweekly)

* `Wxx-summary.md` with: what worked, what didn’t, next 4 challenges, and **1 automation idea** for tooling.

## Final note

This pack **does not replace** TOCD progression. It keeps **hands/memory/judgment** sharp during the Bug Bounty window 
**without opening new fronts**. Tune difficulty based on fatigue and academic load.
