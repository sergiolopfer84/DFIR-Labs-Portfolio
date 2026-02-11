# 🧪 Lab: USB Device Activity Reconstruction (USBDeview)

## 🧾 Scenario

A Windows system was examined to determine which USB storage devices had been connected, when they were first installed, and when they were last used.

The goal was to evaluate potential removable media usage that could indicate data transfer or exfiltration.

---

## 🎯 Objective

- Identify connected USB storage devices.
- Extract device serial numbers.
- Determine first and last connection timestamps.
- Reconstruct removable device timeline activity.

---

## 🧠 Technical Background

Windows records USB device activity in the registry.

Primary registry locations:

HKLM\SYSTEM\CurrentControlSet\Enum\USBSTOR
HKLM\SYSTEM\MountedDevices


Relevant metadata includes:

- Vendor ID (VID)
- Product ID (PID)
- Serial Number
- First Install Date
- Last Plug Date
- Drive Letter Assignment
- Device Description

These artifacts persist even after device removal.

---

## 🛠 Tool Used

- USBDeview (NirSoft)

---

## 🔄 Investigation Workflow

### 1️⃣ Artifact Acquisition

USBDeview was executed to extract device metadata.

Analysis included both:

- Currently connected devices
- Previously connected (disconnected) devices

---

### 2️⃣ Field Analysis

The following columns were reviewed:

- Device Name
- Device Description
- Connected Status
- Drive Letter
- Serial Number
- Registry Time 1 (First Install)
- Registry Time 2 (Last Plug/Unplug)
- VendorID
- ProductID

---

### 3️⃣ Timeline Reconstruction

Device connection timestamps were compared to:

- User activity
- File access events
- Other forensic artifacts

---

## 📊 Key Findings

- Historical USB devices were identified.
- Unique serial numbers enabled device distinction.
- First and last connection timestamps were recoverable.
- Device usage timeline was reconstructable.

---

## ⚖️ Forensic Considerations

- USB artifacts do not confirm file copying.
- Must be correlated with:
  - ShellBags
  - $MFT
  - $UsnJrnl
  - Event Logs
  - Prefetch
- Registry timestamps may reflect installation events rather than active file transfer.

---

## 🔐 SOC & Incident Response Relevance

USB artifact analysis is critical in:

- Data exfiltration investigations
- Insider threat scenarios
- Unauthorized removable media usage
- Corporate endpoint monitoring
- Incident timeline reconstruction

---

## 🧩 Lessons Learned

- Windows maintains persistent USB device records.
- Serial numbers are key for attribution.
- Timeline reconstruction requires multi-artifact correlation.
- Removable media analysis is a core DFIR competency.
