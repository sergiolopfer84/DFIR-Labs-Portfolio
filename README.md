# 🔍 DFIR Labs Portfolio – Sergio López Fernández

This repository documents structured Digital Forensics and Incident Response (DFIR) investigations performed as part of my cybersecurity specialization and hands-on technical development.

The focus is on **host-based forensic analysis, artifact reconstruction, and low-level filesystem investigation**, aligned with SOC Analyst and entry-level DFIR roles.

---

## 👤 About This Portfolio

Unlike theoretical summaries, these labs emphasize:

- Direct interaction with forensic images (E01, raw)
- NTFS internal structure analysis
- MFT-level inspection
- Artifact correlation (Registry, Prefetch, ShellBags, USB)
- Raw block examination
- Evidence handling in read-only environments

The objective is to demonstrate practical investigative capability rather than tool familiarity alone.

---

## 🎯 Professional Objective

Develop real-world technical capabilities aligned with:

- SOC Analyst Level 1
- Incident Response Analyst (Junior)
- Threat Detection & Host Investigation Roles

Core focus areas:

- Host-based forensic analysis
- Incident investigation methodology
- Artifact reconstruction
- Registry and metadata analysis
- Log correlation
- Evidence handling and reporting
- Filesystem-level investigation

---

## 🛠 Technical Stack

### Disk & Filesystem Analysis
- Sleuth Kit (mmls, fsstat, fls, istat, blkcat)
- FTK Imager
- Autopsy
- CAINE
- Guymager

### Windows Artifact Analysis
- RegRipper
- Eric Zimmerman Tools
- NirSoft Utilities
- Windows Event Viewer

### Memory & Volatile Data
- Belkasoft RAM Capturer
- RAMCapturer
- LiME

### Network & Log Analysis
- Wireshark
- Splunk

---

## 📂 Lab Structure

### 01 – Disk Forensics
- FAT16 Partition Analysis
- MBR Extraction & Hash Verification
- NTFS MFT Metadata Analysis
- Timeline Reconstruction
- PhotoRec File Carving

### 02 – Windows Artifact Analysis
- ShellBags Analysis
- USB Device Forensics
- Prefetch Investigation
- Browser Artifact Analysis

### 03 – Windows Registry Forensics
- Windows SAM Hive Analysis (Manual)
- Automated Multi-Hive Analysis with RegRipper

### 04 – NTFS Analysis with Sleuth Kit
- Partition Identification (mmls)
- Filesystem Structure Validation (fsstat)
- File Enumeration (fls)
- MFT Metadata Inspection (istat)
- Raw Block Extraction (blkcat)

---

## 🔬 Investigation Methodology

Each lab follows a structured forensic workflow:

1. Evidence integrity validation
2. Partition and filesystem identification
3. Artifact enumeration
4. Metadata inspection
5. Correlation and interpretation
6. SOC relevance analysis

---

## 📈 Career Roadmap Alignment

This portfolio supports progression toward:

- SOC Analyst L1
- Microsoft SC-200
- CompTIA Security+
- Advanced DFIR Specialization

The emphasis is on building practical investigation capability before certification stacking.

---

## ⚠️ Disclaimer

No sensitive or proprietary data is included.

All materials originate from controlled laboratory or simulated environments.
