---
id: doc2
title: GIT COMMAND
---


Change port in linux command

				https://www.liquidweb.com/kb/changing-the-ssh-port/

Configure the author name and email address to be used with your commits.
		
  				git config --global user.name "Sam Smith"
				git config --global user.email sam@example.com

Create new repository

		  		git init

For a remote server, use:

		  		git clone username@host:/path/to/
				

Add one or more files to staging (index):


		  		git add <filename>

		  		git add *


Commit changes to head (but not yet to the remote repository)

                  		git commit -m "Commit message"


Send changes to the master branch of your remote repository

				git push origin master


List the files you've changed and those you still need to add or commit:

				git status


List all currently configured remote repositories:

				git remote -v


Create a new branch and switch to it:

				git checkout -b <branchname>


Switch from one branch to another:

				git checkout <branchname>


List all the branches in your repo, and also tell you what branch you're currently in:

				git branch

Delete the feature branch:

				git branch -d <branchname>


Push the branch to your remote repository, so others can use it:

				git push origin <branchname>


Fetch and merge changes on the remote server to your working directory:

				git pull


To merge a different branch into your active branch:

				git merge <branchname>


After you have manually resolved any conflicts, you mark the changed file:

				git add <filename>


For ignoring file in repositories for secure credential like password and credit card details use .gitignore file :

				touch .gitignore
				add file which you want to ignore into .gitignore
				add .gitignore in git repository
				git checkout –filename 


It will undo all changes in commited file

				git revert commitID 


all changes are back to filename

				git reset hard-- commit id 


This is used to show the difference you made into file.

				git difftool 


git HEAD Branch_name : 

				HEAD is pointing towards the file you want to point.
				It works as a pointer.

