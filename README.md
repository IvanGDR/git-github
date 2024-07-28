# git-github

Install Git
Git comes installed by default in ubuntu, according to your OS version, it may be not possible to havethe latest git version using:
sudo apt install git

To get latest version, add the repository
sudo add-apt-repository ppa:git-core/ppa 

Then install git latest version, according to git github releases information
sudo apt-get update && sudo apt-get -y install git


Global Git config
For setting git globally, we execute the following command for the whole computer
e.g. in my home directory
git config --global user.name "IvanG-Dell"
git config --global user.email "ivangarciadelrisco@gmail.com"
This will create in /home/ivang/ a git.config file:

ivang@inspiron-15-3552 ~ » cat .gitconfig 
[user]
	name = IvanG-Dell
	email = ivangarciadelrisco@gmail.com

Note: This is not login information but just an identifier



Create Project Directory 

1)Project Directory
$ mkdir /Documents/git-space
$ mkdir /documents/git-space/project1
$ cd /Documents/git-space/project1

2) Initialise git in the project directory
>Documents/git-space/project1 $ git init 
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint: 	git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint: 	git branch -m <name>
Initialised empty Git repository in /home/ivang/Documents/git-space/project1/.git/

note the .git directory created in the project directory
>Documents/git-space/project1/.git (master) » ls -la
drwxrwxr-x 2 ivang ivang 4096 Jul 27 15:28 branches
-rw-rw-r-- 1 ivang ivang   92 Jul 27 15:28 config
-rw-rw-r-- 1 ivang ivang   73 Jul 27 15:28 description
-rw-rw-r-- 1 ivang ivang   23 Jul 27 15:28 HEAD
drwxrwxr-x 2 ivang ivang 4096 Jul 27 15:28 hooks
drwxrwxr-x 2 ivang ivang 4096 Jul 27 15:28 info
drwxrwxr-x 4 ivang ivang 4096 Jul 27 15:28 objects
drwxrwxr-x 4 ivang ivang 4096 Jul 27 15:28 refs

Also, note the config file created
>Documents/git-space/project1/.git (master) » cat config           
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true


Per Project Git config
>Documents/git-space/project1 $ git config user.name "IvanG-Dell"
>Documents/git-space/project1 $ git config user.email "ivangarciadelrisco@gmail.com"   

The config file inside the /Documents/git-space/project1/.git directory has changed after this:

>Documents/git-space/project1/.git (master) » cat config 
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
[user]
	name = IvanG-Dell
	email = ivangarciadelrisco@gmail.com


- Connect to GITHUB repo
Same two commands as PER PROJECT GIF CONFIG
>Documents/git-space/project1 $ git config user.name "IvanG-Dell"
>Documents/git-space/project1 $ git config user.email "ivangarciadelrisco@gmail.com"   
Also:
>Documents/git-space/project1 $ git remote add origin https://github.com/IvanGDR/TestRepo.git

if at this stage we type: git remote -v
origin	https://github.com/IvanGDR/TestRepo.git (fetch)
origin	https://github.com/IvanGDR/TestRepo.git (push)
We could see, there is access to the remote github repo

Now, we may set the access token to this repository, to avoid typying username and password every time interaction with the remote repository happens.First , we create the token in github, so go to github then:
settings/developer settings/personal access tokens/fine grained tokens/generate tokens
in my case, for my github TestRepo repository only:
github_pat_11AQCDBOI0RabmjvNexxxxxxxxxxxxxxxxxxxxxxxxxM54C3NKOUckcUjtAY

>Documents/git-space/project1 $ git remote set-url origin https://IvanGDR:github_pat_11AQCDBOI0RabmjvNexxxxxxxxxxxxxxxxxxxxxxxxxxxM54C3NKOUckcUjtAY@github.com/IvanGDR/TestRepo.git

Additionally
a) git config --global credential.useHttpPath true
b) Make sure when generating token proper repo permissions are given to the token. As minimum ---> contents = read/write


>Documents/git-space/TestRepo/.git (master) » cat config 
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
[user]
	name = IvanG-Dell
	email = ivangarciadelrisco@gmail.com
[remote "origin"]
	url = https://IvanGDR:github_pat_11AQCDBOI0RabmjvNexxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxM54C3NKOUckcUjtAY@github.com/IvanGDR/TestRepo.git
	fetch = +refs/heads/*:refs/remotes/origin/*

