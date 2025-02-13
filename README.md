# Linux Assessment
##### Author: Ogomide samuel

### Tasks & Challenges
##### 1. User and Roles Management
##### Creating User Accounts and Assigning Roles
````linux
# Create the group for the developers
sudo groupadd developers

# Add the new developers and assign them to the group
for user in HypotheticalCorpDev1 HypotheticalCorpDev2 HypotheticalCorpDev3 HypotheticalCorpDev4 HypotheticalCorpDev5; do
    sudo useradd -m -G developers -s /bin/bash $user
    sudo passwd $user  #  set passwords for the new users
done
````

##### Setting Permissions for the users
````linux
sudo chown -R root:developers /var/www/project
sudo chmod -R 750 /var/www/project
````

##### Restricting SSH Access for Dev1 and Dev2
````linux
sudo nano /etc/ssh/sshd_config
DenyUsers HypotheticalCorpDev1 HypotheticalCorpDev2
sudo systemctl restart sshd
````

##### 2. System Monitoring & Performance Analysis
##### Identify the top resource-consuming process
````linux
# Check top processes by resource usage
top -b -n 1 | head -n 20

# Monitor specific process
ps aux | grep [process_name]

# Check system memory usage
free -h

# Monitor CPU usage
mpstat 1 5
````
##### Disk usage
````linux
df -h  
du -sh /var/log/*

````

##### Monitor real-time system logs
````linux
sudo tail -f /var/log/syslog
````
