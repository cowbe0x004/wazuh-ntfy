## Wauzh notification to ntfy integration

This is a custom integration script for pushing alert notifications to ntfy.

### Installation
1. Download the *custom-ntfy* file and put it in */var/ossec/integrations/custom-ntfy*.
2. Update script permission.
```
chmod 755 /var/ossec/integrations/custom-ntfy
chown root:wazuh /var/ossec/integrations/custom-ntfy
```
3. Add the integration entry in */var/ossec/etc/ossec.conf*. This will alert on rule level 10 or above.
```
<integration>
  <name>custom-ntfy</name>
  <hook_url>https://<NTFY_DOMAIN>/<TOPIC></hook_url>
  <alert_format>json</alert_format>
  <level>10</level>
</integration>
```
 - This page has all the available options: https://documentation.wazuh.com/current/user-manual/reference/ossec-conf/integration.html \
4. Restart wazuh manager.
```
systemctl restart wazuh-manager
```
---
* These fields from an alert will be included in the notification. If a field is empty/null, it won't be included in the notification. More fields can be found by looking at the alerts in */var/ossec/logs/alerts/alerts.json*.
    - Timestamp
    - Host
    - Description
    - Level
    - User
    - Source IP
    - Command

---  
__Credit:__ \
https://github.com/joaopsoliveira03/wazuh-ntfy  
https://wazuh.com/blog/how-to-integrate-external-software-using-integrator/
