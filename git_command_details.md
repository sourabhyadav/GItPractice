## Git command Cheat-sheet:

Git is a useful tool for developers. Specialy when you wanted to work on a common project with multiple people on the same workspace github is very usefull. 
I made a concise explaination of most of the commands and in what situation it should be used during the life-cycle of the poject. 

**One time activity:**

These command are usefull when you start your workspace and repo for the git to track for.

git --version				-> prints the version of your git
git config user.name "<author name>" 	-> adds the user name for the given git repo
git config user.email "<email id>" 	-> adds user email fot the given git repo
git init 				-> initilize the empty repo of as git repo to track changes
git remote add origin <webnickName> <URL of the github repo, ending with .git> -> This has to done once to link your local repo with server repo
git push -u origin master 		-> this has to be done at least at very first push for any server repo
	-> -u -> sets up the uplink
	-> origin -> server repo head (github link)
	-> master -> local repo head
	-> This also creates a default brack on the github server called master
	
**Note:** When you clone a repo from the server above command need not to be run because origin will be already set for you

**Basic git utils:**

git log					-> prints all the commit to the repo
git log --author "<author name>" 	-> prints all the commit to the repo from a specific user only
git status 				-> Prints the status of the current branch


**Add a file to git repo and commut them:**

git add <path/filename> or . 		-> . adds the all the new files inside the git repo
git commit -m "your message" 		-> commit your changes
	-> -m: is the message you wanted to give for this commit

**Note:** git commit will only make changes to your locl repo. To make the same changes you need to do git push to make changes to reflect on GitHub 


**View the chages that you made**

git diff 			-> shows the diff between the working file (the file which is not added yer) vs current repo file
git diff --staged 		-> shows diff between the staged copy (file which are added but not yet commited) vs current repo file

**How to delete a file** 

git rm <file name>		-> it deletes the file BUT you need to commit to ask git to take the snapshot for these changes to capture

**Note:** Git rename is simialr to detele and add a new file if you do it manually. Here you have to commit manually
**OR**

// use git mv command
git mv <oldfilename> <newfilename? 	-> it directly does the renaming of files, later comit manually to take the snapshot

**Commiting the changes directly to the repo**

git commit -am "commit message"

**Unsatging any file**

git reset HEAD < staged filename> 	-> unsaging any file making it again working copy	

**Rolling out for the older version of the any file**

git checkout -- <filename> 			-> it does take the repo copy version make it as a working copy
// above command is meant for working copy to replaced with repo copy

**Rolling back to previous commited versions**

git checkout <initials of commit number> -- <filename> 	-> this command will make the provided prev filename to your staging area . You need to review and edit it and them again commit

**Adding & Pushing repo to the github server to make it public (one time activity)**

git remote add <webnickName> <URL of the github repo, ending with .git>

**Pushing our changes to github remote** 

// Best practice is to create a "New Repo" from the github website
// Then start making changes to it 
git clone <website of the repo>
git add .
git commit -m "message of commit"
git push 
git commit -m "commit"

**BRANCHING:**

// Develop more features seperatly without touching master branch
// default branch is "master"
git branch <branch name> 		-> You can create new branch 
git checkout <branch name> 		-> to switch between the branches
git branch -v 				-> lists all the branches with * for working branch
// whenever you can on the particular branch the .git will show only those stuff in your folder struct i.e. win explorer
// Here you can make commits based on the features you are developing on this current branch later you can merge these changes to your master branch then you can push to remote server
// For more graphical details follow the [link](1]):

**MERGING**

// so whenever you create a branch comit or push changes to that particular new branch nothing happens to the master ot other branches
// To take your changes form your branch to say master branch you need to do merging

git merge <branch name> 		-> this will merge the the given branch to current active branch

// you need to add branch to the server if you want to push something from any particular branch
git push -u <branch name>

// you can push anything to a specific branch to the server
// Once the merging is done you can delete the unwanted branches
git branch -D <branch name>	-> this command will delete the branch locally but not on the server

**You need to explicitly delete the braches on the server** 
git push origin --delete <branch name>

**FORKING or Collaboration** with existing git repo <I nee to add more details on this>
// Updating your forked branch:
You might get something like "You are X commits behind <Original Repo>"

**Following are the commands to keep your forked Repo updated:**

cd into/cloned/fork-repo
git remote add upstream git://github.com/ORIGINAL-DEV-USERNAME/REPO-YOU-FORKED-FROM.git
git fetch upstream

git pull upstream master or  <branch name>
git push origin master or  <branch name>

Above commands will take all the changes form the sorce dir to your local copy

References:
[1]: https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging
