# Solution

1. Create a new user with a non-interactive shell:
   ```bash
   sudo useradd -s /sbin/nologin serviceuser
-s /sbin/nologin ensures the user cannot log in interactively.

serviceuser is the username.

Verify the user was created:

bash
Copy code
id serviceuser
Confirm the shell is set correctly:

bash
Copy code
grep serviceuser /etc/passwd
Output should show /sbin/nologin as the shell.

✅ User created successfully with a non-interactive shell.

yaml
Copy code


```text
This folder holds any related code or configs for Day 1.
(For this task, no actual code files were required.)
