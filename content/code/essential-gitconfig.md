+++
title = "Essential .gitconfig"
date = "2017-10-31T18:30:26-07:00"
draft = false

+++

```plaintext
[user]
	name = James Leong
	email = jyleong@sfu.ca
[push]
	default = matching
[core]
	autocrlf = input
	safecrlf = true
	editor = vim
	excludesfile = /Users/jamesleong/.gitignore_global
[alias]
	f = fetch
	ci = commit
	st = status
	co = checkout
	br = branch
	lg1 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
	lg2 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all
	lg = !"git lg1"
[color]
    branch = auto
    diff = auto
    status = auto
[color "branch"]
    current = yellow reverse
    local = yellow
    remote = green
[color "diff"]
    meta = yellow bold
    frag = magenta bold
    old = red bold
    new = green bold
[color "status"]
    added = yellow
    changed = green
    untracked = cyan
[pull]
	rebase = preserve
[rebase]
	autostash = true
[merge]
	ff = no
```