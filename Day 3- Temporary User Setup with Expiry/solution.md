Solution

## Steps Taken
1. Create a new user with an expiry date (e.g., 7 days from today):
   ```bash
   sudo useradd -e $(date -d "+7 days" +%Y-%m-%d) tempuser
-e specifies the expiry date in YYYY-MM-DD format.

tempuser is the username.

Set a password for the user:

bash
Copy code
sudo passwd tempuser
Verify the expiry date:

bash
Copy code
sudo chage -l tempuser
Example output:

pgsql
Copy code
Last password change                                    : Sep 19, 2025
Password expires                                        : never
Account expires                                         : Sep 26, 2025
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7
Test login as the user before expiry:

bash
Copy code
su - tempuser
After expiry date, login attempt should fail with:

arduino
Copy code
This account is currently not available.
Verification
Confirmed the user was created with an expiry date.

Verified that login is possible before expiry and blocked after expiry.

✅ Temporary user setup with expiry date completed successfully.

yaml
Copy code

---


```text
This folder holds any related code or configs for Day 3.
(For this task, no actual code files were required.)