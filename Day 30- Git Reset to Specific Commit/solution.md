Solution

## Steps Taken

1. **Navigate to the repository**
   ```bash
   cd /usr/src/kodekloudrepos/blog
Check commit history

bash
Copy code
git log --oneline --graph
Verified there are multiple commits, including the one with message add data.txt file.

Find the commit hash for add data.txt file

bash
Copy code
git log --oneline | grep "add data.txt file"
Example:

csharp
Copy code
abc1234 add data.txt file
Hard reset branch to that commit

bash
Copy code
git reset --hard abc1234
Remove later commits from history
Use an interactive rebase to keep only the initial commit and add data.txt file:

bash
Copy code
git rebase -i --root
Mark all commits after add data.txt file as drop.

Force push cleaned history to remote

bash
Copy code
git push origin master --force
Verification

bash
Copy code
git log --oneline
Output shows only:

sql
Copy code
abc1234 add data.txt file
7890def initial commit
✅ The repository now has only two commits in its history.

bash
Copy code

---

### 📝 `Day30/code/reset_to_commit.sh`
```bash
#!/bin/bash
# Day 30: Reset repo history to only two commits (initial + add data.txt file)

set -e

cd /usr/src/kodekloudrepos/blog

# Find commit hash for "add data.txt file"
commit_hash=$(git log --oneline | grep "add data.txt file" | awk '{print $1}' | head -n 1)

if [ -z "$commit_hash" ]; then
  echo "❌ Error: Commit with message 'add data.txt file' not found."
  exit 1
fi

echo "✅ Found commit: $commit_hash"

# Reset to that commit
git reset --hard "$commit_hash"

# Clean up commit history interactively (keeping only initial + add data.txt file)
# This requires manual confirmation in interactive editor
# Alternative non-interactive approach:
git rebase -i --root

# Force push cleaned history
git push origin master --force

echo "🎉 Repo cleaned: Only initial commit + add data.txt file remain."