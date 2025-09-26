Solution

## Steps Taken

1. **Navigate to the repository**
   ```bash
   cd /usr/src/kodekloudrepos/ecommerce
Check available stashes

bash
Copy code
git stash list
Example output:

pgsql
Copy code
stash@{0}: WIP on featureX: abc1234 update header
stash@{1}: WIP on master: def5678 update cart module
stash@{2}: WIP on bugfix: ghi9012 fix payment bug
Apply stash@{1}

bash
Copy code
git stash apply stash@{1}
Stage the restored changes

bash
Copy code
git add .
Commit changes

bash
Copy code
git commit -m "Restored changes from stash@{1}"
Push to remote

bash
Copy code
git push origin master
Verification

Run git log --oneline to confirm the new commit exists.

Run git status to ensure no pending changes.

✅ Task complete: Stash stash@{1} successfully restored, committed, and pushed.

yaml
Copy code

---

### 📝 `Day31/code/restore_stash.sh`
```bash
#!/bin/bash
# Day 31: Restore stashed changes in Git

set -e

cd /usr/src/kodekloudrepos/ecommerce

# Show stashes
git stash list

# Apply stash@{1}
git stash apply stash@{1}

# Stage and commit
git add .
git commit -m "Restored changes from stash@{1}"

# Push to origin
git push origin master

echo "✅ Stash stash@{1} restored, committed, and pushed successfully."
⚡ Update your root README.md tracker:

markdown
Copy code
| 31  | Restore Git Stash (stash@{1}) | ✅ Completed |