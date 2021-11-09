repositories contains files, history, config managed by git
Three states of Git:
Working directory
staging area - pre commit holding area
Commit - Git repository (history)

Remote Repository (GitHub)
Master Branch

-----------------------------------------
Install git
Configure git: 
git config --global user.name "mrinal dutta"
git config --global user.email "mrinal.java@gmail.com"

check: git config --global --list
-----------------------------------------

Cloning:
git clone url
go to repo : cd myrepo
git status
>>>>>>>>>>>>>this will create a working directory

add new file:
echo "test git quick start demo" >> start.txt
ls
cat start.txt
git status
>>>>>>>>>>>>>file is in working area

git add .
>>>>>>>>>>>>>now the file is in staging area.

git commit -m "adding start text area"
git status
>>>>>>>>>>>>>Now the file moved from staging to local reporsitory

Still our file is in local area, now need to move into remote area:
git push origin master
>>>>>>>>>>>>>Now the file is in remote area
----------------------------------------

Get updates from remote repo to your local repo: recomended alywas going to pull before going to push:
git pull origin master

Tracked files: files which are tracked after added or commited. Its in staging or repository area -
git ls-files

---------------------------------------

Adding recursively: suppose dir1/dir2/dir3
git add .

----------------------------------------

backing out changes:
after adding, wants to backout staging: git reset HEAD filename

after modified, before adding: git checkout -- filename

-----------------------------------------

Renaming file
git mv level1-file.txt level1.txt

Now check git status:
File is renamed

Now move from one directory to another directory(level2):
mv level1.txt level2

Now check git status:
you can find deleted level1.txt and
added level2/level1.txt

Now revert this and mv using git mv command:
git mv level1.txt level2

Now git status:
you can find its mentioend as renamed

Now check or added the untracked files:
git add -A

--------------------------------------

Deleting files:
Delete untracked file - untracked means its not yet added into staging area:
git rm doomed.txt
>>>>>complain tht did not match any files

So need to rm doomed.txt
here no need to commit anything as git doesnt tracked this file


Now delete tracked file:
suppose you have committed file named newfile.txt

now git rm newfile.txt
git status ---------- shows deleted newfile.txt
now git commit -m "deleting newfile"


---------------------------------------
Revert your changes:
suppose delete one tracked file by >>> git rm hipster.txt

Git status >>> deleted hipser.txt

Now revert your changes :
git reset HEAD hipster.txt

Now ls, but doesnt back into area this hipster.txt
Git reset HEAD actually unstaged this file, but unable to move into his original area.
So we need to checkout this file:

git checkout -- hipster.txt
now check this file back to original place.

----------------------------------
Suppose you have removed a file by bash command: rm hipster.txt
now check: git status
>>> not staged for commit 
deleted hipster.txt

now back to staged: git add -A
now check: git status
>>>chamges to be commited
deleted hipster.txt

now git commit
---------------------------------
Check history:
git log

now check in diff format:
git log --oneline --graph --decorate

git log commitid

check log for a specifc file:
git log --follow -- level/level2/level2.txt

check a commit id:
git commit <commitId>

---------------------------------

Git Alias:
need to configure in global file:
git config --global alias.hist "log--all --graph --decorate --oneline" 

git searches for alias and find the hist.

now try with:  git hist

All of the alias are stored inside the .gitconfig file.
---------------------------------
Git ignore:
specific file: MyFile.txt
File pattern: *.ext
Folder: my-folder

create .gitignore
-------------------------------------

Merge Tool:
Visual Diff/ Merge Tool Setup:
P4Merge for windows
Git configuration

install p4merge from https://www.perforce.com/
now set the path in environment variable for p4merge installer path.
Now go to command prompt: try p4merge

Now set the p4merge in git global configuration:
git config --global merge.tool p4merge
git config --global mergetool.p4merge.path "c:/program files/Perforce/p4merge.exe"
Dont want every time merge tool : git config --global mergetool.prompt false 

Set for diff tool:
git config --global diff.tool p4merge
git config --global difftool.p4merge.path "c:/program files/Perforce/p4merge.exe"
Dont want every time diff tool : git config --global difftool.prompt false 

Now check :
git config --global --list

---------------------------
Comparing staging and working directory:

git diff

also check using p4merge:
git difftool 

comparing working and repository:
git diff HEAD

git difftool HEAD

comparing betwen staging and repository:
git diff --staged HEAD

Using p4merge:
git difftool --staged HEAD


specfic to only readme.md file: git difftool readme.md
--------------------------------------------------------------------------------------------------------------
Comparing between commits:

1. get the history : $ git log --oneline
2.comparing 2 arbtary git commit:git diff <commitid> HEAD
3 Comparing beteen head and head-1 Or last commit and last commit -1 : git diff HEAD HEAD^
4. git difftool <commit id 1> <commit id 2>

----------------------------------------------------------------------------------------------------------------------

comparing local master branch and remote master brnch:
git diff master origin/master 

-----------------------------------------------------------------------------------------------------------------------
  **Branching and Merging**
  git branch -a
  it will return local and remote branches
  it also returns the current active branch
  
  create new branch: git branch mynewbranch
  switch new branch: git checkout mynewbranch
  
  check history: git log --oneline --decorate
  
  renaming branch: git branch -m mynewbranch newbranch
  
  delete a branch: git branch -d newbranch ( remember, you can't delete a branch if you are in the same branch, so before deleting a branch move into some other branch)

  **Happy path / Fast forward Merges**:
  
  create new branch and switch: git checkout -b title-change 
 make some changes from feature branch.
 git commit from feature branch
 
 now move into master branch.
 git merge title-change (fast forward merges)
 No cmmmits here.
 
 **Happy Path/ Disable Fast forward merges**:
 go to master: git merge title-change --no-ff
 preserve commit message
 
 **Automatic Merge**:
 create new branch: git checkout -b simple-changes
 modify some file
 commit chnages: git commit -am "Adding team member to human"
 switch to master: git checkout master
 update some other file
 commit: git commit -am "Adding instruction"
 now check log: git log --oneline --graph --decorate --all (Here you can find 2 diff changes pn 2 diff branches)
 git merge simple-changes -m "merging changes from simele changes into master"
 
 
 
 
 
  
-----------------------------------------------------------------------------------------------------------------------  

**Git Stashing**
Simple Example
How to simple path for stashing in Git.
Command Listing
pwd
cd projects/starter-web
pwd
git status
clear
ls
mate simple.html
git status
git stash
git status
mate simple.html
clear
ls
mate README.md
git status
git commit -am "Quick fix in production to improve copyright notice"
git status
clear
git stash apply
mate simple.html
git commit -am "Done with simple.html updates"
git status
clear
git stash list
git stash drop
clear
  
  
Stashing Untracked Files / Using Stash Pop
Git does not include untracked (new) files with stash by default, however, we change change that. Also, we cover a new way to apply the most
recent stash.
Command Listing
pwd
git status
clear
git ls-files
mate humans.txt
git status
mate ANewFile.txt
git status
git stash
git status
git stash apply
git stash drop
git stash list
clear
git status
git stash -u
clear
git stash list
mate README.md
git commit -a
git commit -a
git status
clear
git stash pop
clear
git status
rm ANewFile.txt
git status
git commit -am "Updates to humans file after stash pop"
git status
  
  
Managing Multiple Stashes
Git's stash feature can support multiple stashes.
Command Listing
pwd
git status
clear
ls
mate simple.html
git stash save "simple changes"
clear
mate index.html
git stash save "index changes"
mate README.md
git stash save "Readme changes"
git stash list
git stash show stash@{1}
clear
git status
git stash list
git stash apply stash@{1}
clear
git status
git stash list
git stash drop stash@{1}
git stash list
clear
git stash list
git stash clear
git stash list
clear
  
  
Stashing into a Branch
We can use stash to move accidental changes into a feature branch.
Command Listing
pwd
git status
git stash list
clear
mate
mate simple.html
mate humans.txt
git status
git add index.html
git status
mate new.md
git status
git stash -u
git status
clear
  
git stash branch newchanges
  it will do following:
  creates a new branch called newchanges, 
  switch into the new branch
  stash applied
  drop stash
  
git stash list
git status
rm new.md
git add .
git status
git commit
  
git checkout master -- move into master
git merge newchanges -- merge all changes from feature branch into master branch
git branch -d newchanges
git branch
clear
  
  
Section Cleanup
Each section, we synchronize our changes with GitHub.
Command Listing
pwd
git status
git pull origin master
git push origin master
