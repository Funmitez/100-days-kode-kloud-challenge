Solution

## Steps Taken

1. **SSH into the storage server**
   ```bash
   ssh max@<storage-server-ip>
   # Password: Max_pass123
Navigate to the repo

bash
Copy code
cd ~/repo_name   # Replace with actual repo name
Check commit history

bash
Copy code
git log --oneline --decorate --graph --all
Verified branch story/fox-and-grapes with commit message: Added fox-and-grapes story.

Login to Gitea Web UI as Max

URL: <gitea-ui-url>

Username: max

Password: Max_pass123

Create Pull Request

PR Title: Added fox-and-grapes story

Source Branch: story/fox-and-grapes

Destination Branch: master

Submit PR

Assign Reviewer

Go to the PR page

Add tom as reviewer in the right-hand side panel

Login as Tom

Logout from Max’s session

Login with:

Username: tom

Password: Tom_pass123

Review & Approve PR

Open PR: Added fox-and-grapes story

Review changes

Approve the PR

Merge into master

Verification

Checked commit history in master

PR commit successfully merged

Story content is now part of master

✅ Task completed successfully.

yaml
Copy code

---

### 📝 `Day29/code/notes.md`
```markdown
# Notes for Day 29

- This task is mostly **UI-based** (Gitea).
- Important commands verified in terminal:
  ```bash
  git log --oneline --graph --decorate --all
  git branch -a
Branch story/fox-and-grapes confirmed before PR.

Screenshots or screen recordings should be taken when:

Creating PR

Assigning reviewer

Approving & merging PR

yaml
Copy code

---

⚡ Update root `README.md` tracker:

```markdown
| 29  | PR Workflow in Gitea (Review & Merge) | ✅ Completed |