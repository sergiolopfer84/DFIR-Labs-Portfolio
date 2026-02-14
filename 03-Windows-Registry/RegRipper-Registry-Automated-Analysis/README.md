# 🔍 Automated Windows Registry Analysis – RegRipper DFIR Lab

## 🧪 Lab: Multi-Hive Registry Analysis with RegRipper

---

## 🧾 Scenario

A Windows system image was examined to perform automated registry analysis using RegRipper 3.0.

The objective was to extract and correlate forensic artifacts from multiple Windows registry hives in order to reconstruct:

- System configuration
- Installed software
- User activity
- Persistence mechanisms
- Execution history

---

## 🎯 Objective

- Extract Windows registry hives from a forensic image.
- Perform automated analysis using RegRipper profiles.
- Identify installed applications and system metadata.
- Extract execution artifacts (UserAssist, Run keys, MRUs).
- Reconstruct user behavior from NTUSER.DAT.
- Detect potential persistence mechanisms.
- Understand multi-hive artifact correlation.

---

## 🧠 Technical Background

Windows registry hives analyzed:

SAM
SECURITY
SOFTWARE
SYSTEM
NTUSER.DAT


Primary system hive location:

Windows\System32\config\


User hive location:

Users<username>\NTUSER.DAT


Each hive contains distinct forensic artifacts:

- **SAM** → User accounts, RIDs, account metadata
- **SOFTWARE** → Installed applications, OS version, Run keys
- **SYSTEM** → Hardware and control data
- **NTUSER.DAT** → User-level activity and execution history

RegRipper automates artifact extraction via plugins tailored to each hive.

---

## 🛠 Tool Used

- RegRipper 3.0
- FTK Imager (Hive acquisition)

---

## 🔄 Investigation Workflow

### 1️⃣ Hive Acquisition

Hives were extracted from:

Windows\System32\config\


User hive extracted from:

Users<username>\NTUSER.DAT


All original files were preserved to maintain forensic integrity.

---

### 2️⃣ Automated Hive Processing

Each hive was processed using RegRipper with the corresponding profile:

- `sam`
- `software`
- `system`
- `security`
- `ntuser`

RegRipper generated structured text reports containing extracted artifacts.

---

### 3️⃣ Command-Line Analysis (Example)

Example of targeted plugin execution:

```bash
rip -r NTUSER.DAT -p userassist
This command extracts:

Executed programs

Execution count

Last execution timestamp

📊 Key Artifacts Extracted
🔹 From SOFTWARE Hive
OS version

Hostname

Installation date

Installed applications (name, version, publisher)

Auto-start entries (Run / RunOnce)

Compatibility settings

Forensic value:

Detect unauthorized software

Identify forensic tools present on system

Establish software installation timeline

🔹 From NTUSER.DAT Hive
UserAssist (executed programs)

MRUs (Most Recently Used documents)

ShellBags (folder access history)

Run keys (user-level persistence)

Jump Lists

Search history (WordWheelQuery)

TypedPaths

RunMRU entries

Forensic value:

Reconstruct user behavior

Detect recently executed tools

Identify access to removable media

Investigate insider activity

Detect user-level persistence

📈 Example Forensic Interpretation
UserAssist entries provide:

UTC timestamp of last execution

Executable path

Execution count

This allows analysts to:

Determine software usage frequency

Identify tools executed before or after an incident

Correlate activity with timeline artifacts

⚖️ Forensic Considerations
RegRipper output must be validated against raw hive data.

Automated extraction does not replace manual verification.

Registry timestamps reflect key modification, not necessarily direct user interaction.

Multi-hive correlation is required for accurate timeline reconstruction.

🔐 SOC & Incident Response Relevance
RegRipper-based registry analysis is critical for:

Post-compromise host analysis

Insider threat investigations

Detection of persistence mechanisms

Identifying unauthorized tools

Reconstructing user behavior

Incident timeline development

Automated registry parsing significantly accelerates triage during incident response.

🧩 Lessons Learned
Multi-hive analysis provides deeper investigative insight than single-hive analysis.

NTUSER.DAT is crucial for user-level behavioral reconstruction.

UserAssist and Run keys are high-value persistence indicators.

Automation improves efficiency but requires analyst validation.

Registry analysis is foundational in Windows DFIR investigations.
