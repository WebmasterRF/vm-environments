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


### Diff

Install: 
[http://blogs.pdmlab.com/alexander.zeitler/articles/installing-and-configuring-p4merge-for-git-on-ubuntu/](http://blogs.pdmlab.com/alexander.zeitler/articles/installing-and-configuring-p4merge-for-git-on-ubuntu/)

Compare working vs. staged
`> git diff`

Compare working vs. last commit
`> git diff HEAD`

Compare state vs. last commit
`> git diff --cached Head`