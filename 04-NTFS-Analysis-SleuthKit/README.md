# 🔍 DFIR Lab – NTFS Analysis with Sleuth Kit (CAINE)

## 🎯 Objective

Perform forensic analysis of a Windows 10 disk image (E01 format) using Sleuth Kit in CAINE Linux to:

- Identify partition structure
- Validate NTFS filesystem parameters
- Enumerate system files
- Extract raw data at block level
- Demonstrate structured forensic workflow in read-only mode

---

## 🧪 Evidence Details

- Image: `windows_001_10.E01`
- Format: E01 (EnCase evidence format)
- Filesystem: NTFS
- Analysis Environment: CAINE Linux
- Mount Mode: Read-only (evidence integrity preserved)

Both victim disk and acquisition disk were mounted in **read-only mode** to ensure forensic soundness.

---

# 1️⃣ Partition Identification – mmls

```bash
mmls windows_001_10.E01
```

## 🔎 Output

![mmls output](screenshots/01_mmls.png)

### 🧠 Interpretation

- NTFS partition start sector: **2048**
- Partition length: **104853504 sectors**
- Sector size: **512 bytes**

### 📏 Partition Size Calculation

```
104853504 × 512 = 53.68 GB
```

✔ A valid NTFS partition was identified and its offset determined for further analysis.

---

# 2️⃣ Filesystem Structure Analysis – fsstat

```bash
fsstat windows_001_10.E01 -o 2048
```

## 🔎 Output

![fsstat output](screenshots/02_fsstat.png)

### 🧠 Key Information Extracted

- Filesystem type: NTFS
- Cluster size identified
- MFT starting location detected
- Root directory entry confirmed
- Total sector and cluster ranges validated

✔ The filesystem structure was verified before proceeding with deeper inspection.

---

# 3️⃣ File Enumeration – fls

```bash
fls windows_001_10.E01 -o 2048
```

## 🔎 Output

![fls output](screenshots/03_fls.png)

### 🧠 Observed System Structure

Key system components detected:

- `Windows`
- `Program Files`
- `Users`
- `pagefile.sys`
- `$MFT`
- `$Recycle.Bin`
- `System Volume Information`

✔ The directory hierarchy was successfully reconstructed directly from the forensic image.

---

# 4️⃣ Raw Block Extraction – blkcat

```bash
blkcat windows_001_10.E01 -o 2048 <block_number>
```

## 🔎 Output

![blkcat output](screenshots/04_blkcat.png)

### 🧠 Analysis

- Extracted raw content directly from a logical NTFS block
- Bypassed logical file parsing
- Verified actual stored data at disk level

✔ Demonstrated low-level forensic capability by inspecting raw block data.

---

# 🔁 Forensic Workflow Summary

1. Identify partition structure → `mmls`
2. Validate filesystem parameters → `fsstat`
3. Enumerate files and directories → `fls`
4. Extract raw content at block level → `blkcat`

This structured methodology ensures defensible forensic analysis.

---

# 🧠 Forensic Value

This lab demonstrates:

- Understanding of NTFS partitioning
- Offset-based filesystem analysis
- Direct disk image interaction
- Low-level block inspection
- Proper evidence handling practices

These are fundamental skills required in DFIR and SOC investigations.

---

# 🚀 Potential Extensions

Future improvements could include:

- Deleted file recovery (`fls -d`)
- File extraction using `icat`
- MFT metadata inspection using `istat`
- Analysis of Alternate Data Streams (ADS)
- Investigation of `$LogFile` and `$UsnJrnl`
- Full timeline reconstruction

---

# 🛡️ Conclusion

The Windows forensic image was successfully analyzed using Sleuth Kit in CAINE.

The investigation validated partition structure, confirmed NTFS parameters, reconstructed directory hierarchy, and demonstrated raw block inspection — core competencies in digital forensic investigations.
