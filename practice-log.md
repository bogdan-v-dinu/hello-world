

Manually merge a pull request with conflicts
============================================
============================================
 :From: readme-edits2 
 :To: main
 :Merge conflict: README.md (edits on the same line)
	*perform the merge locally first (and resolve conflicts)
	*push to repository

Command list
============
 ->git config --get remote.origin.url (opt. info)
 ->git checkout readme-edits2 
 ->git branch (opt. info)
 ->git commit -a
 ->git branch -av (opt. info)
 ->git push origin readme-edits2
 ->git checkout master
 ->git merge --stat --verbose --no-commit --no-ff readme-edits2
 ->git status (opt. info)
 ->git diff --name-status HEAD (opt. info)
 ->git diff README.md (opt. info)
 ->git show :[1|2|3]:README.md	(opt. info)
 ->git commit -a -m "Merge pull request #3 from bogdan-dinu/readme-edits2"
 ->git push origin master
	
Details
=======
	
# get information about remote repository URL
# note: default name for git clone source is "origin"
# ---------------------------------------------------
>git config --get remote.origin.url
  https://github.com/bogdan-dinu/hello-world.git
>git remote show origin
* remote origin
  Fetch URL: https://github.com/bogdan-dinu/hello-world.git
  Push  URL: https://github.com/bogdan-dinu/hello-world.git
  HEAD branch: master
  Remote branches:
    master           tracked
    readme-edits2    tracked
    refs/pull/2/head tracked
    refs/pull/3/head tracked
  Local branches configured for 'git pull':
    master        merges with remote master
    readme-edits2 merges with remote readme-edits2
  Local refs configured for 'git push':
    master        pushes to master        (up to date)
    readme-edits2 pushes to readme-edits2 (fast-forwardable)

# switch to branch "readme-edits2"
# --------------------------------	
>git checkout readme-edits2 
Switched to branch 'readme-edits2'
Your branch is ahead of 'origin/readme-edits2' by 1 commit.
  (use "git push" to publish your local commits)

# list local branches
# note: brach pointed to by HEAD is marked with "*"
# -------------------------------------------------	
>git branch
  master
* readme-edits2

# commit after adding/removing files to/from index based on working folder content
# -------------------------------------------------------------------------------
>git commit -a

[readme-edits2 1dcc1ad] + git help link
 1 file changed, 3 insertions(+)

# list local and remote branches
# ------------------------------ 
>git branch -av
  master                       e0b4bae README update on master
* readme-edits2                1dcc1ad [ahead 2] + git help link
  remotes/origin/HEAD          -> origin/master
  remotes/origin/master        e0b4bae README update on master
  remotes/origin/pr/2          18423fc Update README.md
  remotes/origin/pr/3          91c996f Added dummy article
  remotes/origin/readme-edits2 91c996f Added dummy article

# push changes in "readme-edits2" to remote repository
# ----------------------------------------------------
>git push origin readme-edits2
Counting objects: 12, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (8/8), done.
Writing objects: 100% (8/8), 1.61 KiB | 0 bytes/s, done.
Total 8 (delta 1), reused 0 (delta 0)
To https://github.com/bogdan-dinu/hello-world.git
   91c996f..1dcc1ad  readme-edits2 -> readme-edits2  

# merge two branches with conflicts
# ---------------------------------
>git checkout master
>git merge --stat --verbose --no-commit --no-ff readme-edits2
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.   

# check status
# ------------
>git status
On branch master
Your branch is up-to-date with 'origin/master'

You have unmerged paths.
  (fix conflicts and run "git commit")

Changes to be committed:

        new file:   kb/README.md
        new file:   kb/dummy_article.md
        new file:   kb/index

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   README.md
   
>git diff --name-status HEAD
M       README.md
A       kb/README.md
A       kb/dummy_article.md
A       kb/index   

# view differences in merged files
# --------------------------------
>git diff README.md
++<<<<<<< HEAD
 +Hi github 1,
++=======
+ Hi github 2,
++>>>>>>> readme-edits2

>git show :[1|2|3]:README.md
list file in common-base version OR HEAD version OR MERGE_HEAD version

# commit merged version
# note: conflicts are manually resolved by editing the file, removing merge mark-up and keeping intended merge result
# -------------------------------------------------------------------------------------------------------------------
>git commit -a -m "Merge pull request #3 from bogdan-dinu/readme-edits2"   
[master 3d9aa34] Merge pull request #3 from bogdan-dinu/readme-edits2

# push changes in "master" to remote repository
# ---------------------------------------------
>git push origin master
Counting objects: 7, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 356 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://github.com/bogdan-dinu/hello-world.git
   e0b4bae..3d9aa34  master -> master
