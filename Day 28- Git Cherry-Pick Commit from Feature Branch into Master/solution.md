Solution

## Steps Taken

1. **Navigate to the repository**
   ```bash
   cd /usr/src/kodekloudrepos/demo
List branches and checkout master

bash
Copy code
git branch
git checkout master
Find the commit hash with the message "Update info.txt" from the feature branch

bash
Copy code
git log feature --oneline | grep "Update info.txt"
Example output:

nginx
Copy code
a1b2c3d Update info.txt
Cherry-pick the commit into master

bash
Copy code
git cherry-pick a1b2c3d
Resolve conflicts if any (edit files, then run):

bash
Copy code
git add <resolved_file>
git cherry-pick --continue
Push changes to origin

bash
Copy code
git push origin master
Verification
git log master now shows the commit Update info.txt.

The commit history of feature remains unchanged.

✅ Task completed: Specific commit successfully merged from feature into master using cherry-pick.

bash
Copy code

---

### 📝 `Day28/code/cherry_pick.sh`
```bash
#!/bin/bash
# Day 28: Cherry-pick commit from feature branch into master

set -e

cd /usr/src/kodekloudrepos/demo

# Ensure we are on master
git checkout master

# Get commit hash with message "Update info.txt"
commit_hash=$(git log feature --oneline | grep "Update info.txt" | awk '{print $1}' | head -n 1)

if [ -z "$commit_hash" ]; then
  echo "Error: Commit with message 'Update info.txt' not found on feature branch."
  exit 1
fi

echo "Cherry-picking commit: $commit_hash"

# Cherry-pick into master
git cherry-pick "$commit_hash" || {
  echo "Resolve conflicts, then run: git cherry-pick --continue"
  exit 1
}

# Push updated master branch
git push origin master

echo "✅ Cherry-pick completed and pushed to origin/master."