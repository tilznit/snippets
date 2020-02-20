### makes your local repo exactly like your remote repo
```git
git fetch --prune origin
git reset --hard origin/master
git clean -f -d
```
