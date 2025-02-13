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
````javascript
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


##### 3. Application Management
##### Nginx Installation and Configuration
````linux
# Install Nginx
sudo apt update
sudo apt install nginx

# Enable and start Nginx service
sudo systemctl enable nginx
sudo systemctl start nginx

# Verify service status
sudo systemctl status nginx

# Auto-Restart Nginx on Failure
sudo nano /etc/systemd/system/nginx.service

#Reload systemd:
sudo systemctl daemon-reload

````

##### 4. Networking and Security
##### Blocking all incoming traffic except SSH and HTTP.
````linux
sudo ufw default deny incoming
sudo ufw allow ssh
sudo ufw allow http
sudo ufw enable

````

##### Checking which ports are currently open 
````linux
sudo netstat -tulnp
````

##### Setting up an SSH key-based authentication
````linux
# Generate SSH key pair on client machine
ssh-keygen -t rsa -b 4096
ssh-copy-id user@remote-server


# On the remote server, disable password login:r
sudo nano /etc/ssh/sshd_config


# Disable password authentication
PasswordAuthentication no
ChallengeResponseAuthentication no

# Restart SSH service
sudo systemctl restart sshd
````
