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


### New Branches

```sh
git checkout <branch-name>
git branch <new-branch>
```
- **git checkout** Switch to the branch with the branch name entered following this command
- **git branch** Create branch from current branch

Alternative to the commands above, git checkout provides a convient method (-b) to create a new branch then switching to that newly created branch.
```sh
git checkout -b <new-branch> <existing-branch>
```
- **-b** is a git checkout argument to create and switch to the new branch.
- **<existing-branch>** additional branch parameter for creating a branch from an existing branch — instead of branching from the current one. (Note: If you were to branch from master it's better to branch from 'origin/master' instead of just the branch name, 'master'. 'master' without origin will branch for local.)

This command will push branch to remote
```sh
git push -u origin <newly-created-branch>
```
- **-u** is a git push argument to push upstream. This is a shorthand flag for `--set-upstream` Upstream sets the default remote branch for the current local branch. Any future git pull command (with the current local branch checked-out), will attempt to bring in commits from the `<remote-branch>` into the current local branch.
