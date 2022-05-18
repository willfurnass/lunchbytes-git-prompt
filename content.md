class: center, middle, title-slide

# A visual prompt for git at the command-line

Will Furnass &middot; IT Services &middot; 2022

@willfurnass

---

## In the zone...

```bash
cd ~/path/to/my/current/project
vim main.go
...
vim tests.go
...
vim README.go
...
vim main.go
...
vim template.tmpl
...
vim main.go
...
vim go.mod
...
```
---

## Er, maybe I'm in a git repo?

```sh
$ git status
...
Changes not staged for commit:
...
        modified:   README.md
        modified:   go.mod
        modified:   main.go
        modified:   template.tmpl
        modified:   tests.go
```
Whoops! Not just one logical chunk of uncommitted work!

**Easy to forget to `git status` before/during work**.

---

## State info in shell prompts 

By default, shell prompt might show >=1 of:

* current user
* hostname
* time
* directory
* ...

---
## State info in shell prompts 

Can customise prompt by assigning to `PS1` environment variable:

```sh
[will@laptop ~]$ echo hello
hello

[will@laptop ~]$ PS1='\D{%A @ %X}> '

Wednesday @ 20:33:14> echo hello
hello
```

**Can shell prompt show git state info**? 

E.g. whether in repo; if so, which branch, got uncommitted work?

---
## bash-git-prompt

[https://github.com/magicmonty/bash-git-prompt](https://github.com/magicmonty/bash-git-prompt)

If enabled, my prompt looks like this if my pwd is in a repo: 

```bash
mylaptop [featurebranch|✚ 1…4]
20:39 $
```

* I'm in a git repo!
* Can see which branch (plus other info)
* Prompt dynamically updated

---
## bash-git-prompt

Info that can show: 

* `(main↑3|✚1)` - on branch main, ahead of remote by 3 commits, 1 file changed but not staged
* `(status|●2)` - on branch status, 2 files staged
* `(main|✚7…)` - on branch main, 7 files changed, some files untracked
* `(main|✖2✚3)` - on branch main, 2 conflicts, 3 files changed
* `(main|⚑2)` - on branch main, 2 stash entries
* `(experimental↓2↑3|✔)` - on branch experimental; your branch has diverged by 3 commits, remote by 2 commits; the repository is otherwise clean
* `(:70c2952|✔)` - not on any branch; parent commit has hash 70c2952; the repository is otherwise clean

More syntax and install info: [https://github.com/magicmonty/bash-git-prompt](https://github.com/magicmonty/bash-git-prompt)

---
## Useful settings

Shell variables:

* `GIT_PROMPT_ONLY_IN_REPO=1` - don't modify prompt if not in repo
* `GIT_PROMPT_FETCH_REMOTE_STATUS=0` - don't poll git remotes 
* `GIT_PROMPT_START="$(hostname)"` - custom prompt prefix
* `GIT_PROMPT_DISABLE=1` - only on certain filesystems

---
## Thanks!

@willfurnass

