# 🔍 DFIR Labs Portfolio – Sergio López Fernández

This repository documents structured Digital Forensics and Incident Response (DFIR) investigations performed as part of my cybersecurity specialization and hands-on technical development.

The focus is on **host-based forensics, memory analysis, and network traffic investigation**, aligned with SOC Analyst and entry-level DFIR roles.

---

## 👤 About This Portfolio

Unlike theoretical summaries, these labs emphasize:

- Direct forensic image analysis (E01, raw)
- NTFS internal structure inspection
- MFT-level investigation
- Windows artifact reconstruction
- Browser activity reconstruction
- PCAP traffic analysis
- MAC and network attribution
- Evidence handling in read-only environments
- Structured investigative reporting

The objective is to demonstrate practical investigative capability rather than tool familiarity alone.

---

## 🎯 Professional Objective

Develop real-world technical capabilities aligned with:

- SOC Analyst Level 1
- Incident Response Analyst (Junior)
- Threat Detection & Host Investigation Roles

Core focus areas:

- Endpoint forensic analysis
- Incident investigation methodology
- Artifact reconstruction
- Registry and metadata analysis
- Network traffic analysis
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
- Volatility 3
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
- Browser Artifact Reconstruction

### 03 – Windows Registry Forensics
- Windows SAM Hive Analysis (Manual)
- Automated Multi-Hive Analysis with RegRipper

### 04 – NTFS Deep Analysis (Sleuth Kit)
- Partition Identification (mmls)
- Filesystem Structure Validation (fsstat)
- File Enumeration (fls)
- MFT Metadata Inspection (istat)
- Raw Block Extraction (blkcat)

### 05 – Web Activity Reconstruction
- Chrome History Analysis
- Multi-browser Artifact Correlation
- Timeline Reconstruction

### 06 – Network Traffic Investigation
- HTTP Session Analysis
- Domain Identification via Host Header
- Internal/External IP Attribution
- MAC Vendor Identification
- PCAP Investigation Workflow

---

## 🔬 Investigation Methodology

Each lab follows a structured forensic workflow:

1. Evidence integrity validation
2. Artifact identification
3. Technical extraction
4. Correlation across layers
5. Analytical interpretation
6. Suspicious activity assessment
7. Structured reporting

---

## 📈 Career Roadmap Alignment

This portfolio supports progression toward:

- SOC Analyst L1 roles
- Microsoft SC-200
- CompTIA Security+
- Advanced DFIR specialization

The emphasis is on building practical investigative capability before certification stacking.

---

## ⚠️ Disclaimer

No sensitive or proprietary data is included.

All materials originate from controlled laboratory or simulated environments
