Solution

## Steps Taken

1. Check if SELinux is installed:
   ```bash
   sestatus
If SELinux is not installed, the command will return an error.

Install SELinux packages (example for RHEL/CentOS/Fedora):

bash
Copy code
sudo yum install -y selinux-policy selinux-policy-targeted policycoreutils
For Debian/Ubuntu:

bash
Copy code
sudo apt install -y selinux-basics selinux-policy-default
Enable SELinux:

bash
Copy code
sudo setenforce 1
1 → enforcing mode

0 → permissive mode

Verify the mode:

bash
Copy code
getenforce
Output should be:

nginx
Copy code
Enforcing
Make SELinux permanent in /etc/selinux/config:

bash
Copy code
sudo nano /etc/selinux/config
Ensure the line reads:

ini
Copy code
SELINUX=enforcing
Save the file and reboot the system if required:

bash
Copy code
sudo reboot
Verification
getenforce returns Enforcing.

SELinux is installed and actively protecting the system.

✅ SELinux installation and configuration completed successfully.

yaml
Copy code

---


```text
This folder holds any related code or configs for Day 5.
(For this task, configuration files can be added here if modified.)