# Encrypted Practices – Try Of Check Dogs (TOCD)

This directory is part of the **Try Of Check Dogs (TOCD)** training plan and contains all **encrypted practices** created under the **Encrypted Mission Protocol**.

Each file in this directory represents a realistic simulation of receiving sensitive intelligence, where you must **decrypt and execute the mission** by following the established procedure.

> **Note:** The content is never provided in plain text. You must use `gpg` and follow the decryption steps to access the practice instructions.

---

## What is the Encrypted Mission Protocol?

**Light Practice Format – Sensitive Intelligence Simulation**

The **Encrypted Mission Protocol** replaces the traditional delivery of instructions in plain text for:

- **PBR** – Proof-of-Bounty-Readiness (Challenge-Based Practices)
- **PAD** – Attack and Defense Practices

Instead, all instructions are provided in **encrypted format** and require the proper decryption process to be read and executed.

---

## Objective

To replicate the workflow of a real offensive cybersecurity environment, where critical orders and information **are never directly exposed**.

This protocol aims to strengthen skills in:

- Secure handling of sensitive data.
- Use of **GnuPG** (`gpg`) for encryption and decryption.
- Maintaining a secure and traceable workflow in a hacking lab environment.

---

## Operational Procedure

1. **Receiving the Mission**
    - You will receive an encrypted data block in GPG (ASCII-armored) format.
    - Example:
      ```
      -----BEGIN PGP MESSAGE-----
      
      hQGMA2kQkYX3h13wAQv+NgkzRvP6o1X8Mox+L6FZxkG41jk4zPUyDl7ff1uZ3TrB
      ...
      =0a1B
      -----END PGP MESSAGE-----
      ```

2. **Creating the File in the VM**
    - Save the message into a file inside your Kali Linux virtual machine:
      ```bash
      nano mission.gpg
      ```
    - Paste the encrypted block into the file and save.

3. **Decrypting the Mission**
    - Run:
      ```bash
      gpg --decrypt mission.gpg
      ```
    - If prompted, enter the password provided with the encrypted block.

4. **Reading and Executing**
    - Once decrypted, you will receive the complete practice instructions.
    - Execute the mission following the given steps and document the results.

---

## Example Usage

```bash
# Save the mission
nano mission.gpg

# Decrypt
gpg --decrypt mission.gpg
````

**Expected output:**

```
Mission: Scan the internal network and document active hosts.
Tools: nmap, netdiscover.
Objective: Identify possible attack vectors.
```

---

## Benefits of the Protocol

- **Security:** Prevents accidental exposure of instructions through insecure channels.
    
- **Realism:** Simulates the management of sensitive data in real-world cybersecurity operations.
    
- **Operational Discipline:** Encourages secure and traceable handling of confidential information.
