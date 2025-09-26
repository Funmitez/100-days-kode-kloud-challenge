 Solution

## Steps Taken
1. Check the current file permissions:
   ```bash
   ls -l /path/to/file
Example output:

bash
Copy code
-rw------- 1 root root 1024 Sep 19 10:00 /path/to/file
This shows only the owner (root) can read/write.

Change permissions to allow the user to read the file:

bash
Copy code
sudo chmod 644 /path/to/file
6 → read & write for owner

4 → read-only for group

4 → read-only for others

Verify new permissions:

bash
Copy code
ls -l /path/to/file
Output should be:

bash
Copy code
-rw-r--r-- 1 root root 1024 Sep 19 10:00 /path/to/file
Test access by switching to the user and reading the file:

bash
Copy code
sudo -u <username> cat /path/to/file
Verification
The user is now able to read the file without being given unnecessary write or execute permissions.

✅ File permission issue resolved.

yaml
Copy code

---


```text
This folder holds any related code or configs for Day 2.
(For this task, no actual code files were required.)
