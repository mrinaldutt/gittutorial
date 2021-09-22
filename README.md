# gittutorial


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



