# 🧪 Lab: FAT16 Partition Analysis (Offset 63 & OEM Name Identification)

## 🧾 Scenario

A raw disk image (`.dd`) was provided for forensic examination.  
The objective was to identify the starting offset of a FAT16 partition and extract filesystem metadata using forensic tools.

The partition was located at sector offset 63.

---

## 🎯 Objective

- Identify FAT16 partition starting offset
- Analyze filesystem metadata using `fsstat`
- Locate and interpret the **OEM Name**
- Understand the forensic difference between OEM Name and Volume Label

---

## 🧠 Technical Background

In legacy disk layouts (MBR-based), partitions often begin at sector **63**.

To analyze a filesystem within a disk image, the correct byte offset must be calculated:



Offset = Sector × Bytes per sector


For sector 63 with 512-byte sectors:



63 × 512 = 32256 bytes


This offset allows forensic tools to access the filesystem directly.

---

## 🛠 Tools Used

- `mmls` (The Sleuth Kit)
- `fsstat`
- CAINE Linux

---

## 🔄 Investigation Workflow

### 1️⃣ Identify Partition Layout



mmls hhdd.dd


The FAT16 partition was identified starting at sector 63.

---

### 2️⃣ Calculate Byte Offset



63 × 512 = 32256


---

### 3️⃣ Analyze Filesystem with fsstat



fsstat -o 63 hhdd.dd


This command parses the FAT16 filesystem metadata.

---

## 📊 Key Findings

- FAT16 filesystem confirmed
- Partition located at sector 63
- OEM Name identified in fsstat output
- OEM Name corresponds to the formatting system/tool
- Volume Label is distinct from OEM Name

---

## ⚖️ Forensic Considerations

- OEM Name provides contextual information but does not prove attribution
- Correct offset calculation is critical to avoid misinterpreting data
- Misalignment results in invalid or corrupted filesystem analysis

---

## 🔐 SOC & Incident Response Relevance

This type of analysis is useful when:

- Investigating removable media
- Analyzing legacy storage devices
- Determining how a volume was formatted
- Validating partition integrity

Correct offset handling is fundamental in disk forensics and prevents analytical errors.

---

## 🧩 Lessons Learned

- Accurate partition offset calculation is essential in disk analysis.
- `fsstat` provides valuable low-level filesystem metadata.
- OEM Name and Volume Label serve different forensic purposes.
- Understanding disk structure reduces the risk of misinterpretation.

---
