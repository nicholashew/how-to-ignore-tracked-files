# How to ignore tracked files in git

### Create files

```
mkdir bin
echo bar > foo.txt
echo world > bin\hello.txt
```

### Initial commit

```
git init
git add .
git commit -m "first commit"
```

### Create .gitignore file

```
git checkout -b dev
echo bin/ > .gitignore
git add .
git commit -m "add gitignore"
```

### Remove tracked file

**Important**: The command of `git rm -r --cached .` will delete all ignored files, but previously was tracked.

If you need the files keep those files in your local, first manually backup in somewhere before running commands below

```
git rm -r --cached . 
git add .
git commit -am "Remove ignored files"

git checkout master
git merge dev
git branch -d dev
```

The ignored folder should be deleted now

```
dir
```

Put back the previous bin folder, and the git shall not tracking on it anymore.
Let's create more files inside the bin and see the git status result

```
mkdir bin
echo A > bin\a.txt
echo B > bin\b.txt
echo C > bin\c.txt

dir
git status
```
