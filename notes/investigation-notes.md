# Investigation Notes

## Objective

Investigate a simulated multi-stage Windows attack using Sysmon and Microsoft Defender logs.

---

## Timeline

### Step 1 – PowerShell Payload Creation

Created:

C:\SOCLab\payload.ps1

Purpose

Simulate attacker payload.

---

### Step 2 – Payload Execution

Executed:

powershell.exe -ExecutionPolicy Bypass -File C:\SOCLab\payload.ps1

Observed

- Sysmon Event ID 1

Evidence

- Process Name
- Command Line
- Parent Process
- User

MITRE

T1059.001

---

### Step 3 – Scheduled Task Creation

Created:

SOCLabTask

Purpose

Persistence mechanism.

MITRE

T1053.005

---

### Step 4 – File Download

Executed

Invoke-WebRequest

Downloaded

page.html

Purpose

Simulate payload retrieval.

MITRE

T1105

---

### Step 5 – Microsoft Defender Scan Started

Observed

Microsoft Defender

Event ID 1000

Collected

- Scan Type
- User
- Scan Parameters

---

### Step 6 – Microsoft Defender Scan Completed

Observed

Microsoft Defender

Event ID 1001

Collected

- Scan Duration
- User
- Scan Parameters

---

## Attack Timeline

PowerShell Payload Created

↓

PowerShell Executed

↓

Scheduled Task Created

↓

File Download

↓

Microsoft Defender Scan Started

↓

Microsoft Defender Scan Finished

---

## Conclusion

The investigation successfully correlated Sysmon process creation logs with Microsoft Defender Operational logs to reconstruct the complete attack lifecycle.

No malware was detected during the Defender scan.
