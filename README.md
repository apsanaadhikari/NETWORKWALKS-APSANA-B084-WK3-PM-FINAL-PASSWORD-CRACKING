<div align="center">

# 🔓 Week 3: Password Cracking

**Testing how strong passwords really are, using offline and web-based cracking tools**

![Batch](https://img.shields.io/badge/Batch-B084-blue) ![Week](https://img.shields.io/badge/Week-03-orange) ![Phase](https://img.shields.io/badge/Phase-Password%20Attacks-success) ![Use](https://img.shields.io/badge/Use-Education%20Only-red)

**Apsana Adhikari** | Networkwalks Cybersecurity Internship

</div>

---

## 📌 Overview

Password cracking recovers a password from a protected file or stored hash. Security professionals use it to test how strong a password really is — if it's short or common, it's found in seconds, which is exactly the proof needed to push for stronger passwords.

This week I cracked the same weak password two different ways on two sample locked PDF files supplied for the lab.

## 🎯 Modules Completed

| Module | Task | Status |
|--------|------|--------|
| W3-PM1 | Password cracking with John the Ripper (CLI) + Johnny (GUI) | ✅ Done |
| W3-PM2 | Password cracking with Networkwalks' web tools | ✅ Done |

## 🧰 Tools Used

| Tool | What it does |
|------|--------------|
| 🐧 Kali Linux | OS used to run John the Ripper and Johnny |
| 🔑 `pdf2john` | Extracts a crackable hash from a locked PDF |
| ⚔️ John the Ripper | Command-line password cracking tool |
| 🖱️ Johnny | Graphical front-end for John the Ripper |
| 🌐 Networkwalks Hash Calculator | Browser tool — extracts a PDF's hash |
| 🌐 Networkwalks Password Cracker | Browser tool — cracks a submitted hash |

## 🧗 Part 1: John the Ripper + Johnny

**Hit a snag first:** the Windows build of John the Ripper failed with a missing `cygbz2-1.dll` error. Rather than keep fighting a broken install, I switched to Kali Linux, where JTR comes pre-installed — and that's an officially supported option in the lab guide.

**Steps:**
1. Extracted the hash: `pdf2john locked.pdf > hash.txt`
2. Cracked it: `john hash.txt` → password found in under a second
3. Confirmed with: `john --show hash.txt` → `1 password hash cracked, 0 left`
4. Verified the same result in **Johnny**, the GUI version

| pdf2john + hash | John cracks it | Johnny GUI confirms it |
|---|---|---|
| ![pdf2john](SS/pm1-1-pdf2john-hash.png) | ![john](SS/pm1-2-john-cracked.png) | ![johnny](SS/pm1-4-johnny-gui.png) |

## 🌐 Part 2: Networkwalks Web Tools

No installation needed — both tools run entirely in the browser.

1. Uploaded the locked PDF to the **Hash Calculator** → got a `$pdf$...` hash
2. Pasted it into the **Password Cracker** → match found
3. Opened the PDF with the recovered password → lab flag captured 🎉

| Hash extracted | Password cracked |
|---|---|
| ![hash calc](SS/pm2-1-hash-extracted.png) | ![cracked](SS/pm2-2-password-cracked.png) |

## 🔐 Result

Both methods — a dedicated offline tool and a free web tool — cracked the **same weak password in under a second**, using nothing more than a default wordlist.

## ⚠️ Why This Matters

| Finding | Risk |
|---------|------|
| Dictionary-style password used | 🔴 Critical |
| No rate-limiting possible on offline files | 🟠 Medium |
| Web tools lower the skill barrier to attack | 🟠 Medium |

A short, common password gives almost no protection — against a serious tool *or* a free website.

## ✅ Recommendations

- Use long (12+ character), random passwords — never dictionary words
- Avoid predictable patterns (`password1`, `123456`, name + year)
- Use a password manager for unique passwords everywhere
- Use strong encryption settings when password-protecting files
- Enable multi-factor authentication wherever it's offered
- Test your own passwords periodically — before someone else does

## 📂 Repository Contents

```
├── README.md
├── W3-PM-FINAL-Password-Cracking-Report-Apsana-Adhikari.pdf
└── SS/                     Screenshots: hash extraction, cracking, GUI, flags
```

## 💡 What I Learned

- How a password hash is extracted from a locked file and then attacked offline
- The difference between a CLI tool (John) and its GUI front-end (Johnny)
- When a downloaded tool breaks (missing DLL), switching to a known-good environment like Kali can be faster than debugging it
- Why password strength — not the cracking tool — is what actually protects a file

## 🛡️ Ethical Use

> This project is for education only. All cracking was performed on sample files supplied specifically for this lab exercise. Never attempt to crack a password you do not own or have explicit written permission to test.

---

<div align="center">

Built as part of the **Networkwalks Cybersecurity Internship** | Week 03 | Batch B084

</div>
