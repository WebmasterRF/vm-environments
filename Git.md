### Terminal Commands

Print working direcory
`> pwd`

Show hidden
`> ll`
`> ls -al`

Home directory
`cd ~`
`cd`

Root
`cd /`

Clear
`> clear`

Open directory in finder
`>  xdg-open .`


### Git Configuration

List all
`> git config --global --list`

Set editor
`> git config --global core.editor "getit"`

Set name ane email example
`> git config --global user.email "tc@mail.com"`
`> git config --global user.name "tony c"`

Set alias example
`> git config --global alias.hist "log --oneline --all --decorate --graph"`


### Basics

Back file out of staging
`> git reset HEAD [file]`

Express commit (adds and commits together)
`> git commit -am "[commit message]"`


### Diff

Install: 
[http://blogs.pdmlab.com/alexander.zeitler/articles/installing-and-configuring-p4merge-for-git-on-ubuntu/](http://blogs.pdmlab.com/alexander.zeitler/articles/installing-and-configuring-p4merge-for-git-on-ubuntu/)

Order of commits
working -> stage -> HEAD -> [git hist id] -> repo (fetch)

Compare working vs. staged
`> git diff`
`> git difftool`

Compare working vs. last commit
`> git diff [filename]`
`> git diff HEAD`
`> git difftool HEAD`

Compare state vs. last commit
`> git diff --cached HEAD`
`> git difftool --cached HEAD`

Compare last commit vs. any previous commit
`> git difftool HEAD^^`
`> git difftool HEAD~2`
`> git show HEAD^^`
`> git show HEAD~2`

Compare any previous commit vs. previous commit
`> git show [commit id from 'git hist']`

Compare any vs. any previous commit
`> git difftool [commit id from 'git hist'] [commit id from 'git hist']`
`> git difftool --cached [commit id from 'git hist']`
`> git difftool HEAD [commit id from 'git hist']`

Get latest commit on repo (without merge)
`> git fetch all`

Compare working vs. last commit on repo
`> git difftool origin/[branch]`

Compare stage vs. last commit on repo
`> git difftool --cached origin/master`

Compare last commit vs. last commit on repo
`> git difftool HEAD origin/master`

Compare any previous commit vs. last commit on repo
`> git difftool HEAD~[number] origin/master`
`> git difftool [commit id from 'git hist'] origin/master`


### Branching / Merging

See current local branches available
`> git branch`

Create branch
`> git branch [name of branch]`

Change branch
`> git checkout [name of branch]`

Create / Change branch
`> git checkout -b [name of branch]`

Change branch name
`> git branch -m [current name of branch] [new name of branch]`

Push branch with tracking
`> git push -u origin [branch]`

Merge changes
`> git merge [branch to merge with current]`

No Fast Forward Merge
`> git merge --no-ff [branch to merge with current]`

Delete Branch
`> git branch -d [name of branch]`

Get all branchs from repo
`> git fetch --all`


### Merging Workflow (example using master / dev)

1. Branch off of master
`> git checkout -b master-test`

2. Merge dev into test branch
`> git merge dev`

2a. Resolve conflicts (if necessary)
`> git mergetool`

3. Test changes

4. Change to dev branch
`> git checkout dev`

5. Merge test branch to dev
`> git merge master-test`

6. Change to master
`> git checkout master`

7. Merge dev to master
`> git merge dev`


### Standards / Naming schemes


