# devOps-assignment
devOps assignment - 3
<p>
  # DevOps Assignment 3 – System Monitoring, User Management & Backup Automation

## Overview
This repository contains the implementation of system monitoring, secure user management,
and automated backup configuration as part of Assignment 3.

## Tasks Covered
- System Monitoring Setup
- User Management & Access Control
- Automated Backups for Apache & Nginx

## Tools Used
- htop, df, du, ps
- Linux user management
- Bash scripting
- Cron jobs
- Git & GitHub

## Author
Benniesh  
Fresher DevOps Engineer

## System Monitoring Setup

### Installed Tools
- htop

<img width="1280" height="768" alt="epel install" src="https://github.com/user-attachments/assets/d95179fa-f821-4e46-9b14-0bb797674c54" />

- df

<img width="751" height="202" alt="df -h" src="https://github.com/user-attachments/assets/499e44d4-4492-4590-a74d-da53d151d3c0" />

  
- du
- ps

### Commands Used
```bash
sudo yum install epel-release -y

<img width="1280" height="768" alt="epel install" src="https://github.com/user-attachments/assets/335af48b-caab-4a7d-99b9-b04141a6fb30" />


sudo yum install htop -y

<img width="1280" height="768" alt="htop" src="https://github.com/user-attachments/assets/e8c807db-e44e-4e2b-a6b1-5c3f80831e54" />

*Monitoring Commands*
htop
df -h
du -sh /var/*
ps aux --sort=-%cpu | head
ps aux --sort=-%mem | head

*For advanced logs installed nmon*

<img width="1280" height="768" alt="nmon install" src="https://github.com/user-attachments/assets/91d6c3ed-1d0d-41fd-a626-e42a3fff406c" />

---

## 📄 `task1-system-monitoring/system_monitor.sh`

```bash
#!/bin/bash

LOG_DIR="/var/log/system_monitoring"
LOG_FILE="$LOG_DIR/monitor.log"

mkdir -p $LOG_DIR

echo "===== $(date) =====" >> $LOG_FILE
df -h >> $LOG_FILE
free -m >> $LOG_FILE
top -b -n 1 | head -20 >> $LOG_FILE


*User Creation*
## User Creation

### Users Created
- sarah
- mike

### Commands Used
```bash
sudo useradd sarah
sudo useradd mike
sudo passwd sarah
sudo passwd mike

<img width="1280" height="450" alt="Username and Password" src="https://github.com/user-attachments/assets/a0d62854-6481-4c7a-ab88-9c6f334897c2" />


---

## 📄 `task2-user-management/permissions-verification.txt`

```text
drwx------ 2 sarah sarah /home/sarah/workspace
drwx------ 2 mike  mike  /home/mike/workspace

<img width="997" height="301" alt="user permission" src="https://github.com/user-attachments/assets/5ddc485a-da85-48bc-ba27-f202c4b35b2a" />

*User-Management & Password Policy*

## Password Policy

### Configuration
- Password expiry: 30 days
- Warning before expiry: 7 days

### Commands Used
```bash
sudo chage -M 30 sarah
sudo chage -M 30 mike

<img width="1280" height="377" alt="password policy check" src="https://github.com/user-attachments/assets/c8415bd3-b8ae-4aeb-872d-a180d3e2c83e" />

*Verification*
sudo chage -l sarah
sudo chage -l mike

*Password error and changed password*

<img width="1277" height="792" alt="edit pasword policy" src="https://github.com/user-attachments/assets/32193ce5-1295-43a4-ba76-38be7d1c690d" />


---

# 🔹 TASK 3: BACKUP CONFIGURATION

## 📄 `task3-backup-configuration/apache_backup.sh`

```bash
#!/bin/bash

DATE=$(date +%F)
BACKUP_FILE="/backups/apache_backup_${DATE}.tar.gz"

tar -czf $BACKUP_FILE /etc/httpd /var/www/html
tar -tzf $BACKUP_FILE > /backups/apache_verify_${DATE}.log

<img width="1280" height="377" alt="Screenshot From 2026-01-02 14-51-49" src="https://github.com/user-attachments/assets/cd8b781e-828b-47f4-9755-277f0d83a127" />

*Backup-configuration/nginx_backup.sh*

#!/bin/bash

DATE=$(date +%F)
BACKUP_FILE="/backups/nginx_backup_${DATE}.tar.gz"

tar -czf $BACKUP_FILE /etc/nginx /usr/share/nginx/html
tar -tzf $BACKUP_FILE > /backups/nginx_verify_${DATE}.log

<img width="1279" height="797" alt="Nginx backup script (Mike)" src="https://github.com/user-attachments/assets/821fd94c-a869-4fb3-9abc-58505dbfd7a1" />

0 0 * * 2 /usr/local/bin/apache_backup.sh
0 0 * * 2 /usr/local/bin/nginx_backup.sh

*Backup-configuration/sample-backup-verification.log*

/etc/httpd/httpd.conf
/var/www/html/index.html
/etc/nginx/nginx.conf
/usr/share/nginx/html/index.html

*Used WINSCP as shared folder to capture the screenshots*

<img width="1342" height="863" alt="WinSCP snap" src="https://github.com/user-attachments/assets/b7f0f3be-88e2-471b-a292-a227497e852e" />

</p>
