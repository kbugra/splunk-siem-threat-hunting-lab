# Advanced SIEM & Threat Hunting Home Lab

A portfolio-grade SOC lab project that combines SIEM engineering, MITRE ATT&CK-aligned attack simulation, and high-fidelity detection content in Splunk.

## English

### Project Scope
- Built an end-to-end SIEM pipeline in a virtual lab.
- Ingested Windows telemetry via Splunk Universal Forwarder.
- Enriched visibility with Sysmon and custom `inputs.conf` channels.
- Simulated attacker behaviors and validated detections with reproducible evidence.

### Architecture
- SIEM: Ubuntu Server + Splunk Enterprise (`8000`, `9997`)
- Endpoint: Windows 10 Enterprise
- Attacker VM: Kali Linux
- Telemetry: Windows Event Logs + Sysmon (`Microsoft-Windows-Sysmon/Operational`)

### ATT&CK-Mapped Scenarios
| Scenario | ATT&CK | Attack Activity | Detection Focus |
|---|---|---|---|
| Active Scanning & Brute Force | `T1595`, `T1110` | `nmap` + Hydra SMB attempts | `EventCode=4625`, threshold alerting |
| Masquerading & Privilege Escalation | `T1136.001`, `T1098` | Create `svc_backup_admin`, add to `Administrators` | `4720/4722/4724/4732` correlation + critical alert |
| Defense Evasion (Log Tampering) | `T1070.001` | `wevtutil cl Security` | `EventCode=1102` immediate alert |

### Detection Engineering Outcomes
- Timechart-based SOC monitoring views.
- Scheduled high-confidence alerts for critical behaviors.
- Validated alert logic against real attack simulation output.

### Documentation
- Full technical walkthrough (EN): [docs/project_details_EN.md](docs/project_details_EN.md)
- Tam teknik dokumantasyon (TR): [docs/project_details_TR.md](docs/project_details_TR.md)
- Screenshot evidence: `screenshots/` (25 curated and sanitized files)

---

## Turkce

### Proje Kapsami
- Sanal lab ortaminda uctan uca bir SIEM veri hatti kuruldu.
- Windows telemetrisi Splunk Universal Forwarder ile SIEM'e aktarildi.
- Sysmon ve ozel `inputs.conf` ayarlari ile gorunurluk zenginlestirildi.
- Gercek saldiri davranislari simule edilip tespit icerikleri dogrulandi.

### Mimari
- SIEM: Ubuntu Server + Splunk Enterprise (`8000`, `9997`)
- Endpoint: Windows 10 Enterprise
- Saldiri Makinesi: Kali Linux
- Telemetri: Windows Event Logs + Sysmon (`Microsoft-Windows-Sysmon/Operational`)

### ATT&CK Uyumlu Senaryolar
| Senaryo | ATT&CK | Saldiri Aksiyonu | Tespit Odagi |
|---|---|---|---|
| Ag Kesfi ve Brute Force | `T1595`, `T1110` | `nmap` + Hydra SMB denemeleri | `EventCode=4625`, esik tabanli alarm |
| Masquerading ve Ayricalik Yukseltme | `T1136.001`, `T1098` | `svc_backup_admin` olusturma ve `Administrators` grubuna ekleme | `4720/4722/4724/4732` korelasyonu + kritik alarm |
| Defense Evasion (Log Tampering) | `T1070.001` | `wevtutil cl Security` | `EventCode=1102` anlik alarm |

### Cikti ve Kazanimlar
- SOC izleme panelleri ve alarmlarinin gercek veriyle test edilmesi.
- Yalanci pozitif oranini azaltan, yuksek isabetli tespit yaklasimi.
- CV ve GitHub portfolyosu icin tekrar edilebilir teknik kanit seti.

### Dokumanlar
- English adim adim dokuman: [docs/project_details_EN.md](docs/project_details_EN.md)
- Turkce adim adim dokuman: [docs/project_details_TR.md](docs/project_details_TR.md)

