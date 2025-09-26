# Day 20: Deploy PHP Application with Nginx + PHP-FPM

## Scenario
The Nautilus application development team is preparing to launch a new PHP-based application.  
They want to deploy it on Nautilus infrastructure in Stratos DC, specifically on **App Server 3**.  

The requirements are:

1. Install **Nginx** on App Server 3 and configure it to:
   - Listen on **port 8091**
   - Use **/var/www/html** as the document root  

2. Install **PHP-FPM version 8.1** on App Server 3 and configure it to:
   - Use the unix socket: `/var/run/php-fpm/default.sock`
   - Ensure parent directories exist  

3. Configure **PHP-FPM and Nginx** to work together.  

4. Test the setup using:
   ```bash
   curl http://stapp03:8091/index.php
