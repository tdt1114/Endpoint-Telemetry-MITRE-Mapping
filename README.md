# Endpoint Telemetry → MITRE ATT&CK Mapping

## Overview
This lab demonstrates the process of analyzing Windows endpoint execution telemetry and mapping observed behavior to the MITRE ATT&CK framework, with a focus on analyst reasoning rather than tooling.
## Data Source
Windows process creation telemetry collected via native Security Event ID 4688 / Sysmon Event ID 1.
## Detection Scenario
Encoded PowerShell execution was generated to replicate a commonly abused execution technique used to obscure command-line activity.
## MITRE ATT&CK Mapping
The observed behavior was mapped to T1059.001 – PowerShell, which covers interpreter-based execution commonly leveraged for both administrative automation and adversary tradecraft.
## Detection Logic
A simple detection concept was defined to identify PowerShell executions containing encoded command-line arguments, acknowledging that additional context is required to reduce false positives.
## Key Takeaways
 - Execution telemetry provides high-value visibility
 - Behavior-based detection requires context
 - MITRE ATT&CK enables consistent communication across tools and teams
