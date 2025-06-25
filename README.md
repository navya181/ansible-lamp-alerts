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
├── inventory/
│ └── hosts # Inventory file for target hosts
├── handlers/
│ └── main.yml # Handlers to restart services
├── roles/
│ ├── alertmanager/           
│ │ └── tasks/main.yml
│ ├── apache/ # Apache setup
│ │ └── tasks/main.yml
│ ├── firewall/                
│ │ └── tasks/main.yml
│ ├── monitoring/             
│ │ ├── files/alert-rules.yml
│ │ └── tasks/main.yml
│ ├── mysql/                  
│ │ └── tasks/main.yml
│ ├── php/                 
│ │ └── tasks/main.yml
│ └── ssh/                   
│ └── tasks/main.yml
├── ansible-playbook.yml        

- **Ansible** – Automation engine
- **Ubuntu Server** – Installed in a local Virtual Machine (VM)
- **Apache2**, **MySQL**, **PHP**
- **UFW** – Uncomplicated Firewall
- **Prometheus**, **Alertmanager**
- **Spike.sh** – Alert notifications (email/phone/SMS)
- **VS Code** – Editor used to write and manage Ansible scripts

---

## 📁 Project Structure

ansible-lamp-monitor-alert/
