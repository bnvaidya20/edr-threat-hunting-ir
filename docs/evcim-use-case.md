# Real-World Use Case: EV Charging Infrastructure Management

## Scenario: Lateral Movement and Persistence in EV Charging Control Systems

**Context:**  
A regional utility provider operates an expanding network of EV charging stations across multiple urban zones. Each station is equipped with smart meters and edge devices communicating over secure VPN tunnels to a centralized SCADA system. A suspected compromise was detected on one of the edge nodes managing real-time billing and load balancing.

---

## Initial Detection:
Wazuh agent running on the EV edge node generated a **File Integrity Monitoring (FIM)** alert triggered by a new cron job entry — a suspicious `bash` reverse shell.

---

## Simulated MITRE Techniques:
- **Persistence via Cron Job** → [T1053.003](https://attack.mitre.org/techniques/T1053/003/)
- **Credential Dumping for Lateral Movement** → [T1003](https://attack.mitre.org/techniques/T1003/)
- **Remote File Copy to Exfiltrate Logs** → [T1105](https://attack.mitre.org/techniques/T1105/)

---

## Threat Hunting Activities:
- **Cron Table Analysis**: Revealed unauthorized recurring jobs using base64-encoded payloads.
- **Log Inspection**: Identified SSH brute force attempts originating from another compromised EV charging node.
- **Reverse Shell Detection**: Triggered on `/bin/bash -i >& /dev/tcp/...` pattern with network alerts.

---

## Incident Response Summary:

| Element                | Detail                                                        |
|------------------------|---------------------------------------------------------------|
| Affected Host          | EV Control Node (Edge) - 192.168.0.104                        |
| Detection Vector       | Wazuh FIM, Sysmon logs, OSSEC Rule Trigger                    |
| Malicious Technique    | Cron job scheduling, credential harvesting                    |
| Forensic Artifacts     | Crontab, .bash_history, memory dump (via Volatility3)         |
| Incident Outcome       | Node was isolated, credentials revoked, VPN tunnel reissued   |

---

## Outcome & Mitigation:
- **Credential rotation** across all EV node endpoints.
- **Segmented VPN access controls** to avoid lateral traversal.
- **Deployment of continuous monitoring policies** for scheduled task changes and unauthorized socket connections.

---

## Key Lessons:
- Lightweight Wazuh agents can provide high-fidelity alerts even on edge devices.
- MITRE ATT&CK-mapped detection helps streamline incident triage.
- EV infrastructure should enforce **zero-trust access** between distributed charging nodes and core SCADA networks.



