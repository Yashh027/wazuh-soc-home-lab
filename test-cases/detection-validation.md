# Wazuh SOC Home Lab — Detection Validation

## 1. Objective

Validate that the Wazuh home lab collects and displays selected Windows security events and supports basic File Integrity Monitoring (FIM) tests.

## 2. Test Environment

- **SIEM:** Wazuh
- **Manager OS:** Debian Linux
- **Endpoint OS:** Windows 11
- **Virtualization:** Oracle VirtualBox
- **Event Investigation:** Wazuh Threat Hunting and Windows Event Viewer

## 3. Test Results

| Test ID | Test Case | Expected Result | Observed Result | Status |
|---|---|---|---|---|
| DV-01 | Successful Windows logon | Event ID 4624 is recorded and visible in Wazuh | Successful workstation logon events appeared under rule ID 60118 | PASS |
| DV-02 | Controlled failed Windows logon | Event ID 4625 is recorded and an associated Wazuh alert is visible | Failed-logon event appeared under rule ID 60122, level 5 | PASS |
| DV-03 | Process-creation auditing | Event ID 4688 is recorded when a new process starts | Event ID 4688 was verified in Windows Event Viewer and Wazuh | PASS |
| DV-04 | File creation and deletion | FIM reports the tested file changes | File creation and deletion monitoring was tested successfully | PASS |

## 4. Test Procedures

### DV-01: Successful Logon

1. Sign in to the Windows endpoint normally.
2. Open Windows Event Viewer.
3. Navigate to Windows Logs → Security.
4. Locate Event ID 4624.
5. Search for the event in Wazuh Threat Hunting.

**Result:** Successful workstation logon events were visible in Wazuh.

### DV-02: Failed Logon

1. Perform a controlled failed-login test on the lab endpoint.
2. Locate Event ID 4625 in Windows Event Viewer.
3. Search for the event in Wazuh Threat Hunting.
4. Inspect the timestamp, rule ID, alert level, and available authentication details.

**Result:** The failed-logon event was visible in Wazuh under rule ID 60122 with alert level 5.

### DV-03: Process-Creation Monitoring

1. Enable the Windows Process Creation audit policy.
2. Start new processes on the Windows endpoint.
3. Locate Event ID 4688 in Windows Event Viewer.
4. Search for corresponding events in Wazuh.

**Result:** Process-creation events were verified in Windows and Wazuh.

### DV-04: File Integrity Monitoring

1. Create a test file in a monitored directory.
2. Check Wazuh for the resulting FIM event.
3. Delete the test file.
4. Check for the corresponding deletion event.

**Result:** File creation and deletion monitoring was tested successfully.

## 5. Overall Assessment

The tests confirmed basic collection and visibility of selected Windows authentication and process-creation events, along with the tested FIM behavior.

These results establish a working foundation for further SOC investigation exercises. They do not demonstrate comprehensive threat detection or protection against all attack techniques.

## 6. Planned Improvements

- Test repeated failed logons and verify whether existing Wazuh rules generate a correlated alert.
- Document additional event fields and their investigative value.
- Develop and test custom detection rules where needed.
- Add further endpoint monitoring and incident scenarios.
- Capture sanitized evidence for each validated test.

## 7. Evidence

Relevant screenshots and investigation reports are maintained in the `screenshots/` and `incident-reports/` directories.

Only tests that have been performed and verified should be marked as passed.
