# 🧪 Lab: File Recovery using PhotoRec (Data Carving)

## 🧾 Scenario

A forensic disk image in E01 format was provided as part of a simulated investigation involving potential deletion of user data.  
The objective was to determine whether deleted artifacts could be recovered from unallocated space.

---

## 🎯 Objective

Recover deleted files from the forensic image using signature-based carving techniques without relying on file system metadata (MFT).

---

## 🧠 Technical Background

Data carving is a forensic technique that extracts files directly from raw disk sectors by identifying file signatures (headers and footers), independently of file system structures.

This method is particularly useful when:

- File system metadata has been deleted or overwritten
- The disk has been partially corrupted
- Evidence destruction is suspected
- Only unallocated space remains accessible

---

## 🛠 Tools Used

- CAINE Linux
- ewfmount
- losetup
- PhotoRec

---

## 🔄 Investigation Workflow

### 1️⃣ Mount E01 Image

The forensic image was mounted using:

```
ewfmount image.E01 imagenEWFRaw/
```

This converts the E01 container into a RAW-accessible file.

---

### 2️⃣ Associate RAW Image with Loop Device


```
losetup -fP imagenEWFRaw/ewf1
```

This step allowed the system to treat the image as a physical disk (`/dev/loopX`) and access its partitions directly.

---

### 3️⃣ Execute Carving with PhotoRec

PhotoRec was executed against the target partition.

Two analysis modes were evaluated:

- **Free** → Scan unallocated space only  
- **Whole** → Scan entire partition  

Given the investigation goal (recover deleted artifacts only), the **Free** option was selected to reduce noise and focus exclusively on unallocated space.

---

## 📊 Results

- 214 files recovered
- Majority of recovered artifacts were PNG image files
- Deleted content successfully reconstructed from unallocated space
- No executable binaries or clearly malicious files identified during initial review

Recovered files were exported to a controlled recovery directory.

---

### 🔎 Evidence – Free Space Analysis

![Free Option](images/photorec-free-option.png)

### 📊 Recovery Results

![Recovery Results](images/photorec-recovery-results.png)

### 📁 Recovered Files

![Recovered Files](images/photorec-recovered-files.png)

---

## ⚖️ Forensic Considerations

- Carved files lose original filenames, directory paths, and metadata
- Fragmentation may result in partially corrupted files
- Carving alone does not provide contextual attribution
- Recovered artifacts should be hash-validated to ensure evidentiary integrity

---

## 🔐 Incident Response & SOC Relevance

In real-world incident response scenarios, carving is particularly useful when:

- An attacker attempts to delete evidence to evade detection
- Logs or sensitive files are intentionally removed
- File system metadata is damaged or wiped
- Insider activity involves data destruction

Carving provides a recovery mechanism when traditional file system-based analysis fails.

---

## 🧩 Lessons Learned

- Signature-based carving remains effective even without file system metadata.
- Selecting the appropriate scan scope (Free vs Whole) significantly impacts forensic efficiency.
- Recovery does not equal attribution; contextual correlation is still required.
- Low-level disk knowledge is essential when investigating anti-forensic behavior.

---

## 📎 Supporting Documentation

`PhotoRec-Carving-Documentation.pdf`
