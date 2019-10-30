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

### Delete local and remote branch
```sh
git branch -d <existing-branch>
```
- **-d** option is an alias for --delete, which only deletes the branch if it has already been fully merged in its upstream branch.
```sh
git branch -D <existing-branch>
```
- **-D** option is an alias for --delete --force, which deletes the branch "irrespective of its merged status."
```sh
$ git push <remote-name> --delete <existing-branch>
```
- **`<remote-name>`** is a short-hand label for a remote repository and "origin" is the conventional default name. There can be multiple remotes for your local repo and you use the remote name to push to them.
- **`<existing-branch>`** branch you want to delete.

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
- **`<existing-branch>`** additional branch parameter for creating a branch from an existing branch — instead of branching from the current one. (Note: If branching from master it's better to branch from 'origin/master' instead of just the branch name 'master'. 'master' without 'origin' will branch for local.)

This command will push branch to remote
```sh
git push -u origin <newly-created-branch>
```
- **-u** is a git push argument to push upstream. This is a shorthand flag for `--set-upstream` Upstream sets the default remote branch for the current local branch. Any future git pull command (with the current local branch checked-out), will attempt to bring in commits from the `<remote-branch>` into the current local branch.


### Reset file to origin
To reset local file to its original state from origin
```sh
git checkout <path/filename>
```
