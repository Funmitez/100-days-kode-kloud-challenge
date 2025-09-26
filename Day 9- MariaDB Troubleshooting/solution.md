Solution

## Steps Taken

1. **Check service status**
   ```bash
   sudo systemctl status mariadb
Found service in failed state.

Inspect logs for errors

bash
Copy code
sudo journalctl -xeu mariadb
Common issues found:

Misconfigured my.cnf file

Wrong socket path

Data directory permission errors

Fix configuration (example)

Open /etc/my.cnf or /etc/mysql/mariadb.conf.d/50-server.cnf:

bash
Copy code
sudo nano /etc/my.cnf
Ensure correct socket:

ini
Copy code
[mysqld]
socket=/var/lib/mysql/mysql.sock
datadir=/var/lib/mysql
Ensure /var/lib/mysql owned by mysql:mysql:

bash
Copy code
sudo chown -R mysql:mysql /var/lib/mysql
Restart MariaDB

bash
Copy code
sudo systemctl restart mariadb
Enable on boot

bash
Copy code
sudo systemctl enable mariadb
Verify

bash
Copy code
mysql -u root -p -e "SELECT VERSION();"
Output shows MariaDB version confirming database is running.

Verification
systemctl status mariadb shows active (running).

Able to connect with mysql -u root -p.

✅ MariaDB service fixed and running correctly.

yaml
Copy code

---

### 📝 `Day09/code/mariadb_fix.sh`
```bash
#!/bin/bash
# Day 9: MariaDB Troubleshooting

set -e

# Check service status
sudo systemctl status mariadb || true

# Ensure correct ownership of data directory
sudo chown -R mysql:mysql /var/lib/mysql

# Restart MariaDB
sudo systemctl restart mariadb

# Enable MariaDB on boot
sudo systemctl enable mariadb

# Verify
mysql -u root -p -e "SELECT VERSION();" || echo "Login check required"