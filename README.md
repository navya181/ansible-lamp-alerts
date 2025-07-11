# 🚀 Automated LAMP Stack Deployment with Monitoring & Alerting using Ansible

## 📖 Project Overview

This project automates the setup of a LAMP (Linux, Apache, MySQL, PHP) stack on an Ubuntu server using **Ansible**.  
It also includes real-time monitoring using **Prometheus Node Exporter** and alerting integration with **Spike.sh** via **Alertmanager**.

Designed for beginner-to-intermediate DevOps learners, this project demonstrates how to automate infrastructure, monitor key services, and trigger phone/email alerts when issues occur.

---

## ✨ Features

- Installs and configures:
  - Apache Web Server
  - MySQL Database Server (with root password)
  - PHP and required modules
- Sets up UFW firewall rules for secure access
- Installs Prometheus Node Exporter for system metrics
- Configures Prometheus Alertmanager with alert rules
- Integrates real-time alerts with **Spike.sh** (email/phone call/SMS)
- Automates SSH setup with key-based access

---

## 🛠️ Tools Used

- **Ansible** – Automation engine
- **Ubuntu Server** – Installed in a local Virtual Machine (VM)
- **Apache2**, **MySQL**, **PHP**
- **UFW** – Uncomplicated Firewall
- **Prometheus**, **Alertmanager**
- **Spike.sh** – Alert notifications (email/phone/SMS)
- **VS Code** – Editor used to write and manage Ansible scripts

---

## 📁 Project Structure

```bash
ansible-lamp-monitor-alert/
├── output_images/                 # Playbook execution & alert screenshots
│   ├── playbook-run-success.png
│   ├── prometheus-mysql-down.png
│   ├── alertmanager-mysql-down.png
│   ├── spike-web-triggered.png
│   ├── spike-email-alert.png
│   ├── spike-sh-call.png
│   ├── mysql-started.png
│   ├── prometheus-resolved.png
│   └── spike-alert-resolved.png
├── inventory/
│   └── hosts                      # Inventory file for target hosts
├── handlers/
│   └── main.yml                   # Handlers to restart services
├── roles/
│   ├── alertmanager/
│   │   └── tasks/main.yml
│   ├── apache/                    # Apache setup
│   │   └── tasks/main.yml
│   ├── firewall/
│   │   └── tasks/main.yml
│   ├── monitoring/
│   │   ├── files/alert-rules.yml
│   │   └── tasks/main.yml
│   ├── mysql/
│   │   └── tasks/main.yml
│   ├── php/
│   │   └── tasks/main.yml
│   └── ssh/
│       └── tasks/main.yml
├── ansible-playbook.yml          # Main playbook
```
## 🚀 How to Use

### 1. Clone the Repository

```bash
git clone https://github.com/navya181/ansible-lamp-alerts.git
cd ansible-lamp-alert
``` 

### 2. Update Inventory File
Edit the inventory file with your server details:
```ini
[webservers]
<your-server-ip> ansible_user=your_username ansible_ssh_private_key_file=/home/your_username/.ssh/ansible_key 
``` 

### 3. Run the Playbook

```bash
ansible-playbook -i inventory/hosts ansible-playbook.yml --ask-become-pass
``` 
✅ Use --ask-become-pass if your remote user requires sudo privileges (e.g., on Ubuntu).
This flag will prompt for the sudo password during execution.

---

## 📊 Monitoring & Alerting Access

- **Prometheus Metrics**  
  `http://<your-server-ip>:9100/metrics`

- **Alertmanager Dashboard**  
  `http://<your-server-ip>:9093`

- **Alerts**  
  Triggered by Prometheus alert rules and sent to **Spike.sh** via webhook.  
  You’ll receive real-time notifications through **email**, **SMS**, and **phone call** for service failures like Apache/MySQL downtime.
  
---
## 📸 Example Alerts & Monitoring Outputs

Below are examples demonstrating how the alerting system works when MySQL goes down:

### ✅ Successful Playbook Run

![Playbook Success](./output_images/playbook-run-success.png)

### 📉 Prometheus Alert Triggered

![Prometheus Alert](./output_images/prometheus-mysql-down.png)

### 🚨 Alertmanager Display

![Alertmanager](./output_images/alertmanager-mysql-down.png)

### 🧾 Spike.sh Web Incident

![Spike.sh Web Incident](./output_images/spike-web-triggered.png)

### 📬 Spike.sh Email Alert

![Spike.sh Email](./output_images/spike-email-alert.png)

### ✅ Phone Call Notification (Spike.sh)

![Phone Call](./output_images/spike-sh-call.png)

### 🟢 Service Restored

- ✅ MySQL started again:

  ![MySQL Started](./output_images/mysql-started.png)

- ✅ Prometheus shows alert as resolved:

  ![Resolved Alerts](./output_images/prometheus-resolved.png)

### 📨 Spike.sh Alert Resolved

![Spike.sh Resolved](./output_images/spike-alert-resolved.png)

---

## 🔐 Security Notes

- Passwords (like the MySQL root password) are hardcoded for demonstration purposes.  
  ➤ Use **Ansible Vault** to encrypt sensitive data in real-world projects.

- Ensure that your SSH key (`~/.ssh/ansible_key.pub`) exists and is securely configured on your control machine.

---

## 👤 Author

**Navya Sattineni**  
Feel free to connect on [LinkedIn](https://www.linkedin.com/in/navya-ratna-kumari-sattineni-a03986265/)
