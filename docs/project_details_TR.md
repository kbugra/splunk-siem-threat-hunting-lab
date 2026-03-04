# Proje Detaylari (TR)

Bu dokuman, yuksek sinyal degerine sahip ekran goruntuleriyle hazirlanmis ozet teknik yurutumu sunar.

## Adim 1
![01_splunk_download_package.png](<../screenshots/01_splunk_download_package.png>)
**Yapilan islem:** Splunk Enterprise paketi Ubuntu uzerine `wget` komutuyla indirildi ve basariyla kaydedildi.

## Adim 2
![02_splunk_install_dpkg.png](<../screenshots/02_splunk_install_dpkg.png>)
**Yapilan islem:** Indirilen `.deb` paketi `sudo dpkg -i` ile kuruldu.

## Adim 3
![03_splunk_admin_account_setup.png](<../screenshots/03_splunk_admin_account_setup.png>)
**Yapilan islem:** Ilk `splunk start --accept-license` calistirmasinda administrator hesap olusturma ekranina ulasildi.

## Adim 4
![04_splunk_service_started.png](<../screenshots/04_splunk_service_started.png>)
**Yapilan islem:** Splunk baslangic kontrolleri tamamlandi ve web arayuzunun erisilebilir oldugu goruldu.

## Adim 5
![05_splunk_admin_home.png](<../screenshots/05_splunk_admin_home.png>)
**Yapilan islem:** Splunk web arayuzu acilarak admin dashboard ve ayar erisimi dogrulandi.

## Adim 6
![06_splunk_configure_receiver_9997.png](<../screenshots/06_splunk_configure_receiver_9997.png>)
**Yapilan islem:** Splunk receive konfigurasyonunda forwarder verisi icin `9997` portu girildi.

## Adim 7
![07_splunk_receiver_9997_enabled.png](<../screenshots/07_splunk_receiver_9997_enabled.png>)
**Yapilan islem:** Splunk, receiving port `9997` kaydini basarili ve etkin olarak gosterdi.

## Adim 8
![08_uf_setup_indexer_target.png](<../screenshots/08_uf_setup_indexer_target.png>)
**Yapilan islem:** Universal Forwarder kurulumunda hedef indexer IP ve port (`192.168.1.184:9997`) olarak ayarlandi.

## Adim 9
![09_windows_uf_service_running.png](<../screenshots/09_windows_uf_service_running.png>)
**Yapilan islem:** Windows Services ekraninda `SplunkForwarder` servisinin calistigi teyit edildi.

## Adim 10
![10_uf_inputs_core_logs.png](<../screenshots/10_uf_inputs_core_logs.png>)
**Yapilan islem:** Splunk Search ekraninda host dagilimi (`ubuntu`, `windows`, `localhost`) incelenerek telemetri akisinin geldigi dogrulandi.

## Adim 11
![11_splunk_windows_ingestion_validation.png](<../screenshots/11_splunk_windows_ingestion_validation.png>)
**Yapilan islem:** Windows endpoint ag bilgileri `ipconfig` ile toplandi.

## Adim 12
![12_kali_nmap_recon_preparation.png](<../screenshots/12_kali_nmap_recon_preparation.png>)
**Yapilan islem:** Kali terminalinde aktif kesif komutu hazirlandi: `nmap -sS -A -p- 192.168.1.173`.

## Adim 13
![13_kali_hydra_smb_bruteforce.png](<../screenshots/13_kali_hydra_smb_bruteforce.png>)
**Yapilan islem:** Hedef `192.168.1.173` uzerine Hydra ile SMB brute-force denemesi yapildi.

## Adim 14
![14_splunk_failed_logon_detection_4625.png](<../screenshots/14_splunk_failed_logon_detection_4625.png>)
**Yapilan islem:** Splunkta `EventCode=4625` sorgusu ile Windows Security loglarindaki basarisiz girisler listelendi.

## Adim 15
![15_splunk_4625_timechart_dashboard.png](<../screenshots/15_splunk_4625_timechart_dashboard.png>)
**Yapilan islem:** Basarisiz giris aktiviteleri `timechart count` ile gorsellestirildi.

## Adim 16
![16_splunk_bruteforce_alert_configuration.png](<../screenshots/16_splunk_bruteforce_alert_configuration.png>)
**Yapilan islem:** `Critical: SMB Brute Force Detected` alarm ayarlari acildi ve esik (>2) konfigure edildi.

## Adim 17
![17_windows_sysmon_installation.png](<../screenshots/17_windows_sysmon_installation.png>)
**Yapilan islem:** Windows uzerinde `Sysmon64.exe -accepteula -i -n` komutuyla Sysmon kuruldu.

## Adim 18
![18_uf_sysmon_channel_configuration.png](<../screenshots/18_uf_sysmon_channel_configuration.png>)
**Yapilan islem:** Forwarder `inputs` dosyasina `Microsoft-Windows-Sysmon/Operational` log kanali eklendi.

## Adim 19
![19_windows_local_admin_creation_simulation.png](<../screenshots/19_windows_local_admin_creation_simulation.png>)
**Yapilan islem:** Windows ortaminda local hesap olusturma ve admin gruba ekleme komutlari calistirildi (`net user` + `net localgroup`).

## Adim 20
![20_splunk_svc_backup_admin_hunt.png](<../screenshots/20_splunk_svc_backup_admin_hunt.png>)
**Yapilan islem:** Splunkta `svc_backup_admin` odakli av sorgusu ile hesap ve yetki olaylari goruntulendi.

## Adim 21
![21_splunk_privilege_query_4720_4732.png](<../screenshots/21_splunk_privilege_query_4720_4732.png>)
**Yapilan islem:** `EventCode=4720 OR EventCode=4732` sorgusu kosuldu ve alarm veya rapor kaydetme menusu acildi.

## Adim 22
![22_splunk_privilege_escalation_alert.png](<../screenshots/22_splunk_privilege_escalation_alert.png>)
**Yapilan islem:** `Critical: Unauthorized Local Account Creation & Privilege Escalation` alarm konfigurasyonu tamamlandi.

## Adim 23
![23_windows_security_log_cleared_command.png](<../screenshots/23_windows_security_log_cleared_command.png>)
**Yapilan islem:** Defense-evasion simulasyonu icin Windows uzerinde `wevtutil cl Security` komutu calistirildi.

## Adim 24
![24_splunk_eventcode_1102_detection.png](<../screenshots/24_splunk_eventcode_1102_detection.png>)
**Yapilan islem:** Splunkta `EventCode=1102` (security log temizleme) olayi tespit edildi ve kaydetme secenekleri acildi.

## Adim 25
![25_splunk_defense_evasion_alert.png](<../screenshots/25_splunk_defense_evasion_alert.png>)
**Yapilan islem:** `Critical: Defense Evasion (Security Event Logs Cleared)` alarmi Splunkta konfigure edildi.

