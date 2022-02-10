# DebugGit
 for testing git commands with window cmd prompt 

# check the status of the local branch 
`git status`

# stage (add) specific changes to next commit
`git add path/to/filename.extension` 

# stage all changes
`git add .`

# unstage all changes from the commit
`git reset`

# unstage specific changes from the commit
`git reset path/to/filename.extension` 

# commit all staged changes
`git commit`
you will be ask to give a commit message 

# unstage locally committed changes that have not been pushed. 
`git reset --soft HEAD~n`
where n is the number of commits to unstage. 
`git reset --soft HEAD~2`
the line above will unstage the last two commits. 