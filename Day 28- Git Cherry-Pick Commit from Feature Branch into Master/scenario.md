# Day 28: Git Cherry-Pick Commit from Feature Branch into Master

## Scenario
The Nautilus application development team has been working on a project repository `/opt/demo.git`.  
This repo is cloned at `/usr/src/kodekloudrepos` on the Storage server in Stratos DC.  

There are **two branches** in this repository:  
- `master`  
- `feature`  

A developer is still working on the `feature` branch, but they want to merge **one specific commit** into the `master` branch.  
The commit message to be merged is:


You need to cherry-pick that commit into `master` and push the updated branch back to the origin.
