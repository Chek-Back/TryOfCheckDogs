
# Encrypted Practices — TOCD · Encrypted Mission Protocol (EMP)

> **Scope:** Training, **lab-only**.
> **Objective:** Deliver practice instructions **exclusively in encrypted form**, simulating the handling of sensitive tasking.

## What is the Encrypted Mission Protocol?

The **Encrypted Mission Protocol (EMP)** replaces plain-text handouts for:

* **PBR** — reproducible labs (challenge-style where applicable)
* **PAD** — analysis & documentation

All instructions ship **encrypted**. You must decrypt them inside your lab VM before reading or executing anything.

## Why (goals)

* **Realism:** mirrors workflows where sensitive directives are never sent in clear.
* **Discipline:** enforces a traceable, reproducible process for handling “intel”.
* **Skill-building:** practice safe data handling and GnuPG usage.

## Prerequisites

* A **dedicated lab VM** (e.g., Kali/Ubuntu) with `gnupg` installed.
* Either:

  * **Symmetric** mode: passphrase provided alongside the message; or
  * **Asymmetric** mode: your TOCD keypair imported into the VM.

> **Never** decrypt or store outputs outside the lab VM.

## Directory layout (suggested)

```
encrypted/
  EMP-YYYYWW-XX/
    mission.asc        # ASCII-armored GPG payload
    README.md          # your PAD summary after completion (never includes secrets)
    evidence/          # logs, screenshots, hashes (no private keys/passphrases)
.gitignore             # must exclude *.txt produced from decryption and secrets/
```

> Add a **pre-commit** guard to prevent committing decrypted artifacts (see below).

## Standard workflow

1. **Receive the mission**
   You’ll get an **ASCII-armored** GPG block:

   ```
   -----BEGIN PGP MESSAGE-----
   ...
   -----END PGP MESSAGE-----
   ```

2. **Create the file in the VM**

   ```bash
   nano mission.asc
   # paste the armored block, save
   ```

3. **Decrypt inside the VM**

   * **Symmetric** (passphrase prompt):

     ```bash
     gpg --decrypt mission.asc > mission.txt
     ```

   * **Asymmetric** (after importing the provided public/private keys):

     ```bash
     gpg --import tocd.pub  # once, if needed
     gpg --decrypt --output mission.txt mission.asc
     ```

4. **Read & execute**
   Open `mission.txt`, follow steps, and **document evidence** as you go.

5. **Document (PAD)**
   Write a short PAD (what/why/how, results, issues, mitigations) and store evidence (logs, screenshots, hashsets) under `evidence/`.

## Example (expected decrypted content)

```
Mission: Scan the lab subnet and document active hosts.
Tools: nmap, netdiscover.
Objective: Identify potential attack surfaces.
Deliverables: scan logs, host inventory CSV, short PAD (≤200 words).
```

## Validation & traceability

* Record environment info and hashes:

  ```bash
  date -Iseconds | tee evidence/start_time.txt
  uname -a        | tee evidence/uname.txt
  sha256sum mission.asc > evidence/mission.asc.sha256
  ```

* Keep command logs:

  ```bash
  script -q -c "bash -l" evidence/session.typescript
  # exit to stop recording
  ```

* Close with checksums of outputs and a brief PAD.

## OPSEC / Legal

* **Lab-only**; **benign** targets/datasets.
* No decrypted content leaves the VM.
* Never commit secrets, private keys, or passphrases.
* Follow your program’s **consent** and **acceptable-use** rules.

## Pre-commit guard (optional but recommended)

`.git/hooks/pre-commit` (make executable):

```bash
#!/usr/bin/env bash
# Block accidental commits of decrypted mission files or secrets
if git diff --cached --name-only | grep -E '\.(txt|log)$' | grep -qi 'mission'; then
  echo "Blocked: decrypted mission artifacts detected. Commit evidence to evidence/ only."
  exit 1
fi
if git diff --cached --name-only | grep -qiE 'secrets|private|\.key$'; then
  echo "Blocked: secret material detected."
  exit 1
fi
```

## Troubleshooting

* **`gpg: decryption failed: No secret key`**
  You tried asymmetric decryption without importing the key; either import the key or confirm the mission uses **symmetric** mode.

* **`gpg: no valid OpenPGP data found`**
  Ensure the armored block is intact (no missing header/footer, no wrapped lines cut).

* **Passphrase issues**
  Verify keyboard layout and whitespace. Passphrases are **case-sensitive**.

---

### Summary

* Missions arrive **encrypted** (`*.asc`), never in clear.
* Decrypt **inside** your lab VM, execute, and document.
* Keep a **clean audit trail** (hashes, logs, PAD).
* Protect secrets; commit **evidence and PAD only**, not decrypted instructions.
