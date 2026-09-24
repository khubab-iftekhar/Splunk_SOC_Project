# Splunk SOC Detection & Investigation Lab

SOC L1/L2 detection and investigation lab in Splunk Enterprise using the Boss of the SOC (BOTS v1) dataset, with every detection mapped to MITRE ATT&CK.

**Status:** In progress

---

## 1. Project Overview

| Item | Detail |
|---|---|
| Goal | Simulate the daily workflow of a SOC analyst (L1 triage to L2 investigation) using a SIEM |
| Platform | Splunk Enterprise 10.2.3 on Windows (SPL, dashboards, alerts, CIM) |
| Data | BOTS v1 (primary), plus small supplementary datasets and self-generated Windows logs |
| Log sources | Windows Security, Sysmon, Suricata IDS, IIS/web logs, HTTP stream, DNS |
| Frameworks | MITRE ATT&CK, Cyber Kill Chain, NIST SP 800-61 |
| Planned outcome | 12 core detections, 2 dashboards, triage playbooks, 1-2 incident reports |

## 2. Objectives

1. Onboard and understand multi-source security telemetry in Splunk
2. Build and tune detections mapped to MITRE ATT&CK techniques
3. Create dashboards for SOC monitoring and threat hunting
4. Configure alerts with severity, throttling, and triage guidance
5. Investigate a multi-stage attack and reconstruct the full timeline
6. Write professional incident reports with IOCs and recommendations

## 3. Repository Structure

| Folder | Contents |
|---|---|
| 01-lab-setup | Installation, licensing, data onboarding, troubleshooting |
| 02-data-understanding | Data source cheat sheet, sourcetypes, key fields |
| 03-detections | Detection catalog and SPL for each detection |
| 04-dashboards | SOC overview and threat hunting dashboards |
| 05-alerts-and-playbooks | Alert configuration and triage playbooks |
| 06-investigations | End-to-end incident investigations |
| 07-reports | Incident reports and templates |

## 4. Project Phases

**Phase 1: Lab Setup.** Install Splunk Enterprise, load BOTS v1, verify with `index=botsv1 | stats count by sourcetype`, install the Windows, Sysmon, and CIM add-ons.

**Phase 2: Data Understanding.** Document every sourcetype: purpose, key fields, and use cases. Map fields to CIM.

**Phase 3: Detection Engineering.** Build 12 core detections. Each one is documented with description, ATT&CK mapping, SPL, data source, test results, false positives, tuning (before and after counts), alert configuration, and a triage playbook.

**Phase 4: Dashboards.** SOC overview (alert volume, top source IPs, failed logons, top techniques) and a threat hunting dashboard with drilldowns.

**Phase 5: Alerting and Triage.** Save detections as scheduled alerts with severity, throttling, and tags. Write a triage playbook per alert type.

**Phase 6: Incident Investigation.** Work the BOTS v1 scenarios end to end and build timelines from initial access through impact.

**Phase 7: Reporting.** Executive summary, timeline, root cause, IOCs, ATT&CK mapping, impact, remediation, and lessons learned.

## 5. Detection Catalog

| # | Detection | ATT&CK | Data Source | Status |
|---|---|---|---|---|
| 1 | Brute force / password spray | T1110 | Windows Security 4625 | Planned |
| 2 | Successful logon after multiple failures | T1110 | Windows Security 4624/4625 | Planned |
| 3 | Office app spawning shell | T1204, T1059 | Sysmon EID 1 | Planned |
| 4 | Encoded PowerShell execution | T1059.001 | Sysmon EID 1 | Planned |
| 5 | New service creation | T1543.003 | Windows 7045 / 4697 | Planned |
| 6 | Web vulnerability scanner activity | T1595 | HTTP / web logs | Planned |
| 7 | Joomla admin login brute force | T1110 | HTTP stream | Planned |
| 8 | Suspicious file upload to web server | T1105 | HTTP stream / IIS | Planned |
| 9 | DNS anomalies (long/rare domains) | T1071.004 | DNS logs | Planned |
| 10 | Scheduled task creation | T1053.005 | Sysmon / Security 4698 | Planned |
| 11 | Mass file rename / ransomware extension | T1486 | Sysmon EID 11 | Planned |
| 12 | Suricata high-severity alert correlation | Multiple | Suricata | Planned |

Status values: Planned, Built, Tested, Tuned, Documented. A detection is only marked Tested after it has been run against real data.

## 6. Skills Demonstrated

- SIEM: Splunk SPL, dashboards, alerts, data models, field extraction
- Detection engineering: rule creation, tuning, false positive reduction
- Threat hunting: hypothesis-driven searches and pivoting across sources
- Incident response: triage, timeline reconstruction, IOC extraction
- Frameworks: MITRE ATT&CK, Cyber Kill Chain, NIST SP 800-61
- Log analysis: Windows events, Sysmon, IDS, web, DNS
- Documentation: playbooks and incident reports

## 7. Results

| Metric | Result |
|---|---|
| Detections built | TBD |
| ATT&CK techniques covered | TBD |
| Events analyzed | TBD |
| Incidents investigated | TBD |
| False positive reduction after tuning | TBD |

## 8. Lab Notes

The lab-setup folder documents real problems hit during setup, including the Splunk Free license fallback ("Requires license feature='Auth'") and how it was diagnosed and fixed.

## 9. References

- Boss of the SOC (BOTS) v1: github.com/splunk/botsv1
- Splunk Attack Data: github.com/splunk/attack_data
- EVTX-ATTACK-SAMPLES: github.com/sbousseaden/EVTX-ATTACK-SAMPLES
- MITRE ATT&CK: attack.mitre.org
- NIST SP 800-61 Rev. 2

## 10. Author

Khubab Iftekhar | SOC Analyst (aspiring) | LinkedIn:
