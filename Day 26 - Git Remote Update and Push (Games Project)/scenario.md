# Day 26: Git Remote Update and Push (Games Project)

## Scenario
The xFusionCorp development team maintains a project under `/opt/games.git`, which is cloned at `/usr/src/kodekloudrepos/games`.  

Recently, the DevOps team added new Git remotes on the Git server hosted in Stratos DC.  
Your tasks are:

1. In `/usr/src/kodekloudrepos/games` repo, add a new remote named `dev_games` and point it to `/opt/xfusioncorp_games.git`.
2. Copy the file `/tmp/index.html` into the repo.
3. Add and commit the file to the `master` branch.
4. Push the `master` branch to the new remote (`dev_games`).
