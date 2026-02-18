# 🔍 DFIR Lab – NTFS Analysis with Sleuth Kit (CAINE)

## 🎯 Objective

Perform forensic analysis of a Windows 10 disk image (E01 format) using Sleuth Kit tools in CAINE Linux to:

- Identify partition structure
- Validate NTFS filesystem parameters
- Enumerate files and directories
- Inspect MFT metadata entries
- Extract raw data at block level
- Demonstrate proper forensic workflow in read-only mode

---

## 🧪 Evidence Details

- Image Name: `windows_001_10.E01`
- Format: E01 (EnCase evidence format)
- Filesystem: NTFS
- Analysis Environment: CAINE Linux
- Mount Mode: Read-only (victim disk and acquisition disk)

All analysis was performed in **read-only mode** to preserve evidence integrity.

---

## 🛠️ Tools Used

- `mmls`
- `fsstat`
- `fls`
- `istat`
- `blkcat`

---

# 1️⃣ Partition Identification – mmls

```bash
mmls windows_001_10.E01
```

### 🔎 Findings

- NTFS partition start sector: **2048**
- Partition length: **104853504 sectors**
- Sector size: **512 bytes**

### 📏 Partition Size Calculation

```
104853504 × 512 = 53.68 GB
```

✔ Confirmed valid NTFS partition structure.

---

# 2️⃣ Filesystem Structure Analysis – fsstat

```bash
fsstat windows_001_10.E01 -o 2048
```

### 🔎 Key Information Extracted

- Filesystem type: NTFS
- Cluster size identified
- MFT starting cluster located
- Root directory entry confirmed
- Total sector and cluster ranges validated

✔ Verified filesystem structure before deeper inspection.

---

# 3️⃣ File Enumeration – fls

```bash
fls windows_001_10.E01 -o 2048
```

### 🔎 Observed Structure

Detected key system components:

- `Windows`
- `Program Files`
- `Users`
- `pagefile.sys`
- `$MFT`
- `$Recycle.Bin`
- `System Volume Information`

✔ Confirmed full directory structure from forensic image.

---

# 4️⃣ MFT Entry Analysis – istat

```bash
istat windows_001_10.E01 -o 2048 52880
```

### 🔎 Metadata Reviewed

- `$STANDARD_INFORMATION` timestamps:
  - Created
  - Modified
  - MFT Modified
  - Accessed

- `$FILE_NAME` timestamps
- File flags (Hidden, System, Directory)
- Parent MFT reference
- Block allocation details

✔ Verified metadata integrity at NTFS internal level.

### 🧠 Forensic Relevance

Comparing `$STANDARD_INFORMATION` and `$FILE_NAME` timestamps is essential for detecting potential timestamp manipulation (timestomping).

---

# 5️⃣ Raw Block Inspection – blkcat

```bash
blkcat windows_001_10.E01 -o 2048 1713959
```

### 🔎 Result

- Extracted raw content directly from a logical NTFS block
- Bypassed logical file structure
- Verified actual stored content

✔ Demonstrated low-level disk inspection capability.

---

# 🔁 Forensic Workflow Summary

1. Identify partitions → `mmls`
2. Validate filesystem parameters → `fsstat`
3. Enumerate files → `fls`
4. Inspect metadata → `istat`
5. Extract raw data → `blkcat`

This structured approach ensures accurate and defensible forensic analysis.

---

# 🧠 Forensic Value

This lab demonstrates:

- Understanding of NTFS internal structures
- Ability to work at MFT level
- Direct interaction with disk image at block level
- Proper evidence handling methodology
- Linux-based forensic workflow proficiency

---

# 🔎 Investigation Perspective

Although this lab focuses on structural analysis, the same methodology can be applied to:

- Investigate suspicious files
- Detect timestamp manipulation
- Identify deleted file artifacts
- Validate file integrity
- Analyze partially overwritten data

---

# 📚 Lessons Learned

- NTFS metadata analysis is critical for detecting anomalies.
- Timestamps must be validated at multiple attribute levels.
- Raw block extraction allows validation beyond logical parsing.
- Partition offset identification is fundamental before any filesystem analysis.

---

# 🚀 Future Improvements

- Recover deleted files using `fls -d`
- Extract files with `icat`
- Analyze Alternate Data Streams (ADS)
- Inspect `$LogFile` and `$UsnJrnl`
- Perform full timeline reconstruction

---

# 🛡️ Conclusion

The Windows forensic image was successfully analyzed using Sleuth Kit in CAINE.

The workflow validated partition structure, inspected NTFS metadata, and demonstrated raw-level data extraction — core skills required for DFIR and SOC-level investigations.
