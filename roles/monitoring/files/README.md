# ⚠️ Prometheus Alert Rules

This file (`alert-rules.yml`) defines custom **Prometheus alerting rules** for monitoring critical system and service-level issues on your server.

These rules help Prometheus detect problems and notify Alertmanager (and then Spike.sh) to trigger alerts.

---

## 📋 Included Alerts

| Alert Name     | What It Detects                         | Severity  | Trigger Condition                     |
|----------------|------------------------------------------|-----------|----------------------------------------|
| **ApacheDown** | Apache service is not running/responding | Critical  | Apache metric missing for 1 minute     |
| **MySQLDown**  | MySQL server is down                    | Critical  | `mysql_up == 0` for 1 minute           |
| **HighCPUUsage** | CPU usage is too high                  | Warning   | CPU usage > 80% for 2 minutes          |
| **LowMemory**  | Available RAM is critically low         | Critical  | Free memory < 10% for 2 minutes        |
| **DiskFull**   | Disk is almost full                     | Warning   | Disk usage > 90% for 2 minutes         |

---

## 💬 How It Works

- These rules are written in **PromQL** (Prometheus Query Language).
- When a condition is true for the defined time (`for:`), the alert is sent to **Alertmanager**.
- Alertmanager forwards the alert to **Spike.sh** (via webhook), which triggers real-time email/phone alerts.

---

## 📂 File Path

This file is located at:
```bash
roles/monitoring/files/alert-rules.yml
```
It is copied to:

```bash
/etc/prometheus/alert-rules.yml
```
And then included in `prometheus.yml` using:

```yaml
rule_files:
  - "/etc/prometheus/alert-rules.yml"
```
--- 

## 📝 Note
You can add more alerts based on your needs (e.g., service-specific, port checks, disk I/O).


