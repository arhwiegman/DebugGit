# DebugGit
 for testing git commands with window cmd prompt 

# basic git commands

## check the status of the local branch 
`git status`

## stage (add) specific changes to next commit
`git add path/to/filename.extension` 

## stage all changes
`git add .`

## unstage all changes from the commit
`git reset`

## unstage specific changes from the commit
`git reset path/to/filename.extension` 

## commit all staged changes
`git commit`
you will be ask to give a commit message 

## unstage locally committed changes that have not been pushed. 
`git reset --soft HEAD~n`
where n is the number of commits to unstage. 
`git reset --soft HEAD~2`
the line above will unstage the last two commits. 

# Ignoring files and directories 

## .gitignore file
You can make Git ignore certain files and directories — that is, exclude them from being tracked by Git — by creating one or more .gitignore files in your repository.

In software projects, .gitignore typically contains a listing of files and/or directories that are generated during the build process or at runtime. Entries in the .gitignore file may include names or paths pointing to:

temporary resources e.g. caches, log files, compiled code, etc.
local configuration files that should not be shared with other developers
files containing secret information, such as login passwords, keys and credentials
When created in the top level directory, the rules will apply recursively to all files and sub-directories throughout the entire repository. When created in a sub-directory, the rules will apply to that specific directory and its sub-directories.

When a file or directory is ignored, it will not be:

tracked by Git
reported by commands such as git status or git diff
staged with commands such as git add -A
In the unusual case that you need to ignore tracked files, special care should be taken. 

https://sodocumentation.net/git/topic/245/ignoring-files-and-folders

```
# Lines starting with `#` are comments.

# Ignore files called 'file.ext'
file.ext

# Comments can't be on the same line as rules!
# The following line ignores files called 'file.ext # not a comment'
file.ext # not a comment 

# Ignoring files with full path.
# This matches files in the root directory and subdirectories too.
# i.e. otherfile.ext will be ignored anywhere on the tree.
dir/otherdir/file.ext
otherfile.ext

# Ignoring directories
# Both the directory itself and its contents will be ignored.
bin/
gen/

# Glob pattern can also be used here to ignore paths with certain characters.
# For example, the below rule will match both build/ and Build/
[bB]uild/

# Without the trailing slash, the rule will match a file and/or
# a directory, so the following would ignore both a file named `gen`
# and a directory named `gen`, as well as any contents of that directory
bin
gen

# Ignoring files by extension
# All files with these extensions will be ignored in
# this directory and all its sub-directories.
*.apk
*.class

# It's possible to combine both forms to ignore files with certain
# extensions in certain directories. The following rules would be
# redundant with generic rules defined above.
java/*.apk
gen/*.class

# To ignore files only at the top level directory, but not in its
# subdirectories, prefix the rule with a `/`
/*.apk
/*.class

# To ignore any directories named DirectoryA 
# in any depth use ** before DirectoryA
# Do not forget the last /, 
# Otherwise it will ignore all files named DirectoryA, rather than directories
**/DirectoryA/
# This would ignore 
# DirectoryA/
# DirectoryB/DirectoryA/ 
# DirectoryC/DirectoryB/DirectoryA/
# It would not ignore a file named DirectoryA, at any level

# To ignore any directory named DirectoryB within a 
# directory named DirectoryA with any number of 
# directories in between, use ** between the directories
DirectoryA/**/DirectoryB/
# This would ignore 
# DirectoryA/DirectoryB/ 
# DirectoryA/DirectoryQ/DirectoryB/ 
# DirectoryA/DirectoryQ/DirectoryW/DirectoryB/

# To ignore a set of files, wildcards can be used, as can be seen above.
# A sole '*' will ignore everything in your folder, including your .gitignore file.
# To exclude specific files when using wildcards, negate them.
# So they are excluded from the ignore list:
!.gitignore 

# Use the backslash as escape character to ignore files with a hash (#)
# (supported since 1.6.2.1)
\#*#
```
This topic illustrates how to avoid adding unwanted files (or file changes) in a Git repo.
There are several ways (global or local .gitignore, .git/exclude, git update-index --assume-unchanged, and git update-index --skip-tree), but keep in mind Git is managing content, which means: ignoring actually ignores a folder content (i.e. files). An empty folder would be ignored by default, since it cannot be added anyway.

You can make Git pretend that the working directory version of the file is up to date and read the index version instead (thus ignoring changes in it) with "skip worktree" bit:
`git update-index --skip-worktree <file>`
Writing is not affected by this bit, content safety is still first priority. You will never lose your precious ignored changes; on the other hand this bit conflicts with stashing: to remove this bit, use
`git update-index --no-skip-worktree <file>`
