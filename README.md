# Wazuh SOC Home Lab

## Overview
A hands-on Security Operations Center (SOC) home lab built to practice endpoint security monitoring, Windows event analysis, and basic incident investigation using Wazuh.

## Lab Architecture
- **SIEM:** Wazuh
- **Manager:** Debian Linux virtual machine
- **Endpoint:** Windows 11 with Wazuh agent
- **Virtualization:** Oracle VirtualBox

## Implemented and Tested

### 1. Windows Authentication Monitoring
- Investigated successful logon events (Windows Event ID 4624).
- Generated and investigated a controlled failed-login event (Event ID 4625).
- Verified that the failed-login event was visible in Wazuh.
- Examined available event details, including timestamps and logon information.

### 2. Process-Creation Monitoring
- Enabled Windows process-creation auditing.
- Verified Event ID 4688 in Windows Event Viewer.
- Checked Wazuh for corresponding process-creation events.

### 3. File Integrity Monitoring
- Tested file creation and deletion monitoring.
- Examined the resulting security events.

## Investigation Workflow
1. Generate a controlled test event on the lab endpoint.
2. Verify the event in Windows Event Viewer.
3. Search for the corresponding event in Wazuh.
4. Review timestamps, event fields, and alert metadata.
5. Document evidence, findings, and recommended next steps.

## Current Scope
This project demonstrates basic endpoint telemetry collection and event investigation in a personal lab. Advanced correlation rules, broader detection coverage, and additional attack simulations will be documented only after they have been implemented and tested.

## Evidence
See the `screenshots/`, `incident-reports/`, and `test-cases/` directories.

## Disclaimer
All tests are performed on systems controlled by the project owner in a personal lab environment. Sensitive identifiers are redacted from published evidence.
