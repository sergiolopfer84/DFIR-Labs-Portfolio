# 🔍 Web Activity Reconstruction – Browser Artifacts Analysis

## 📌 Scenario

A Windows user workstation was analyzed after suspicion of non-authorized web usage during working hours.

The objective was to reconstruct the user’s web browsing activity and determine:

- What websites were accessed
- What searches were performed
- Whether files were downloaded or opened
- If any suspicious or malicious domains were visited
- If activity correlates with local file access

---

## 🛠 Tools Used

- Wintriage (evidence acquisition)
- ChromeHistoryView (Nirsoft)
- BrowsingHistoryView (Nirsoft)
- Windows File System Artifacts

---

## 📂 Evidence Source

Browser history extracted from:
- Google Chrome (Chromium-based)
- User profile directory

---

## 🔎 Step 1 – ChromeHistoryView Analysis

ChromeHistoryView was used to analyze the SQLite `History` database.

### Key Fields Analyzed

- URL
- Title
- Visited On
- Visit Count
- Typed Count
- Referrer
- Visit Duration
- Profile

---

### 📊 Findings

#### 🔹 Repeated Website Access

- `https://rtvc.es/en-directo/`
- Multiple visits on 08/08/2025 between 09:46 and 10:31
- Accessed via Google search query (`search?q=rtvc`)

**Interpretation:**  
User actively accessed live streaming media content during working hours.

---

#### 🔹 Search Activity Identified

Example search query:

- "jurassic world rebirth poster imdb"

**Interpretation:**  
Search conducted manually (confirmed via Typed Count > 0).

---

## 🔎 Step 2 – BrowsingHistoryView Analysis

BrowsingHistoryView was used to correlate multi-browser activity and detect local file access.

---

### 📂 Local File Access (file://)

Observed entries:


file:///C:/Users/Usuario/Desktop/Guías/Práctica Volatility.odt
file:///C:/Users/Usuario/Downloads/


**Interpretation:**

- User opened a local .odt document from Desktop.
- User accessed Downloads folder.
- Confirms interaction with local files during same session timeframe.

---

## 🧵 Timeline Reconstruction

| Date       | Time   | Activity |
|------------|--------|----------|
| 08/08/2025 | 09:46  | Google search performed |
| 08/08/2025 | 09:48  | Access to rtvc.es |
| 08/08/2025 | 10:05  | Local file opened (.odt) |
| 08/08/2025 | 10:12  | Downloads folder accessed |

---

## 🚨 Suspicious Indicators Assessment

- ❌ No access to known malicious domains
- ❌ No suspicious download URLs
- ❌ No evidence of phishing or exploit kits
- ❌ No high-risk external IP connections observed

Activity appears consistent with:

- Media streaming
- Educational research
- Local document access

---

## 🔗 Correlation Opportunities (Advanced DFIR)

This browser artifact analysis can be correlated with:

- Prefetch (to confirm browser execution times)
- Amcache (to confirm downloaded executables)
- Event Logs (to verify session logon time)
- Memory analysis (if dump available)

---

## ✅ Conclusion

The reconstructed browsing history indicates:

- Repeated access to media content
- Educational platform usage
- Manual search activity
- Local document interaction

No indicators of compromise were detected in this dataset.

---

## 📚 Lessons Learned

- Browser artifacts provide strong insight into user intent.
- Typed Count helps differentiate between direct URL entry and redirected traffic.
- Referrer field helps reconstruct navigation chains.
- `file://` entries are extremely valuable for correlating web and local activity.
- Multisource artifact correlation significantly increases evidentiary strength.

---

## 🎯 DFIR Value

This lab demonstrates:

- Web artifact extraction
- Behavioral reconstruction
- Timeline building
- Analytical interpretation
- Suspicion validation methodology
