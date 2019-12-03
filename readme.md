# Now it works

## it just didn't ¬¬

## NOW IT WORKS AGAIN

[link to where it worked](https://stackoverflow.com/questions/24382150/git-hook-make-server-pull-after-i-push-to-github/36021187#36021187)

Just in case: 

Suppose ~/example is your project public/www folder. Ssh into your server:

`cd ~/example && mkdir .git && cd .git && git init --bare`

open:
`code hooks/post-receive`

add:

```
#!/bin/sh
GIT_WORK_TREE=~/example git checkout -f
```

`chmod +x hooks/post-receive`

The above will create a bare git repo in ~/example/.git folder. Add a post-receive executable hook and perform checkout into the example directory.

On local repo:

```
git remote add server ssh://my_user@my_server.com:/absolute_path/example/.git/
git push server +master:refs/heads/master

```
