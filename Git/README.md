# Git
### Delete all local branches except current branch, master, and unmerged branches  
```sh
git branch -D `git branch --merged | grep -v \* | grep -v "master" | xargs`
```
- **`** Everything you type between backticks is evaluated (executed) by the shell before the main command
- **git branch -D** shortcut for --delete --force.
- **grep** prints lines that contain a match for one or more patterns.
- **grep -v** Invert the sense of matching of grep, to select non-matching lines
- **|** A pipe is a form of redirection (transfer of standard output to some other destination)
- **Xargs** It converts input from standard input into arguments to a command.
