Knowledge base on GIT
=====================

Links
-----
Reset Demystified http://git-scm.com/blog

General
-------
Test what a command would do: 
	git <command> --dry-run
Commands
--------
Remove from index not from disk (file status deleted & untracked)
	git rm --cached <filepath>
Commit with automatic edit detection
	git commit -a	= edit <filename> (..)/git add <filename>/git comit
Reset
	git reset --soft <rev-hash> = move HEAD pointer to specified commit (index and working dir. not changed, hence files appear "changed")
	git reset [--mixed] <rev-hash> = same as --soft plus update the index (working dir. not changed, hence files appear "modified" or "untracked")
	git reset --hard <rev-hash> = same as --mixed plus overwrites files in working dir.
Q&A
---
1. What does HEAD~ stand for?	
	