# Application Production Support - Advanced Linux Admin Commands

## Overview
This repository contains **advanced Linux administration commands** crucial for **Application Production Support**. These commands help in troubleshooting, monitoring, security hardening, and performance tuning, often encountered in **technical interviews**.

---

## **System Information & Performance Monitoring**
### 1. Display detailed CPU and memory usage
```sh
top -o %CPU  # Sort by CPU usage
htop  # Interactive monitoring (if installed)
```

### 2. Find top memory-consuming processes
```sh
ps aux --sort=-%mem | head -10
```

### 3. Show disk I/O statistics
```sh
iostat -x 1 5  # Install sysstat if not available
```

### 4. Check real-time system performance
```sh
vmstat 1 10
```

### 5. Monitor network activity in real-time
```sh
nload  # If installed
iftop -i eth0  # For interface-specific monitoring
```

---

## **User & Permission Management**
### 6. Check last login of all users
```sh
lastlog
```

### 7. Lock and unlock a user account
```sh
sudo passwd -l username  # Lock
sudo passwd -u username  # Unlock
```

### 8. Find files with specific permissions (e.g., SUID)
```sh
find / -perm -4000 -type f 2>/dev/null
```

### 9. List sudo privileges for a user
```sh
sudo -l -U username
```

---

## **Networking & Troubleshooting**
### 10. Check open ports and listening services
```sh
ss -tulnp  # Alternative to netstat
```

### 11. Test network latency
```sh
ping -c 5 google.com
```

### 12. Trace packet route to a destination
```sh
traceroute google.com
```

### 13. Capture network traffic (requires root)
```sh
tcpdump -i eth0 -c 100 -w capture.pcap
```

### 14. Test remote port connectivity
```sh
nc -zv 192.168.1.1 80  # Netcat test
```

---

## **Process & Service Management**
### 15. Find top CPU-consuming processes
```sh
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head
```

### 16. Kill a process by name
```sh
pkill -9 process_name
```

### 17. Restart a crashed service automatically
```sh
while true; do systemctl is-active --quiet service_name || systemctl restart service_name; sleep 10; done
```

### 18. Check logs of a specific service
```sh
journalctl -u service_name --since "1 hour ago"
```

---

## **Log Management & Debugging**
### 19. Find specific error messages in logs
```sh
grep -i "error" /var/log/syslog | tail -20
```

### 20. Check kernel logs for system crashes
```sh
dmesg | tail -50
```

### 21. Monitor logs in real-time
```sh
tail -f /var/log/syslog
```

---

## **Security & Hardening**
### 22. Check failed login attempts
```sh
sudo grep "Failed password" /var/log/auth.log
```

### 23. Enable firewall and list rules
```sh
sudo ufw enable
sudo ufw status verbose
```

### 24. Block an IP address
```sh
sudo iptables -A INPUT -s 192.168.1.100 -j DROP
```

### 25. Audit user activities
```sh
ausearch -m USER_CMD --start recent
```

---

## **Backup & Disaster Recovery**
### 26. Create a compressed tar backup
```sh
tar -czvf backup.tar.gz /var/www/html
```

### 27. Restore a tar backup
```sh
tar -xzvf backup.tar.gz -C /restore_path/
```

### 28. Create a database backup (MySQL example)
```sh
mysqldump -u root -p database_name > backup.sql
```

### 29. Sync files between servers
```sh
rsync -avz /source/path/ user@remote:/destination/path/
```

---

## **Automation & Scheduling**
### 30. List all cron jobs for a user
```sh
crontab -l
```

### 31. Schedule a script to run every 5 minutes
```sh
*/5 * * * * /path/to/script.sh
```

### 32. Run a command at system startup
```sh
echo "/path/to/script.sh" >> /etc/rc.local
```

---

## **Advanced Interview Questions**
### **System Monitoring & Debugging**
1. How do you identify high CPU usage and troubleshoot it?
2. What tools can you use to analyze memory leaks on a Linux system?
3. How do you check which process is consuming the most network bandwidth?

### **Process & Job Control**
4. What is the difference between a foreground and background process in Linux?
5. How do you terminate a zombie process?

### **Storage & Filesystem Management**
6. How do you check which directory is consuming the most disk space?
7. What is an inode, and how do you check inode usage?
8. How do you recover a deleted file in Linux?

### **Security Hardening**
9. How do you secure SSH access on a production server?
10. How do you check for rootkits and malware in Linux?

### **Networking & Troubleshooting**
11. How do you debug a slow network connection on a Linux server?
12. What is the difference between TCP and UDP, and when would you use each?

### **Backup & Recovery**
13. What are the best practices for backing up a production database?
14. How do you automate backups and ensure their integrity?

---

