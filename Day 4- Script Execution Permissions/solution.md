Solution

## Steps Taken

1. Check the current permissions of the script:
   ```bash
   ls -l /path/to/script.sh
Example output:

css
Copy code
-rw-r--r-- 1 user user 1024 Sep 19 10:00 script.sh
This shows the script is not executable.

Make the script executable for the owner:

bash
Copy code
chmod u+x /path/to/script.sh
u+x → adds execute permission for the owner only.

(Optional) Allow group or others to execute if required:

bash
Copy code
chmod go+x /path/to/script.sh
g+x → group execute

o+x → others execute

Verify new permissions:

bash
Copy code
ls -l /path/to/script.sh
Example output:

css
Copy code
-rwxr--r-- 1 user user 1024 Sep 19 10:00 script.sh
Test execution:

bash
Copy code
./script.sh
Verification
Script executes without permission errors.

Only intended users have execution rights.

✅ Script execution permissions configured successfully.

yaml
Copy code


```text
This folder holds any related code or configs for Day 4.
(For this task, the script itself can be added here if needed.)