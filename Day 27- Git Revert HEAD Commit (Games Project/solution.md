Solution

## Steps Taken

1. Navigate to the repository:
   ```bash
   cd /usr/src/kodekloudrepos/games
Check the commit history:

bash
Copy code
git log --oneline
Example output:

sql
Copy code
a1b2c3d (HEAD -> master) Add index.html file
1234567 Initial commit
Revert the HEAD commit:

bash
Copy code
git revert HEAD --no-edit
Amend the commit message to exactly:

nginx
Copy code
revert games
If --no-edit is used, follow with:

bash
Copy code
git commit --amend -m "revert games"
Verify commit history:

bash
Copy code
git log --oneline
Expected:

sql
Copy code
7f8e9d0 (HEAD -> master) revert games
a1b2c3d Add index.html file
1234567 Initial commit
Push changes if required:

bash
Copy code
git push origin master
Verification
Latest commit message is revert games.

Repo state matches before the last commit (while preserving history).

✅ HEAD successfully reverted.

yaml
Copy code

---

### 📝 `Day27/code/git_revert_head.sh`
```bash
#!/bin/bash
# Day 27: Git Revert HEAD Commit (Games Project)

set -e

# Navigate to repo
cd /usr/src/kodekloudrepos/games || exit 1

# Revert latest commit
git revert HEAD --no-edit

# Amend commit message to required format
git commit --amend -m "revert games"