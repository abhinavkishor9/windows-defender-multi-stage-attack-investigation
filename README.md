# windows-defender-multi-stage-attack-investigation
## Overview

This project demonstrates a simulated multi-stage Windows attack and investigates the generated telemetry using Sysmon and Microsoft Defender.

The objective is to understand how endpoint activities generate security events and how defenders can correlate logs to reconstruct an attack timeline.

---

## Lab Objectives

- Execute a PowerShell script
- Establish persistence using a Scheduled Task
- Simulate a file download
- Trigger a Microsoft Defender Quick Scan
- Investigate Sysmon Process Creation events
- Investigate Microsoft Defender Operational logs
- Correlate multiple events into a single attack timeline

---

## Lab Environment

- Windows 10
- Microsoft Defender Antivirus
- Sysmon v15
- Windows Event Viewer
- PowerShell

---

## Attack Scenario

The following activities were performed during the simulation:

1. Created a PowerShell payload.
2. Executed the payload using PowerShell.
3. Created a Scheduled Task for persistence.
4. Simulated a file download using Invoke-WebRequest.
5. Ran a Microsoft Defender Quick Scan.
6. Investigated Sysmon and Defender logs.
7. Correlated all events into a complete attack timeline.

---

## Investigation Timeline

### Phase 1 – PowerShell Execution

Observed using:

- Sysmon Event ID 1

Evidence

- powershell.exe executed
- payload.ps1 launched

MITRE ATT&CK

- T1059.001 – PowerShell

---

### Phase 2 – Persistence

A Scheduled Task named **SOCLabTask** was created.

Purpose

Persistence through scheduled task execution.

MITRE ATT&CK

- T1053.005 – Scheduled Task

---

### Phase 3 – File Download

PowerShell downloaded a file using:

- Invoke-WebRequest

Purpose

Simulated payload retrieval from the Internet.

MITRE ATT&CK

- T1105 – Ingress Tool Transfer

---

### Phase 4 – Microsoft Defender Response

A Quick Scan was started manually.

Windows Defender generated:

- Event ID 1000 – Scan Started
- Event ID 1001 – Scan Finished

Collected Information

- Scan Type
- Scan Parameters
- User
- Scan Duration

---

## Event Correlation

| Event Source | Event ID | Purpose |
|--------------|---------|---------|
| Sysmon | 1 | PowerShell Process Creation |
| Microsoft Defender | 1000 | Scan Started |
| Microsoft Defender | 1001 | Scan Completed |

---

## MITRE ATT&CK Mapping

| Activity | Technique |
|----------|-----------|
| PowerShell Execution | T1059.001 |
| Scheduled Task Persistence | T1053.005 |
| File Download | T1105 |

---

## Skills Demonstrated

- Endpoint Threat Hunting
- Windows Event Log Analysis
- Sysmon Investigation
- Microsoft Defender Investigation
- PowerShell Analysis
- Process Creation Analysis
- Scheduled Task Investigation
- Timeline Correlation
- MITRE ATT&CK Mapping

---

## Learning Outcome

This lab demonstrates how multiple endpoint activities generate security telemetry and how Sysmon and Microsoft Defender logs can be correlated to reconstruct an attack timeline during a SOC investigation.
