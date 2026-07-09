# Troubleshooting Notes

## Issue 1

PowerShell script failed to execute.

Cause

Incorrect file path.

Resolution

Verify:

C:\SOCLab\payload.ps1

---

## Issue 2

Scheduled Task not created.

Cause

PowerShell not running as Administrator.

Resolution

Launch PowerShell with Administrator privileges.

---

## Issue 3

Sysmon events not generated.

Cause

Sysmon service not running.

Verification

Get-Service Sysmon64

Expected Status

Running

---

## Issue 4

PowerShell process not visible.

Resolution

Verify Event Viewer:

Applications and Services Logs

↓

Microsoft

↓

Windows

↓

Sysmon

↓

Operational

↓

Event ID 1

---

## Issue 5

Microsoft Defender events missing.

Cause

Quick Scan still running or not completed.

Resolution

Wait until the scan finishes before checking the Operational log.

---

## Issue 6

Incorrect Defender Event IDs filtered.

Correct Event IDs

- 1000 — Scan Started
- 1001 — Scan Finished

PowerShell Filter

Get-WinEvent -LogName "Microsoft-Windows-Windows Defender/Operational" |
Where-Object {$_.Id -in 1000,1001}

---

## Issue 7

Scheduled Task still exists after the lab.

Cleanup

Delete Scheduled Task

schtasks /delete /tn SOCLabTask /f

---

## Issue 8

Lab files remain on the system.

Cleanup

Remove-Item C:\SOCLab -Recurse -Force

---

## Final Verification

- Sysmon service running
- Scheduled Task removed
- Lab directory deleted
- Defender scan completed successfully
- Event IDs 1000 and 1001 recorded
- Sysmon Event ID 1 captured
