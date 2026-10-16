# Incident 001: Windows Failed Login Investigation

## 1. Incident Summary

A failed Windows logon event was detected and investigated using Wazuh. The event was generated during a controlled authentication test on my own Windows 11 endpoint.

The objective was to verify Windows security event collection, Wazuh alert generation, and the basic incident investigation workflow.

## 2. Lab Environment

- **SIEM:** Wazuh
- **Wazuh Manager:** Debian Linux virtual machine
- **Monitored Endpoint:** Windows 11
- **Virtualization:** Oracle VirtualBox
- **Windows Event ID:** 4625 — Failed logon
- **Wazuh Rule ID:** 60122
- **Wazuh Alert Level:** 5

## 3. Detection Evidence

- **Event timestamp:** 16 October 2026, approximately 18:13:08
- **Agent name:** WINDOWS-AGENT
- **Event description:** Logon Failure — Unknown user or bad password
- **Detection source:** Windows Security event log, forwarded to and analyzed by Wazuh

The event was visible in Windows Event Viewer and the corresponding failed-logon alert was found in Wazuh Threat Hunting.

## 4. Investigation Steps

1. Generated a controlled failed-login event on my own Windows endpoint.
2. Verified Event ID 4625 in Windows Event Viewer.
3. Searched for the corresponding event in Wazuh Threat Hunting.
4. Confirmed that Wazuh displayed the failed-logon event under rule ID 60122 with alert level 5.
5. Reviewed the available event details, including the timestamp and authentication-related fields.

## 5. Findings

The test confirmed that Windows authentication telemetry was being collected and that Wazuh generated an alert for the failed logon.

A single failed login is not sufficient evidence of a brute-force attack or unauthorized access. Further investigation would be required to establish whether the event was suspicious.

## 6. Recommended Follow-up

- Review additional failed logons for repeated attempts against the same account.
- Correlate failed logons with nearby successful logons.
- Review the logon type and source address, when available.
- Investigate unusual patterns before classifying the activity as malicious.

## 7. Outcome

**Result: Detection test passed.**

The controlled failed-login event was recorded by Windows and its corresponding alert was visible in Wazuh.

**Scope limitation:** This test validates event collection and alert visibility. It does not establish that a real attack occurred or that every authentication-related threat would be detected.

## 8. Evidence

- Wazuh failed-logon alert screenshot: `../screenshots/failed-login-4625.png`
- Additional Windows Event Viewer evidence: Add a screenshot if available

All testing was conducted in a personal lab environment. Personal identifiers have been omitted from this report.
