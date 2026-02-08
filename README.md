# Endpoint Telemetry → MITRE ATT&CK Mapping

## Overview
This lab demonstrates a SOC-style workflow for analyzing Windows endpoint execution telemetry and translating observed behavior into MITRE ATT&CK context. The focus is on analyst reasoning and detection thinking rather than reliance on SIEM tooling.

The objective is to practice identifying execution patterns, understanding their significance, and communicating findings using standardized security frameworks.

---

## Data Source
- Windows process creation telemetry  
- Security Event ID 4688 and/or Sysmon Event ID 1  

Telemetry was reviewed directly from the endpoint to reinforce foundational analysis skills independent of specific SIEM platforms.

---

## Detection Scenario
Encoded PowerShell execution was generated to replicate a commonly abused execution technique used to obscure command-line activity.

While the command executed in this lab was benign (`whoami`), encoded PowerShell is frequently observed in real-world tradecraft due to its ability to reduce visibility into script contents.

---

## MITRE ATT&CK Mapping
The observed behavior was mapped to the following MITRE ATT&CK technique:

- **T1059 – Command and Scripting Interpreter**
  - **T1059.001 – PowerShell**

This mapping was selected because the execution involved interpreter-based command execution with encoded input, which aligns directly with the technique definition.

---

## Detection Logic
A simple detection concept was defined to identify PowerShell executions containing encoded command-line arguments.

This behavior alone does not confirm malicious activity; however, it represents higher-scrutiny telemetry that warrants additional context-based validation.

Factors that would be reviewed before escalation include:
- Parent process
- User context
- Host role
- Adjacent activity (network connections, file writes, persistence mechanisms)

---

## Key Takeaways
- Endpoint execution telemetry provides high-value visibility into system behavior
- Encoded command-line execution is a dual-use pattern that requires analyst judgment
- MITRE ATT&CK enables consistent communication of observed behavior across tools and teams
- Detection effectiveness depends on context, not individual events in isolation

---

## Artifacts
- Process execution command demonstrating encoded PowerShell
- Corresponding process creation event from Windows logs
- MITRE ATT&CK technique reference
- Sigma-style detection logic for encoded PowerShell execution
