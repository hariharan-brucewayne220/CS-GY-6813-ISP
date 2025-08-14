# CS-GY 6813 — Information Security & Privacy  
## RePy Reference Monitor & Attack Suite

**Author:** Hariharan Loganathan
**NetID:** hl5865  
**Course:** CS-GY 6813 — Spring 2025  
**Grade:** **A**  

---

## 📜 Overview  
This repository contains my full implementation for the **RePy programming labs** from *Information Security & Privacy (CS-GY 6813)*. The work covers:  
1. **Part 0:** Familiarization with RePy through a controlled file-manipulation exercise.  
2. **Part 1:** Hardened reference monitor for secure A/B flash abstraction.  
3. **Part 2:** Offensive test cases to exploit vulnerabilities in insecure reference monitors.  

---

## 🛠 Part 0 — myapplication.r2py  
Goal: Learn the RePy environment and basic file operations.

**Key Changes:**  
- Filled placeholders to open `story.txt`, read first/last characters, and compute file length.  
- Dynamically replaced “lamb” → “LAMB” at the correct offset.  
- Appended a new sentence at EOF without creating gaps.  
- Removed debugging logs for silent final submission.  

---

## 🔒 Part 1 — reference_monitor_hl5865.r2py  
Goal: Implement a **hardened reference monitor** with secure A/B staging.

**Security Features Implemented:**  
- **A/B Flash Abstraction:** Writes go to `filename.b`, commit to `filename.a` only if valid.  
- **Validity Rule:** Must start with `'S'` and end with `'E'`.  
- **Write Guard:** Rejects writes starting with a space at offset 0.  
- **Silent Security:** No logs or exceptions to reveal system details.  
- **Length & EOF Handling:** Accurate tracking, supports writes past EOF, and handles reopen/append flows (IACOR).  
- **Thread-Safety:** Per-file locking to prevent race conditions and ensure resource contention safety.

**✅ All Part 1 Tests Passed:**  
- Writes past EOF — 4.5/4.5  
- Base case — 4.5/4.5  
- File length tracking — 4.5/4.5  
- Valid/multiple writes — 4.5/4.5 each  
- Invalid writes — 4.5/4.5  
- IACOR — 4.5/4.5  
- Leading-space writes — 4.5/4.5  
- Resource contention — 4.5/4.5  
- Existing file writes — 4.5/4.5  

---

## 💣 Part 2 — attackcase\*.r2py  
Goal: Identify and exploit vulnerabilities in insecure monitors (secure monitor must remain unbroken).

**Attack Strategies:**  
- **File-length & boundary probes** — exploited incorrect validation based on size/offset.  
- **Poor-defense probes** — manipulated `create` flag, out-of-order writes, and backup exposure attempts.  

**✅ Vulnerable Monitor Tests Passed:**  
- Threading-defense vulnerabilities — 13.5/13.5  
- File-length validation vulnerabilities — 13.5/13.5  
- Bare functionality — 9/9  
- Poor defenses — 9/9  
- Secure monitor — remained unbroken (expected).  

---

## 📂 Repository Structure  
```
.
├── myapplication.r2py           # Part 0 solution
├── reference_monitor_hl5865.r2py # Part 1 hardened monitor
├── attackcase1.r2py              # Part 2 attack file #1
├── attackcase2.r2py
├── attackcase3.r2py
├── attackcase4.r2py
└── README.md                     # This document
```

---

## 🚀 Running the Code  

### **Part 0**  
```bash
python3 repy.py encasementlib.r2py gettingstartedmonitor.r2py myapplication.r2py
```

### **Part 1** (Hardened Monitor)  
```bash
python3 repy.py encasementlib.r2py reference_monitor_hl5865.r2py attackcase1.r2py
```

### **Part 2** (Testing Attacks)  
Replace `attackcaseX.r2py` with the desired attack case.  

---

## 📈 Results Summary  
| Part | Description | Result |
|------|-------------|--------|
| 0    | Basic RePy familiarity | Completed |
| 1    | Hardened reference monitor | **All tests passed** |
| 2    | Offensive testing on insecure monitors | **All vulnerable tests passed; secure monitor unbroken** |

---


