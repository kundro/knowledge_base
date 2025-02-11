**GIT**

### What is Git?
💡 Git is a version control system that helps track changes in code and allows multiple people to work on a project at the same time.

#### Check Status
```sh
git status
```
💡 Shows which files have been changed and whether they are staged, unstaged, or untracked.

#### Fetch and Pull
```sh
git fetch   # Downloads changes but does not merge them
git pull    # Downloads and merges changes automatically
```
💡 `git pull = git fetch + git merge`.

### Commit
```sh
git add filename   # Add a specific file
git add .          # Add all changes
git commit -m "Your message"
```
💡 `git add` stages changes, and `git commit` saves them with a message.

### New Branch
```sh
git branch new-branch   # Create a new branch
git checkout new-branch # Switch to the new branch
git checkout -b new-branch  # Create and switch in one step
```
💡 Branches let you work on new features without affecting the main code.

### Merge
```sh
git checkout main   # Switch to the main branch
git merge new-branch  # Merge new-branch into main
```
💡 This combines changes from one branch into another.

### Rebase
```sh
git checkout feature-branch
git rebase main
```
💡 Rebasing moves your changes on top of another branch’s latest changes, keeping history clean.

### Resolve Merge Conflicts
1. Open the conflicting file.
2. Look for conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
3. Choose the correct version.
4. Save the file and run:
```sh
git add filename
git commit -m "Resolved conflict"
```
💡 Git warns you when different changes happen in the same file, and you need to fix them manually.

### Delete Branch
```sh
git branch -d branch-name  # Delete local branch
git push origin --delete branch-name  # Delete remote branch
```
💡 Use this when you no longer need a branch.

### Undo the Last Commit
```sh
git reset --soft HEAD~1  # Undo commit but keep changes
git reset --hard HEAD~1  # Undo commit and delete changes
```
💡 Use `--soft` to keep changes or `--hard` to remove them.

### Revert Commit
```sh
git revert commit-hash
```
💡 This creates a new commit that undoes the changes from a previous commit without deleting history.

