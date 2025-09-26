Day 30: Git Reset to Specific Commit

## Scenario
The Nautilus application development team was working on a git repository located at:

/usr/src/kodekloudrepos/blog

sql
Copy code

This was just a test repository, and one of the developers pushed a couple of changes for testing.  

Now, they want to **clean the repository** along with the commit history/work tree so that the repository only points back to a specific commit.  

### Requirement
- Reset the git commit history so that only **two commits** remain:
  1. Initial commit  
  2. `add data.txt file`  

- Push these changes to the remote repository.  