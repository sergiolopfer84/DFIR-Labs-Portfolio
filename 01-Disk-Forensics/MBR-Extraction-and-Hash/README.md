# 🧪 Lab: MBR Extraction and SHA1 Verification

## 🧾 Scenario

A raw disk image (`.dd`) was provided for forensic analysis.  
The objective was to extract the Master Boot Record (MBR) and calculate its SHA1 hash to ensure integrity and enable further examination.

---

## 🎯 Objective

- Extract the first 512 bytes (MBR) from the disk image
- Save the MBR as a binary file
- Calculate its SHA1 hash

---

## 🧠 Technical Background

The Master Boot Record (MBR):

- Occupies the first 512 bytes of a disk
- Contains boot code and partition table
- Exists outside any filesystem
- Is critical for boot integrity and forensic validation

Because it is raw binary data, it is typically saved as `.bin`.

---

## 🛠 Tools Used

- `dd`
- `sha1sum`
- PowerShell (`Get-FileHash`)

---

## 🔄 Investigation Workflow

### 1️⃣ Extract MBR (Linux)

dd if=hhdd.dd of=mbr.bin bs=512 count=1


- `bs=512` → sector size  
- `count=1` → copy first sector only  

### 2️⃣ Calculate SHA1 Hash (Linux)

sha1sum mbr.bin


### 3️⃣ Alternative (PowerShell)

Get-FileHash mbr.bin -Algorithm SHA1


---

## 📊 Results

- MBR successfully extracted
- SHA1 hash calculated for integrity verification
- File preserved as raw binary (`.bin`)

---

## ⚖️ Forensic Considerations

- Hash verification ensures evidence integrity
- MBR may contain malicious boot modifications
- Extraction must not modify original image

---

## 🔐 SOC & Incident Response Relevance

MBR analysis is useful in cases involving:

- Bootkits
- Rootkits
- Suspicious disk tampering
- Partition manipulation

---

## 🧩 Lessons Learned

- The MBR exists outside the filesystem.
- Hashing extracted artifacts preserves evidentiary integrity.
- Low-level disk analysis strengthens forensic investigations.

---

## 📎 Supporting Documentation

`MBR-Extraction-Practice.pdf`
