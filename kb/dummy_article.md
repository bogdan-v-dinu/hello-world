----------------------------
Knowledge base on GIT itself
============================

Links
=====
GitHub Guides
https://guides.github.com/

Reset Demystified http://git-scm.com/blog
Merge conflicts and remotes http://dont-be-afraid-to-commit.readthedocs.org/en/latest/git/index.html

General
=======

Common options
--------------
-Test what a command would do: git <command> --dry-run

Pull Request 
------------
-comments are written in Markdown ==> embed mentions, images, emoji, use pre-formatted text blocks, other lightweight formatting
-mention = "@user-name"
-emoji = ":eyes:"
-close an issue = "fix(es/ed) #issue_no", also works with "close" and "resolve"

Commands
========
commit 
	git commit -a	= with automatic edit detection(equivalent to edit <filename>.../git add <filename>/git comit); TBD how does it work on removals

log
	git log origin/master..HEAD = log of un-pushed commits

reset
	git reset --soft <rev-hash> = move HEAD pointer to specified commit (index and working dir. not changed, hence files appear "changed")
	git reset [--mixed] <rev-hash> = same as --soft plus update the index (working dir. not changed, hence files appear "modified" or "untracked")
	git reset --hard <rev-hash> = same as --mixed plus overwrites files in working dir.

rm (remove) 
	git rm -r --cached <filepath> = recursively remove from index not from disk (file status deleted & untracked); by default removes from working folder as well

Work Sequence
-------------
	
Q&A
---
1. What does HEAD~ stand for?	
	