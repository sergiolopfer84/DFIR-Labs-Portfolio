# 🧪 Lab: ShellBags Registry Artifact Analysis

## 🧾 Scenario

During forensic analysis of a Windows user profile, registry hives were examined to determine whether folder access activity could be reconstructed — even in cases where folders were deleted or external devices were no longer connected.

The analysis focused on the ShellBags artifact stored in:

- NTUSER.DAT
- USRCLASS.DAT

---

## 🎯 Objective

- Identify folder paths accessed by the user.
- Detect interaction with removable media or network locations.
- Evaluate persistence of folder access artifacts after deletion.

---

## 🧠 Technical Background

ShellBags are Windows registry structures that store information about folders opened in Windows Explorer.

They contain:

- Folder paths (including USB and network paths)
- View preferences (icons, list, details)
- Registry Last Write timestamps
- Internal Bag IDs

### 📍 Registry Locations

NTUSER.DAT\Software\Microsoft\Windows\Shell\BagMRU
NTUSER.DAT\Software\Microsoft\Windows\Shell\Bags
USRCLASS.DAT\Local Settings\Software\Microsoft\Windows\Shell\BagMRU


ShellBags persist even if:

- The folder has been deleted
- The USB device is no longer connected
- The user attempts to remove evidence

---

## 🛠 Tool Used

- ShellBagsView (NirSoft)

---

## 🔄 Investigation Workflow

### 1️⃣ Hive Acquisition

External registry hives were loaded using:

- NTUSER.DAT
- USRCLASS.DAT

The **External Registry Files** option was selected to avoid altering the original system.

---

### 2️⃣ Hive Integrity Verification

Hives were verified to ensure they were in a **clean state** and not marked as dirty (pending transactions).

---

### 3️⃣ Artifact Review

The following fields were analyzed:

- Folder Path
- Last Write Time
- User SID
- Bag ID
- File System Type

Special attention was given to:

- Removable drive paths
- Network shares
- Unusual directory structures

---

## 📊 Key Findings

- Folder access history persisted despite deletion.
- Removable media paths were recoverable.
- Explorer navigation activity could be reconstructed.
- Registry timestamps provided temporal context.

---

## ⚖️ Forensic Considerations

- ShellBags confirm folder access, not file execution.
- IDs may be reused over time.
- Should be correlated with:
  - $MFT
  - $UsnJrnl
  - USB artifacts
  - Event Logs

---

## 🔐 SOC & Incident Response Relevance

ShellBags analysis is particularly useful in:

- Insider threat investigations
- Data exfiltration cases
- Access to hidden or deleted directories
- User activity reconstruction
- Post-incident timeline validation

---

## 🧩 Lessons Learned

- Registry artifacts may outlive file system evidence.
- External hive analysis is safer for forensic integrity.
- ShellBags provide strong contextual insight into user behavior.
- Correlation with additional artifacts increases evidentiary value.
