# EDR Threat Hunting & Incident Response Project

This repository demonstrates practical implementations of **EDR (Endpoint Detection and Response)** for threat hunting and incident response using **Wazuh** in a virtualized lab setup. It includes hands-on simulation of adversarial techniques and a real-world industrial use case in **EV Charging Infrastructure Management**.

---

## Objectives

- Deploy Wazuh XDR/EDR with Docker and configure agent-based monitoring.
- Simulate adversarial behavior using MITRE ATT&CK TTPs.
- Conduct blue team threat hunting and forensic investigation.
- Analyze a real-world attack simulation in EV infrastructure using Wazuh.

---

## Project Components

| Component         | Description                                              |
|------------------|----------------------------------------------------------|
| [`edr-ir-implementation.md`](./docs/edr-ir-implementation.md) | Full step-by-step guide to building the EDR lab with Dockerized Wazuh Manager and Ubuntu Endpoint using VirtualBox. |
| [`evcim-use-case.md`](./docs/evcim-use-case.md)              | EV Charging Infrastructure Management: Simulated real-world use case for lateral movement, persistence, and log exfiltration. |

---

## Lab Setup Overview

### System Architecture

| Host             | IP             | Role                     |
|------------------|----------------|--------------------------|
| Wazuh Manager    | 192.168.0.103  | EDR/SIEM (Dockerized)    |
| Ubuntu Endpoint  | 192.168.0.104  | Wazuh Agent + Red Team   |
| VirtualBox Host  | —              | Bridged Networking       |

➡️ Refer to: [`EDR Implementation Guide`](./docs/edr-ir-implementation.md#step-by-step-setup)

---

## Red Team Simulations

### Simulated MITRE ATT&CK Techniques:

| Technique Description                  | MITRE ID     |
|----------------------------------------|--------------|
| Persistence via Cron Job               | [T1053.003](https://attack.mitre.org/techniques/T1053/003/) |
| Credential Dumping                     | [T1003](https://attack.mitre.org/techniques/T1003/) |
| Remote File Copy (Exfiltration)        | [T1105](https://attack.mitre.org/techniques/T1105/) |

➡️ Refer to: [`Red Team Attack Simulation`](./docs/edr-ir-implementation.md#6-simulate-attacks-red-team)

---

## Blue Team Activities

- Detect suspicious cron jobs, unauthorized shell invocations.
- Monitor file integrity and system logs.
- Investigate credential theft or log manipulation attempts.

➡️ Refer to: [`Threat Hunting`](./docs/edr-ir-implementation.md#7-threat-hunting-blue-team)

---

## Real-World Scenario: EV Infrastructure

A simulated breach in smart EV charging control systems demonstrates how Wazuh can detect and respond to:

- Lateral movement via harvested credentials.
- Cron job persistence with reverse shell payloads.
- Exfiltration attempts using remote file copy tools.

➡️ Detailed Report: [`EV Charging Use Case`](./docs/evcim-use-case.md)

---

## Forensic & Incident Response Workflow

- Collect logs and `.bash_history` from endpoints.
- Analyze artifacts with Volatility3 for memory forensics.
- Document findings in structured incident reports.

➡️ Template: [`Incident Report Format`](./docs/edr-ir-implementation.md#8-incident-response--forensics)

---

## Dashboards & Visualizations

- Wazuh Security Event Monitoring
- MITRE ATT&CK Technique Mapping

➡️ Screenshots: [`Dashboards`](./docs/edr-ir-implementation.md#8-dashboard-samples)

---

## Key Takeaways

- Wazuh provides robust detection for edge and control nodes.
- Combining MITRE ATT&CK with FIM and Sysmon rules streamlines threat response.
- Ideal for simulating and training on real-world cybersecurity challenges.

---

## Related Resources

- [Wazuh Documentation](https://documentation.wazuh.com/)
- [Atomic Red Team Repository](https://github.com/redcanaryco/atomic-red-team)
- [MITRE ATT&CK Framework](https://attack.mitre.org/)

---

## License

This repository is open for educational and research use. Attribution encouraged.

---

