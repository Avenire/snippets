## rm deleted files from git
`git rm $(git ls-files --deleted)`

Alternatively, stage all changes in tracked files with `git add -u` 
