# Alertmanager Role

This Ansible role sets up Prometheus Alertmanager with a basic configuration to send alerts to **Spike.sh** using a webhook.

## Tasks Performed

- Creates Alertmanager config directory at `/etc/alertmanager`
- Uploads a custom `alertmanager.yml` configuration file
- Configures:
  - Alert routing rules
  - Webhook receiver (`Spike.sh`)
  - Alert grouping and repeat settings

## Configuration

- Webhook URL is hardcoded inside the playbook (edit with your own Spike.sh endpoint if needed).
- The `send_resolved: true` flag ensures resolution alerts are also sent.

## Handler

This role notifies a handler named `Restart Alertmanager` whenever the configuration changes.

## Example Usage

```yaml
- hosts: all
  become: true
  roles:
    - alertmanager
```
## 📝 Notes

- Make sure Alertmanager is installed and managed by systemd.
- The actual alert rules (e.g., for Apache/MySQL) are defined in the monitoring role.

---
