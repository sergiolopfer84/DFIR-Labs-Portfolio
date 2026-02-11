# 🧪 Lab: NTFS $MFT Metadata Analysis with MFTECmd

## 🧾 Scenario

An NTFS $MFT artifact was extracted from a Windows volume as part of a simulated forensic exercise.  
The goal was to analyze filesystem metadata in order to identify active, deleted and modified files, and reconstruct timeline activity.

No additional artifacts (USN or $LogFile) were used in this lab. The analysis focused solely on $MFT metadata.

---

## 🎯 Objective

- Parse the $MFT artifact using MFTECmd
- Generate structured CSV output
- Identify deleted files (InUse = false)
- Analyze timestamps (Created0x10, Modified, Accessed)
- Perform basic timeline filtering using Timeline Explorer

---

## 🛠 Tools Used

- MFTECmd v1.3.0.0 (Eric Zimmerman)
- Timeline Explorer
- Windows NTFS test dataset

---

## 🔄 Investigation Workflow

### 1️⃣ Process $MFT with MFTECmd

The extracted $MFT artifact was parsed using:


.\MFTECmd.exe -f "..$MFT.copy0" --csv .\ --csvf mft_analysis.csv


This generated a structured CSV file containing NTFS metadata records.

---

### 2️⃣ Load CSV into Timeline Explorer

The generated CSV was opened in Timeline Explorer to:

- Sort by Created0x10 timestamp
- Filter deleted files (InUse == false)
- Identify recently modified files
- Search by extension (.exe, .zip, .jpg, etc.)
- Inspect suspicious paths (e.g., \$RECYCLE.BIN, System Volume Information)

---

## 📊 Key Observations

- Deleted entries were successfully identified using `InUse == false`
- Full file paths were available through MFT records
- Multiple timestamp attributes (0x10 and 0x30) allowed temporal comparison
- Metadata persists even after file deletion

No clearly malicious files were identified during this controlled exercise.

---

## ⚖️ Forensic Considerations

- $MFT provides metadata but not full transaction detail
- Timestamp manipulation (timestomping) may affect reliability
- Cross-artifact correlation (USN, $LogFile) strengthens conclusions
- Deleted file records remain recoverable until overwritten

---

## 🔐 SOC & Incident Response Relevance

$MFT analysis is valuable in scenarios involving:

- Deleted file investigations
- Malware dropper identification
- Suspicious file creation before incidents
- Evidence of file manipulation
- Insider activity reconstruction

Even without additional artifacts, $MFT provides foundational timeline visibility.

---

## 🧩 Lessons Learned

- Metadata analysis is often the first step in NTFS investigations.
- Filtering by InUse and timestamps quickly reduces investigative scope.
- Cross-validation with other artifacts is essential for higher confidence.
- Understanding NTFS internal structures improves investigative accuracy.

---

## 📎 Supporting Documentation

`MFT-Artifact-Analysis.pdf`
