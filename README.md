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
Git
