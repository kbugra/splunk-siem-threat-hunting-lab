# Project Details (EN)

This document is a curated technical walkthrough with high-signal screenshot evidence.

## Step 1
![01_splunk_download_package.png](<../screenshots/01_splunk_download_package.png>)
**What was done:** Splunk Enterprise package was downloaded to Ubuntu with a `wget` command and saved successfully.

## Step 2
![02_splunk_install_dpkg.png](<../screenshots/02_splunk_install_dpkg.png>)
**What was done:** Splunk was installed from the downloaded `.deb` package using `sudo dpkg -i`.

## Step 3
![03_splunk_admin_account_setup.png](<../screenshots/03_splunk_admin_account_setup.png>)
**What was done:** Initial `splunk start --accept-license` run reached the administrator account setup prompt.

## Step 4
![04_splunk_service_started.png](<../screenshots/04_splunk_service_started.png>)
**What was done:** Splunk startup completed prerequisite checks and reported that the web interface is available.

## Step 5
![05_splunk_admin_home.png](<../screenshots/05_splunk_admin_home.png>)
**What was done:** Splunk web UI was opened and admin dashboard/settings access was verified.

## Step 6
![06_splunk_configure_receiver_9997.png](<../screenshots/06_splunk_configure_receiver_9997.png>)
**What was done:** In Splunk receive configuration, port `9997` was entered for inbound forwarder data.

## Step 7
![07_splunk_receiver_9997_enabled.png](<../screenshots/07_splunk_receiver_9997_enabled.png>)
**What was done:** Splunk confirmed receiving port `9997` as saved and enabled.

## Step 8
![08_uf_setup_indexer_target.png](<../screenshots/08_uf_setup_indexer_target.png>)
**What was done:** Universal Forwarder setup was configured with target indexer IP and port (`192.168.1.184:9997`).

## Step 9
![09_windows_uf_service_running.png](<../screenshots/09_windows_uf_service_running.png>)
**What was done:** Windows Services console confirmed that `SplunkForwarder` service is running.

## Step 10
![10_uf_inputs_core_logs.png](<../screenshots/10_uf_inputs_core_logs.png>)
**What was done:** Splunk Search view displayed host distribution (`ubuntu`, `windows`, `localhost`) to validate incoming telemetry.

## Step 11
![11_splunk_windows_ingestion_validation.png](<../screenshots/11_splunk_windows_ingestion_validation.png>)
**What was done:** Windows endpoint network details were collected with `ipconfig`.

## Step 12
![12_kali_nmap_recon_preparation.png](<../screenshots/12_kali_nmap_recon_preparation.png>)
**What was done:** Kali terminal prepared active reconnaissance command: `nmap -sS -A -p- 192.168.1.173`.

## Step 13
![13_kali_hydra_smb_bruteforce.png](<../screenshots/13_kali_hydra_smb_bruteforce.png>)
**What was done:** Hydra SMB brute-force attempt was executed against target `192.168.1.173`.

## Step 14
![14_splunk_failed_logon_detection_4625.png](<../screenshots/14_splunk_failed_logon_detection_4625.png>)
**What was done:** Splunk query with `EventCode=4625` returned failed logon events from Windows Security logs.

## Step 15
![15_splunk_4625_timechart_dashboard.png](<../screenshots/15_splunk_4625_timechart_dashboard.png>)
**What was done:** Failed logon activity was visualized using `timechart count` in Splunk.

## Step 16
![16_splunk_bruteforce_alert_configuration.png](<../screenshots/16_splunk_bruteforce_alert_configuration.png>)
**What was done:** `Critical: SMB Brute Force Detected` alert configuration was opened and tuned (threshold > 2).

## Step 17
![17_windows_sysmon_installation.png](<../screenshots/17_windows_sysmon_installation.png>)
**What was done:** Sysmon installation command (`Sysmon64.exe -accepteula -i -n`) executed successfully on Windows.

## Step 18
![18_uf_sysmon_channel_configuration.png](<../screenshots/18_uf_sysmon_channel_configuration.png>)
**What was done:** Forwarder `inputs` file was updated to include `Microsoft-Windows-Sysmon/Operational` log channel.

## Step 19
![19_windows_local_admin_creation_simulation.png](<../screenshots/19_windows_local_admin_creation_simulation.png>)
**What was done:** Local account creation and admin group assignment commands were run on Windows (`net user` + `net localgroup`).

## Step 20
![20_splunk_svc_backup_admin_hunt.png](<../screenshots/20_splunk_svc_backup_admin_hunt.png>)
**What was done:** Splunk hunt query for `svc_backup_admin` showed related account and privilege events.

## Step 21
![21_splunk_privilege_query_4720_4732.png](<../screenshots/21_splunk_privilege_query_4720_4732.png>)
**What was done:** Splunk query for `EventCode=4720 OR EventCode=4732` was run and Save menu opened for alert/report creation.

## Step 22
![22_splunk_privilege_escalation_alert.png](<../screenshots/22_splunk_privilege_escalation_alert.png>)
**What was done:** `Critical: Unauthorized Local Account Creation & Privilege Escalation` alert configuration was completed.

## Step 23
![23_windows_security_log_cleared_command.png](<../screenshots/23_windows_security_log_cleared_command.png>)
**What was done:** Defense-evasion simulation command `wevtutil cl Security` was executed on Windows.

## Step 24
![24_splunk_eventcode_1102_detection.png](<../screenshots/24_splunk_eventcode_1102_detection.png>)
**What was done:** Splunk detected `EventCode=1102` (security log cleared) and save options were opened.

## Step 25
![25_splunk_defense_evasion_alert.png](<../screenshots/25_splunk_defense_evasion_alert.png>)
**What was done:** `Critical: Defense Evasion (Security Event Logs Cleared)` alert was configured in Splunk.
