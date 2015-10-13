# p4mergescripts
Launchers for P4 Merge to use with git.

# WHAT?
Scripts to launch p4 merge to use it with git.

# Credits
These were all taken from here:
http://pempek.net/articles/2014/04/18/git-p4merge/

I put these in a git repo for convenience and future reference.
All credit to Gregory Pakosz.

Below begins his documentation:

----------------------------------------------------------------

##Smooth Git + P4merge

Git Logo
For a couple of year, I’ve been using P4Merge as my Git diff/merge tool.

Generally speaking, I’m exclusively using Git CLI because I’ve witnessed people who insist on using GUI frontends seem to stagnate on the Git learning curve.

Nevertheless, I appreciate working with a visual diff/merge tool in the following situations:

- comparing branches/sha1s content: $ git difftool A..B [<path>...]
- resolving merge conflicts: $ git mergetool [<path>...]

To improve my experience, I wrote a p4merge launcher script I’m sharing with you.

The script exists in 3 versions: Windows, Linux and Mac. Compared to invoking P4Merge directly, it irons out small discrepancies:

P4Merge on Windows doesn’t support /dev/null
P4Merge on Mac works better with the provided launchp4merge launcher and absolute paths
When dealing with submodules, Git up to 1.9.1 feeds the submodule directory in the external diff driver instead of creating a temporary file containing "Subproject commit $sha"

#Windows instructions

Save the following p4merge file in the `C:\Program Files (x86)\Git\bin` directory.

Then, from within Git Bash, issue the following commands:
`
$ chmod +x '/c/Program Files (x86)/Git/bin/p4merge'
$ git config --global merge.tool p4merge
$ git config --global mergetool.keepTemporaries false
$ git config --global mergetool.prompt false
`

#Linux instructions

Save the following p4merge file in the `/usr/local/bin` directory.

Then, from within Bash, issue the following commands:
`
	$ chmod +x '/usr/local/bin/p4merge'
	$ git config --global merge.tool p4merge
	$ git config --global mergetool.keepTemporaries false
	$ git config --global mergetool.prompt false
	The script assumes P4Merge is installed in /opt/p4v.
`

#Mac instructions

Save the following p4merge file in the `/usr/local/bin` directory.

Then, from within Bash, issue the following commands:
`
	$ chmod +x '/usr/local/bin/p4merge'
	$ git config --global merge.tool p4merge
	$ git config --global mergetool.keepTemporaries false
	$ git config --global mergetool.prompt false
`

Hope that helps!