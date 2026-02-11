# 🧪 Lab: NTFS Artifact Timeline Reconstruction ($MFT, $LogFile, $UsnJrnl)

## 🧾 Scenario

A Windows NTFS volume was analyzed as part of a simulated forensic investigation.  
A test file was created, renamed, modified and later deleted in order to evaluate whether NTFS internal artifacts could reconstruct the complete activity timeline.

The objective was to determine how NTFS system files record file system operations at a transactional and journal level.

---

## 🎯 Objective

Reconstruct the full lifecycle of a file using NTFS artifacts:

- $MFT
- $LogFile
- $UsnJrnl:$J

Correlate events to build a reliable forensic timeline.

---

## 🧠 Technical Background

NTFS maintains several internal artifacts that track file system activity:

- **$MFT (Master File Table)** → Core metadata for every file and directory.
- **$LogFile** → Transaction log recording low-level NTFS operations.
- **$UsnJrnl ($J)** → Change journal that logs file creation, modification, rename and deletion events.

Unlike traditional event logs, these artifacts operate at the file system level and may retain activity even after files are deleted.

---

## 🛠 Tools Used

- FTK Imager (artifact extraction)
- NTFS Log Tracker (timeline reconstruction)
- Windows NTFS test environment

---

## 🔄 Investigation Workflow

### 1️⃣ Create Test Artifact

A text file was created and renamed to simulate normal user activity.

### 2️⃣ Extract NTFS Artifacts

Using FTK Imager, the following files were exported:

- `$MFT`
- `$LogFile`
- `$Extend\$UsnJrnl:$J`

These artifacts were preserved for offline analysis.

### 3️⃣ Load Artifacts into NTFS Log Tracker

The extracted artifacts were loaded into NTFS Log Tracker and parsed to reconstruct file activity.

---

## 📊 Timeline Reconstruction

The following sequence was identified:

- **19:58:16** → File created as *Nuevo Documento de texto.txt*
- Immediate rename to *Video$Logfile.txt*
- MFT timestamp updates recorded
- Object ID assigned
- File content written (resident → later non-resident data growth)
- Creation of Recent shortcut artifacts (.lnk)
- **20:21:28** → File closed and later deleted

The $LogFile recorded transactional operations including rename, metadata update, data write and deletion.  
The $UsnJrnl confirmed the chronological sequence of events.

---

## 🔎 Key Findings

- Full file lifecycle reconstructed despite later deletion
- Transaction-level visibility available through $LogFile
- USN Journal provides high-level chronological activity
- Correlation between artifacts increases evidentiary reliability

---

## ⚖️ Forensic Considerations

- $LogFile captures transactional data not visible in standard logs
- USN Journal entries may persist even after file removal
- Timeline reconstruction requires cross-artifact validation
- File tunneling behavior may affect interpretation

---

## 🔐 SOC & Incident Response Relevance

This type of analysis is critical when:

- A suspect attempts to delete or manipulate files
- Malware creates, renames or deletes payloads
- Insider threats attempt data concealment
- Log tampering is suspected

NTFS artifact correlation allows investigators to reconstruct actions even when traditional logs are unavailable or wiped.

---

## 🧩 Lessons Learned

- NTFS artifacts provide deeper visibility than standard Windows Event Logs.
- Correlation between $MFT, $LogFile and $UsnJrnl strengthens forensic conclusions.
- Transaction logs reveal operations that may not be obvious at file level.
- Timeline reconstruction is fundamental for incident response investigations.

---

## 📎 Supporting Documentation

Original lab documentation available in:

`NTFS-Artifact-Analysis.pdf`
