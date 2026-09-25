# Git commands

## create a new repository on the command line

```bash
echo "# Git-Tutorial" >> README.md
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/cauvery-digital/Git-Tutorial.git
git push -u origin main
```

```bash
git init && git add . && git commit -m "first commit" && git branch -M main && git remote add origin https://github.com/cauvery-digital/Git-Tutorial.git && git push -u origin main
```

…or push an existing repository from the command line

```bash
git remote add origin https://github.com/cauvery-digital/Git-Tutorial.git
git branch -M main
git push -u origin main
```
