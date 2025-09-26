Solution

## Steps Taken

1. Navigate to the repo:
   ```bash
   cd /usr/src/kodekloudrepos/games
Add the new remote:

bash
Copy code
git remote add dev_games /opt/xfusioncorp_games.git
Copy the required file:

bash
Copy code
cp /tmp/index.html .
Stage and commit the file:

bash
Copy code
git add index.html
git commit -m "Add index.html file from /tmp to master branch"
Push master branch to the new remote:

bash
Copy code
git push dev_games master
Verification
Run git remote -v to confirm dev_games is added.

Check git log to verify commit with index.html.

Ensure push to dev_games remote succeeds.

✅ New remote added, file committed, and pushed successfully.

yaml
Copy code

---

### 📝 `Day26/code/git_remote_update.sh`
```bash
#!/bin/bash
# Day 26: Git Remote Update and Push (Games Project)

set -e

# Navigate to repo
cd /usr/src/kodekloudrepos/games || exit 1

# Add new remote
git remote add dev_games /opt/xfusioncorp_games.git

# Copy index.html into repo
cp /tmp/index.html .

# Stage and commit
git add index.html
git commit -m "Add index.html file from /tmp to master branch"

# Push master branch to dev_games remote
git push dev_games master