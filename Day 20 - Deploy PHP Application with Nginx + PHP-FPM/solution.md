📝 `Day20/solution.md`
```markdown
# Solution

## Steps Taken

1. **Install Nginx**
   ```bash
   sudo yum install -y nginx   # (or apt install nginx on Debian/Ubuntu)
Configure Nginx

Open the config:

bash
Copy code
sudo nano /etc/nginx/conf.d/app.conf
Add:

nginx
Copy code
server {
    listen 8091;
    server_name stapp03;

    root /var/www/html;
    index index.php index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include fastcgi_params;
        fastcgi_pass unix:/var/run/php-fpm/default.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }
}
Install PHP-FPM 8.1

bash
Copy code
sudo yum install -y php-fpm php-cli php-mysqlnd php-common
or on Debian/Ubuntu:

bash
Copy code
sudo apt install -y php8.1-fpm
Configure PHP-FPM

Create socket directory:

bash
Copy code
sudo mkdir -p /var/run/php-fpm
Edit the pool config (usually in /etc/php-fpm.d/www.conf or /etc/php/8.1/fpm/pool.d/www.conf):

ini
Copy code
listen = /var/run/php-fpm/default.sock
listen.owner = nginx
listen.group = nginx
listen.mode = 0660
Set correct permissions

bash
Copy code
sudo chown -R nginx:nginx /var/www/html
Start and enable services

bash
Copy code
sudo systemctl enable --now php-fpm
sudo systemctl enable --now nginx
Test

bash
Copy code
curl http://stapp03:8091/index.php
Expected: PHP output rendered correctly.

Verification
curl returned valid PHP content.

Both index.php and info.php load via port 8091.

✅ PHP-FPM + Nginx setup completed successfully.

bash
Copy code

---

### 📝 `Day20/code/setup_php_nginx.sh`
```bash
#!/bin/bash
# Day 20: Setup PHP-FPM + Nginx for Nautilus Project

set -e

# Install nginx and PHP-FPM 8.1
if command -v apt >/dev/null 2>&1; then
    sudo apt update
    sudo apt install -y nginx php8.1-fpm
else
    sudo yum install -y epel-release
    sudo yum install -y nginx php-fpm php-cli php-mysqlnd php-common
fi

# Create socket directory
sudo mkdir -p /var/run/php-fpm

# Configure PHP-FPM socket (adjust file path based on OS)
POOL_CONF=$(find /etc -name "www.conf" | grep fpm | head -n1)
sudo sed -i 's|^listen = .*|listen = /var/run/php-fpm/default.sock|' "$POOL_CONF"
sudo sed -i 's|^;listen.owner = .*|listen.owner = nginx|' "$POOL_CONF"
sudo sed -i 's|^;listen.group = .*|listen.group = nginx|' "$POOL_CONF"
sudo sed -i 's|^;listen.mode = .*|listen.mode = 0660|' "$POOL_CONF"

# Configure Nginx
NGINX_CONF="/etc/nginx/conf.d/app.conf"
sudo tee $NGINX_CONF > /dev/null <<EOF
server {
    listen 8091;
    server_name stapp03;

    root /var/www/html;
    index index.php index.html;

    location / {
        try_files \$uri \$uri/ =404;
    }

    location ~ \.php\$ {
        include fastcgi_params;
        fastcgi_pass unix:/var/run/php-fpm/default.sock;
        fastcgi_param SCRIPT_FILENAME \$document_root\$fastcgi_script_name;
    }
}
EOF

# Ensure ownership
sudo chown -R nginx:nginx /var/www/html || true

# Restart services
sudo systemctl enable --now php-fpm
sudo systemctl enable --now nginx