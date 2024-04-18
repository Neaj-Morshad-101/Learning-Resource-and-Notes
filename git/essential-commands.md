# Remove Large files from git
To see all the large files pushed into the git repo
```
git rev-list --objects --all |
  git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' |
  sed -n 's/^blob //p' |
  sort --numeric-sort --key=2 |
  cut -c 1-12,41- |
  $(command -v gnumfmt || echo numfmt) --field=2 --to=iec-i --suffix=B --padding=7 --round=nearest
```


Run command like this to remove that file from every commit in the git history

```
git filter-branch -f --prune-empty --tag-name-filter cat --index-filter "git rm -rf --cached --ignore-unmatch files_to_delete" -- --all
```
# Essential Git Commands
stash, git stash pop, git rebase, git merge
pull, push -f, checkout, branch, rebase. squash(gitk), log, status, learn these stuff.


### Git squash / marge all commit into one commit: 
` gitk `
select the last commit from where you started committing. (Not your commit, prev of your first commit) 
right click -> select reset -> merge option -> ok. 
then your commit will be removed
To add your changes. commit and push again 
git add . / git commit / git push -f :

### Git rebase 
`git checkout master`
`git pull`
`git checkout feature-branch`
`git rebase master` or ` git rebase origin/main ` 
then if conflict happens, then goland -> Git -> Rebase > Merge [Left is your current brannch, Middle is what you want, right is master]


### Amend and Force Push
git add .
git commit -s -m "Commit Message" // -s for sign 
git push
git push --set-upstream origin <newbranch>   // if your commit has new branch
git commit --amend -s -m "Commit Message" // add this commit to prev-commit
git push -u -f //force push




## Initializing a Repository
- `git init`: Initializes a new Git repository in the current directory.

## Basic Configuration
- `git config --global user.name "Your Name"`: Sets your name for Git commits.
- `git config --global user.email "youremail@example.com"`: Sets your email address for Git commits.

## Cloning a Repository
- `git clone <repository-url>`: Clones a remote Git repository to your local machine.

## Making Changes
- `git status`: Displays the current status of your repository, showing modified, staged, and untracked files.
- `git add <file>`: Stages changes of a specific file to be included in the next commit.
- `git add .` or `git add -A`: Stages all modified and untracked files for the next commit.
- `git commit -m "Commit message"`: Commits the staged changes with a descriptive message.

## Branching and Merging
- `git branch`: Lists all branches in the repository.
- `git branch <branch-name>`: Creates a new branch with the specified name.
- `git checkout <branch-name>`: Switches to the specified branch.
- `git checkout -b <new-branch-name>`: Creates a new branch and switches to it.
- `git merge <branch-name>`: Merges the specified branch into the current branch.
- `git branch -d <branch-name>`: Deletes the specified branch.

## Remote Repositories
- `git remote`: Lists all remote repositories.
- `git remote -v`: Lists all remote repositories with their URLs.
- `git remote add <remote-name> <repository-url>`: Adds a new remote repository.
- `git push <remote-name> <branch-name>`: Pushes the branch to the specified remote repository.
- `git pull <remote-name> <branch-name>`: Pulls changes from a remote repository into the current branch.
- `git fetch <remote-name>`: Fetches changes from a remote repository without merging.

## Inspecting History
- `git log`: Displays a log of all commits in the repository.
- `git log --oneline`: Displays a compact log with abbreviated commit messages.
- `git diff`: Shows the differences between the working directory and the last commit.
- `git diff <commit-id-1> <commit-id-2>`: Shows the differences between two commits.

## Undoing Changes
- `git reset <commit-id>`: Undoes commits, moving the branch pointer to a previous commit.
- `git revert <commit-id>`: Creates a new commit that undoes the changes made in a specific commit.
- `git checkout -- <file>`: Discards changes in a specific file and reverts it to the last commit.
- `git clean -df`: Removes untracked files from the working directory.

## Tagging
- `git tag`: Lists all tags in the repository.
- `git tag <tag-name>`: Creates a new lightweight tag at the current commit.
- `git tag -a <tag-name> -m "Tag message"`: Creates an annotated tag with a message.
- `git push <remote-name> --tags`: Pushes tags to the specified remote repository.
- `git show <tag-name>`: Displays information about a specific tag.