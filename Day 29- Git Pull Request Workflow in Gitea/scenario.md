# Day 29: Git Pull Request Workflow in Gitea

## Scenario
Max wants to push new changes to one of the repositories, but we cannot allow developers to push directly into the `master` branch since it should only contain reviewed and approved code.  

Instead, the correct workflow should be followed:  

1. SSH into the storage server using user `max` and password `Max_pass123`.  
2. The repo is already cloned under Max's home directory.  
3. Max has written his story **The 🦊 Fox and Grapes 🍇** and pushed it to the remote repository in branch:  


story/fox-and-grapes

4. Check the contents of the repo and confirm commit history (validate author info, commit messages, etc).  
5. Create a **Pull Request** (PR) to merge `story/fox-and-grapes` into `master`.  
6. PR Details:  
- Title: `Added fox-and-grapes story`  
- Source branch: `story/fox-and-grapes`  
- Destination branch: `master`  

7. Assign **Tom** as reviewer through the Git Portal UI.  
8. Login as Tom (`tom` / `Tom_pass123`) and approve the PR.  
9. Merge the PR into `master`.  

✅ Once merged, Max’s story is officially part of `master`.  

> **Note**: For UI-based tasks (like Gitea PRs), screenshots or recordings (e.g., via Loom) should be taken for review.

