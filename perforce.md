P4 setup:
1. Create p4 config file for project
2. p4 set P4HOST
3. P4 set P4USER=<user_name>
4. p4 set P4CLIENT=<project_name>

p4 swamp
p4 submit -> submit for review 
git commit = p4 shelve
after p4 submit -> add subsription -> being reviewed -> as2 to submit. 

Mainline: serves as the base or trunk of a stream system.

# Delete Client
  $ p4 client -d <client-name>

# Pull
	$ p4 sync

# Show all branches
	$ p4 branches

# Sjpw foes to be added/deleted
	$ p4 status

# Check what's changed
	$ p4 opened

# Open files and/or the stream spec for branching or merging.
  $ p4 intergrate


# Shelve Store files (or a stream spec) from a pending changelist in the depot, without submitting them.
  # shelve all the opened files. 
  $ p4 shelve

	$ p4 shelve -r -c <Change-List#>
	-r : replace all shelves files in that changelist with files opened in your own workspace. 
	-c : specify the pending changelist in which shelved files are to be creaeted. 

# Delete shelve 
	$ p4 shelve -d -c <change-list#>
	$ p4 change -d <change-list#>

# Revert all changes
	$ p4 revert //...





