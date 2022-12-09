# Github CLI 

	gh repo list

	gh repo clone <repo-name>

# Create a new branch
	$ git checkout -b <branch-name>

# Use another branch's file into current branch
	$ git checkout <branch-name> <file-in-that-branch-to-be-copied-to-current-branch>
# Get git repository url from terminal.

	$ git remote show origin

# Add local folders to a remote respository

	0) git init .

	1) git remote add origin <git_repo>

	2) git add . # make sure no files exceeds 100MB

	3) git commit -m "<message>"

	4) git push origin master

# Reset local branch to what's at remote

	$ git reset --hard <remote-branch-name>

# Generate ssh key for a machine with new OS installation

	$ ssh-keygen -t ed25519 -C "your_email@example.com"
	
	### Enter <Enter> for default "key" and "passphrase" entry 

	The public key to be pasted to github website at:

	$ vim ~/.ssh/id_rsa.pub 


	2) Configure local account information

	$ git config --global user.email <email>
	
 	$ git config --global user.name <name>

	3) Configure git commit message editor

	$ git config --global core.editor "vim"

# Clone your fork:

	$ git clone git@github.com:<username>/<FORKED_REPO>.git

# Pull from the master 

	$ git pull <remote> <branch>

	For example,

	$ git pull origin master

# Add remote from original repository in your forked repository:

	$ cd into/cloned/fork-repo
	
	$ git remote add upstream git://github.com/ORIGINAL-DEV-USERNAME/REPO-YOU-FORKED-FROM.git
	
	$ git fetch upstream

# Updating your fork from original repo to keep up with their changes:

	$ git pull upstream master

# To upload files to an unexisted repo: 
	
	### create that repo on github
	
	### git init .  
	
	### git add .
	
	### git remote add origin git@github.com:username/new_repo
	
	  *if these files have already belong to another origin, do: git remote rm origin
	
	### git commit -m "sync"
	
	### git push origin master 

# To add files with sizes larger than 100MB to .gitignore
	
	$ find . -size +100M >> .gitignore

# To undo "add"
	
	$ git add reset <file_name>

# To delete the last local commit.
	
	$ git reset HEAD^.

	This will keep the change and actual state of files, and just flushing the commits of them.

# If there are large files in the commit history, and you cannot delete even after reset:
    (!) git-filter-branch has a glut of gotchas generating mangled history rewrites.

    $ git filter-branch -f --tree-filter 'rm -f </path/to/file>' HEAD --all

# Untrack all files
	
	$ git rm --cached -r . 

	#commit the change again after untracking
	
	$ git commit --amend

# Delete all past commits of a repository

	# checkout a new one
	
	$git checkout --orphan latest_branch

	#Add all the files
	
	$ git add .

	#Commit the changes
	
	$ git commit -am "commit message"

	#Delete the branch
	$ git branch -D master

	#Rename the current branch to master
	
	$ git branch -m master

	#Finally, force update your repository
	
	$ git push -f origin master
	
# Fork a remote branch
	# identify current branch
	$ branch

	# make new branch
	$ git checkout -b "<branch_name>"

	# push this branch to the remote repository
	$ git push origin <branch_name>

# Delete a local branch
	$ git checkout -d <branch_name>

# Delete a remote branch
	$ git push origin --delete <branch_name>

# Add a submodule to a git repository

	$ git submodule add <repository-name> -b <branch-name> <folder-name>

	# This will clone the repository's certain branch into a location folder with 'folder-name' into the current directory

# Delete submodule

	$ git rm -r <submodule-name>

# gitignore rules:

	If there's a '#' anywhere in a line, then entire row is treated as a comment!

	/<folder>

# Fixing empty submodule after cloning parent git repo.

$ git submodule update --init

# Make current commit new head

 $ git reset --hard

 > HEAD is now at xxxx

 $ git checkout -B master

 Now do a normal push...


# List files cached before commit
	$ git diff --cached



	

	
