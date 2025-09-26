Solution

## Steps Taken

1. Go to the repo location:
   ```bash
   cd /usr/src/kodekloudrepos/cluster
Check the current branch:

bash
Copy code
git branch
Create and switch to a new branch xfusion:

bash
Copy code
git checkout -b xfusion
Copy the file /tmp/index.html into the repo:

bash
Copy code
cp /tmp/index.html .
Stage and commit the new file:

bash
Copy code
git add index.html
git commit -m "Add index.html file from /tmp into xfusion branch"
Push the new branch to origin:

bash
Copy code
git push origin xfusion
Switch back to master:

bash
Copy code
git checkout master
Merge the xfusion branch into master:

bash
Copy code
git merge xfusion
Push updated master to origin:

bash
Copy code
git push origin master
Verification
git log --oneline --graph --all shows index.html commit on both xfusion and master.

git branch -r confirms both branches pushed to origin.

✅ Task completed successfully.

yaml
Copy code

---

### 📝 `Day25/code/git_commands.sh`
```bash
#!/bin/bash
# Day 25: Git Branching and Merge Task

cd /usr/src/kodekloudrepos/cluster || exit 1

# Create and checkout new branch
git checkout -b xfusion

# Copy the index.html file
cp /tmp/index.html .

# Stage and commit
git add index.html
git commit -m "Add index.html file from /tmp into xfusion branch"

# Push xfusion branch
git push origin xfusion

# Switch back to master and merge
git checkout master
git merge xfusion

# Push master branch
git push origin master