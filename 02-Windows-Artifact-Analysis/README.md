# 🖥️ Windows Artifact Analysis Labs

This section contains forensic labs focused on Windows-specific artifacts used for user activity reconstruction, device tracking, and incident response investigations.

Unlike low-level disk forensics, these labs analyze operating system artifacts that persist beyond file deletion and provide contextual evidence of system usage.

---

## 🎯 Focus Areas

- Registry-based artifacts
- User activity reconstruction
- Removable media tracking
- Timeline correlation
- Incident response support

---

## 📚 Labs Included

| Lab | Artifact Type | Investigation Focus |
|------|--------------|--------------------|
| ShellBags Registry Analysis | Registry (NTUSER.DAT / USRCLASS.DAT) | Folder access reconstruction |
| USB Device Forensics | SYSTEM Registry | Removable media timeline |

---

## 🧠 Why Windows Artifacts Matter

Windows maintains extensive metadata within the registry and system files.  
Even when files are deleted, many artifacts remain intact and can provide:

- Evidence of user interaction
- Removable device usage
- Access to specific directories
- Temporal activity context
- Indicators of potential data exfiltration

These artifacts are commonly used in:

- Insider threat investigations
- Corporate IR cases
- SOC triage workflows
- Digital forensic examinations

---

## 🔐 DFIR Relevance

Windows artifact analysis is a critical component of modern DFIR operations because:

- Most enterprise environments run Windows endpoints.
- Registry artifacts persist beyond traditional file deletion.
- Device tracking is essential in data leakage investigations.
- Artifact correlation strengthens investigative conclusions.

---

## 📈 Relationship with Other Sections

This module complements:

- `01-Disk-Forensics` → low-level disk & filesystem analysis
- (Future) Memory Forensics → volatile evidence analysis
- (Future) Log & Event Analysis → detection engineering & SOC workflows

Together, these modules form a structured DFIR learning path.

---

## 🧩 Skills Developed

- Registry hive interpretation
- Artifact correlation methodology
- Timeline reconstruction
- Investigative reasoning
- Evidence handling best practices
