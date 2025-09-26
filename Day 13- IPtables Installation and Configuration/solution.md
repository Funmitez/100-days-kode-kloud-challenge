 Solution

## Steps Taken

1. **Install iptables**
   ```bash
   sudo yum install -y iptables iptables-services   # RHEL/CentOS
   sudo apt install -y iptables-persistent          # Debian/Ubuntu
Flush existing rules (clean state)

bash
Copy code
sudo iptables -F
Allow SSH (22), HTTP (80), and HTTPS (443)

bash
Copy code
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT
Allow localhost and established connections

bash
Copy code
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
Drop everything else

bash
Copy code
sudo iptables -A INPUT -j DROP
Save rules

bash
Copy code
sudo service iptables save          # RHEL/CentOS
sudo netfilter-persistent save      # Debian/Ubuntu
Enable iptables on boot

bash
Copy code
sudo systemctl enable iptables
sudo systemctl start iptables
Verify

bash
Copy code
sudo iptables -L -n -v
Output should show ACCEPT for ports 22, 80, 443 and DROP for all others.

Verification
Able to connect via SSH, HTTP, HTTPS.

All other ports blocked.

✅ IPtables installation and configuration completed successfully.

pgsql
Copy code

---

### 📝 `Day13/code/iptables_setup.sh`
```bash
#!/bin/bash
# Day 13: IPtables Installation and Configuration

set -e

# Install iptables
if command -v yum >/dev/null 2>&1; then
    sudo yum install -y iptables iptables-services
else
    sudo apt update
    sudo apt install -y iptables iptables-persistent
fi

# Flush old rules
sudo iptables -F

# Allow SSH, HTTP, HTTPS
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# Allow loopback and established connections
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Drop everything else
sudo iptables -A INPUT -j DROP

# Save rules
if command -v service >/dev/null 2>&1; then
    sudo service iptables save || true
fi
if command -v netfilter-persistent >/dev/null 2>&1; then
    sudo netfilter-persistent save || true
fi

# Enable on boot
sudo systemctl enable iptables || true