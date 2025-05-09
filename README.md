# Sideloading-well_known_domains.dll  Microsoft Edge.

This technique abuses DLL search order hijacking by planting a **malicious `well_known_domains.dll`** in a **user-writable directory** that is later loaded by a **trusted Microsoft-signed binary**—specifically, **Microsoft Edge**.

---

## 🔧 Steps to Reproduce

1. Copy your malicious DLL to the following path:
   ```
   C:\Users\<USERNAME>\AppData\Local\Microsoft\Edge\User Data\Well Known Domains\1.x.x.x
   ```

2. **Launch or close Microsoft Edge.**  
   This action triggers the vulnerable DLL load, causing the payload to execute.

---

## 🧠 Technical Details

- The target directory is **user-writable**:
  ```
  C:\Users\<USERNAME>\AppData\Local\Microsoft\Edge\User Data\Well Known Domains\1.2.0.0
  ```

- **Edge will load `well_known_domains.dll` from this location**, trusting it implicitly.

- No integrity or signature validation is performed on the DLL.

- This results in **arbitrary code execution** within the context of a **trusted Microsoft process**, which can:
  - Bypass certain endpoint defenses.
  - Aid in defense evasion and persistence.
  - Be used in **living-off-the-land (LotL)** scenarios.

---

> 💡 **Tip:** Combine with AMSI or ETW bypasses for stealthier operations.
```
