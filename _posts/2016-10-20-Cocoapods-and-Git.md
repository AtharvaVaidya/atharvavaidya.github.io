#Cocoapods

1. Uninstall: `pod deintegrate`
2. Install: `pod install`
3. Update: `pod update`
4. Clear all pods' cache: `pod cache clean --all`
5. Initialize PodFile: `pod init`
6. List all pods: `pod list`
7. Update Pod Repo: `pod repo update`
8. Setup: `pod setup`
9. Build cocoapod: `pod lib lint --no-clean`

Get help for a command: `--help`. Example: `pod search --help`.

Verbose output flag: `--verbose`  

#Git

##Scripts

####Push to Existing Git Repo

1. `git add .`
2. `git commit -m "Your message for commit"`
3. `git push`

####Revert to previous commit

1. Hard Delete All Current Changes: `git reset --hard`
2. Save Current Work and then Revert: 
	`git stash ||
	 git reset --hard ||
	 git stash pop
	 `
	 
####Undo a git merge that hasn't been pushed

1. `git reset --hard ORIG_HEAD`

##Commands

`//$branch_name is a branch name`

1. Switch branch: `git checkout $branch_name`
2. Merge another branch into the current: `git merge $branch_name`
3. Pull new changes from remote: `git pull`
4. Remove a file from the working tree: `git rm $file_name`
5. List all branches: `git branch -a`