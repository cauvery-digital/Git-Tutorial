
# What is Git?

A distributed version control system (VCS) whose primary user interface is the Unix command line. It basically keeps a "non-human-readable" database of the files you put under version control ("track") and provides commands to access and update that database.

Graphical user interfaces, integration in Integrated Design Environments, and web platforms GitHub/GitLab/… have formed around the Git core software.

The aim here is not to tell you every single Git command in existence or even to teach you all the functionality. The aim is to familiarise you with the principles of version control, and some good practices, and get you started on the practical matters.

Git is also Source Control Management (SCM), i.e. a tool, which allows you to manage and track changes to files over time, making it possible to revert to a file.

## Practical introduction by example

### We're going to walk you through an example. 

The things we show you here will teach you all you need to know to collaborate on your team project using Git.

## Why version control?

* Combine the work of multiple collaborators
* Understand changes
* Support incremental development
* Compare and revert to earlier versions
* Backup
* Parallel versions

Document development (for other developers and yourself, not for users)

→ version control is awesome. Use it all the time.

## Installation: <https://git-scm.com/downloads>

**Windows user:** git is not automatically installed.

**Mac user:** git is typically already installed.

Note: when git is installed, git Bash is automatically installed.

# Git Tutorial

Here's a **complete list of Git commands** with clear **explanations** to help beginners understand and use Git confidently. These are organized by category so you can refer back as you grow.

---

The git config command is a powerful built-in utility used to get, set, and customize the behavior, appearance, and environment variables of [Git](https://git-scm.com/docs/git-config).

These settings govern everything from your basic commit identity to advanced merge tools and custom shortcuts.

The 3 Configuration Levels
Git stores its settings in text files across three distinct levels of scope. Local settings always override global ones, and global settings override system ones.

| Scope | Flag | Description | File Location |
|---|---|---|---|
| Local | --local | Applies only to the current active repository. | .git/config (within the project) |
| Global | --global | Applies to your specific user across all repositories. | ~/.gitconfig (Linux/macOS) C:\Users\<Name>\.gitconfig (Windows) |
| System | --system | Applies to every user on the entire machine. | /etc/gitconfig |

## 🛠️ **Setup & Configuration**

| Command                                           | Explanation                             |
| ------------------------------------------------- | --------------------------------------- |
| `git --version`                                   | Check installed Git version.            |
| `git config --global user.name "Your Name"`       | Set your Git username globally.         |
| `git config --global user.email "your@email.com"` | Set your Git email globally.            |
| `git config --global core.editor code`            | Set VS Code (or any editor) as default. |
| `git config -global branch.autosetuprebase always`| Avoid merge commit for pulling.         |
| `git config --list`                               | Show all Git configuration settings.    |
| `git config -global color.ui true`                | enable color highilighting for git console|
| `git config -global color.status auto`            |                                         |
| `git config -global color.branch auto`            |                                         |

### ⚙️ Essential Configuration Commands

#### 1. Identity & First-Time Setup
Setting up your identity ensures that your commits are correctly attributed to you in collaborative environments. 

* Set username: 
```
git config --global user.name "Your Name"
```
* Set email address: 
```
git config --global user.email "your.email@example.com"
```
* Set default branch name: 
```
git config --global init.defaultBranch main
```
(Changes the default branch from master to main for new repositories).

#### 2. Inspecting Your Settings

* List all active settings: 
```
git config --list
```
* List settings with their origin file: 
```
git config --list --show-origin
```
* Check a single setting value:
```
git config user.name
```

#### 3. Modifying & Removing Values

* Change a setting: Run the exact configuration command again with the new value.
* Remove a setting:
```
git config --global --unset <key>
```
(e.g., git config --global --unset user.signingkey).

------------------------------

### 🎨 Popular Workflow Customizations

#### The Core Editor

By default, Git opens the system terminal editor (like Vim or Nano) for commit messages. You can switch this to a modern editor:

* Visual Studio Code:
```
git config --global core.editor "code --wait"
```
* Emacs:
```
git config --global core.editor "emacs"
```

#### UI and Mechanics

* Colorize terminal output:
```
git config --global color.ui auto
```
* Pull with rebase by default:
```
git config --global pull.rebase true
```
(Avoids unnecessary merge commits when updating your local branch).

#### Git Aliases
You can create short aliases for long or frequently used commands to save keystrokes:

* Shortcut for checkout:
```
git config --global alias.co checkout
```
* Shortcut for status: 
```
git config --global alias.st status
```
* Fancy log view:
```
git config --global alias.lg "log --graph --oneline --decorate"
```

---

## 📁 **Repository Initialization**

| Command                | Explanation                                        |
| ---------------------- | -------------------------------------------------- |
| `git init`             | Create a new Git repository in current folder.     |
| `git clone <repo-url>` | Clone a remote repository into your local machine. |

---

## ✅ **Basic Workflow**

| Command                    | Explanation                                      |
| -------------------------- | ------------------------------------------------ |
| `git status`               | Show changes in the working directory.           |
| `git add <file>`           | Add a specific file to staging area.             |
| `git add .`                | Add **all** modified/created files.              |
| `git commit -m "message"`  | Commit changes with a short message.             |
| `git commit -am "message"` | Add **tracked** files and commit in one command. |
| `git log`                  | Show commit history (latest to oldest).          |
| `git show <commit>`        | Show detailed info for a specific commit.        |
| `git diff`                 | Show changes not yet staged.                     |
| `git diff --staged`        | Show staged changes.                             |

---

## 🌐 **Remote Repositories (GitHub, GitLab, etc.)**

| Command                       | Explanation                                          |
| ----------------------------- | ---------------------------------------------------- |
| `git remote -v`               | Show remote repositories (like GitHub).              |
| `git remote add origin <url>` | Add a remote repo and name it `origin`.              |
| `git push -u origin main`     | Push local main branch to remote for the first time. |
| `git push`                    | Push committed changes to remote repo.               |
| `git pull`                    | Fetch and merge changes from remote repo.            |
| `git fetch`                   | Get updates from remote, **don’t merge**.            |

---

## 🌱 **Branching & Merging**

| Command                         | Explanation                           |
| ------------------------------- | ------------------------------------- |
| `git branch`                    | List all branches.                    |
| `git branch <branch-name>`      | Create a new branch.                  |
| `git checkout <branch-name>`    | Switch to another branch.             |
| `git checkout -b <branch-name>` | Create and switch to a new branch.    |
| `git merge <branch>`            | Merge a branch into your current one. |
| `git branch -d <branch>`        | Delete a branch (if merged).          |
| `git branch -D <branch>`        | Force delete a branch.                |

---

## 🔄 **Undoing Changes**

| Command                       | Explanation                            |
| ----------------------------- | -------------------------------------- |
| `git restore <file>`          | Undo changes in working directory.     |
| `git restore --staged <file>` | Unstage file (keep changes).           |
| `git reset <file>`            | Unstage file (older method).           |
| `git reset --hard`            | Discard all changes in tracked files.  |
| `git reset --soft HEAD~1`     | Undo last commit, keep changes staged. |
| `git reset --mixed HEAD~1`    | Undo last commit, unstage changes.     |

---

## 🧪 **Stashing (Temporary Work Saving)**

| Command           | Explanation                         |
| ----------------- | ----------------------------------- |
| `git stash`       | Save current work temporarily.      |
| `git stash pop`   | Apply last stash and remove it.     |
| `git stash apply` | Apply last stash but keep it saved. |
| `git stash list`  | Show all stashed changes.           |
| `git stash drop`  | Delete the last stash.              |

---

## 🔍 **Viewing Information**

| Command             | Explanation                       |
| ------------------- | --------------------------------- |
| `git log --oneline` | Short summary of commit history.  |
| `git log --graph`   | Show commits as a visual tree.    |
| `git blame <file>`  | Show who last modified each line. |

---

## 🚮 **Deleting Files**

| Command                  | Explanation                                   |
| ------------------------ | --------------------------------------------- |
| `git rm <file>`          | Delete a file from Git and working directory. |
| `git rm --cached <file>` | Remove file from Git, keep it locally.        |

---

## 🔐 **Tagging Releases**

| Command                     | Explanation                      |
| --------------------------- | -------------------------------- |
| `git tag`                   | Show all tags.                   |
| `git tag <tag>`             | Create a new tag (e.g., `v1.0`). |
| `git tag -a <tag> -m "msg"` | Create annotated tag.            |
| `git push origin <tag>`     | Push tag to remote.              |
| `git push origin --tags`    | Push all tags to remote.         |

---

## 🧼 **Clean Up**

| Command        | Explanation                  |
| -------------- | ---------------------------- |
| `git clean -n` | Preview files to be deleted. |
| `git clean -f` | Delete untracked files.      |

---

## ⚙️ **Git Aliases (Optional, but Useful)**

Set shortcuts for common commands:

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm "commit -m"
git config --global alias.st status
```

Then you can do:

* `git co main` instead of `git checkout main`
* `git cm "message"` instead of full commit message

---

Would you like me to export this list as a PDF or Markdown file for easy reference?

## gitignore global setup

Git supports a global .gitignore file that allows you to specify patterns for files and directories to be ignored across all your local Git repositories. This is useful for ignoring operating system-specific files (e.g., .DS_Store, Thumbs.db), IDE configuration files (e.g., .vscode, .idea), or temporary files generated by your development environment.

To set up a global .gitignore file: Create the global ignore file.

You can create a file named ignore within the ~/.config/git/ directory (you may need to create this directory if it doesn't exist).

```bash
    mkdir -p ~/.config/git && touch ~/.config/git/ignore
```

Alternatively, you can create the file anywhere you prefer, for example, in your home directory:

```bash
    touch ~/.gitignore_global
```

### Add patterns to the global ignore file:

Open the created file (e.g., ~/.config/git/ignore or ~/.gitignore_global) with a text editor and add the patterns for files and directories you want to ignore globally, following the same syntax as a regular .gitignore file.

**Full .gitignore:**

```bash
package-lock.json
# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
lerna-debug.log*

# Diagnostic reports (https://nodejs.org/api/report.html)
report.[0-9]*.[0-9]*.[0-9]*.[0-9]*.json

# Runtime data
pids
*.pid
*.seed
*.pid.lock

# PM2 process logs
pids/
*.pm2.log

# Directory for instrumented libs generated by jscoverage/JSCover
lib-cov

# Coverage directory used by tools like istanbul
coverage
*.lcov

# nyc test coverage
.nyc_output

# Grunt intermediate storage (https://gruntjs.com/creating-plugins#storing-task-files)
.grunt

# Bower dependency directory (https://bower.io/)
jspm_packages/
bower_components

# node-waf configuration
.lock-wscript

# Compiled binary addons (https://nodejs.org/api/addons.html)
build/Release

# Dependency directories
node_modules/
jspm_packages/

# Production build
dist/
build/

# Snowpack dependency directory (https://snowpack.dev/)
web_modules/

# TypeScript cache
*.tsbuildinfo

# Optional npm cache directory
.npm

# Optional eslint cache
.eslintcache

# Optional stylelint cache
.stylelintcache

# Optional REPL history
.node_repl_history

# Output of 'npm pack'
*.tgz

# Yarn Integrity file
.yarn-integrity

# dotenv environment variable files
.env
.env.*   # covers .env.development, .env.production, etc.
!.env.example

# parcel-bundler cache (https://parceljs.org/)
.cache
.parcel-cache

# Next.js build output
.next
out

# Nuxt.js build / generate output
.nuxt
dist

# Gatsby files
.cache/
# Comment in the public line in if your project uses Gatsby and not Next.js
# https://nextjs.org/blog/next-9-1#public-directory-support
# public

# vuepress build output
.vuepress/dist

# vuepress v2.x temp and cache directory
.temp
.cache

# Sveltekit cache directory
.svelte-kit/

# vitepress build output
**/.vitepress/dist

# vitepress cache directory
**/.vitepress/cache

# Docusaurus cache and generated files
.docusaurus

# Serverless directories
.serverless/

# FuseBox cache
.fusebox/

# DynamoDB Local files
.dynamodb/

# Firebase cache directory
.firebase/

# TernJS port file
.tern-port

# Stores VSCode versions used for testing VSCode extensions
.vscode-test

# yarn v3
.pnp.*
.yarn/*
!.yarn/patches
!.yarn/plugins
!.yarn/releases
!.yarn/sdks
!.yarn/versions

# yarn v2
.yarn/cache
.yarn/unplugged
.yarn/build-state.yml
.yarn/install-state.gz

# Vite logs files
vite.config.js.timestamp-*
vite.config.ts.timestamp-*

.vscode/*
!.vscode/settings.json
!.vscode/tasks.json
!.vscode/launch.json
!.vscode/extensions.json
!.vscode/*.code-snippets
!*.code-workspace

# Built Visual Studio Code Extensions
*.vsix

# Mac system files
.DS_Store

### Windows ###
# Windows thumbnail cache files
Thumbs.db
Thumbs.db:encryptable
ehthumbs.db
ehthumbs_vista.db

# Dump file
*.stackdump

# Folder config file
[Dd]esktop.ini
Desktop.ini

# Recycle Bin used on file shares
$RECYCLE.BIN/

# Windows Installer files
*.cab
*.msi
*.msix
*.msm
*.msp

# Windows shortcuts
*.lnk

# SvelteKit build
.svelte-kit/

# Turbo/ Nx build cache
turbo/
nx-cache/

# Optional IDE settings
.idea/
*.suo
*.ntvs*
*.njsproj
*.sln

# if you're deploying to Vercel or Firebase:
.vercel/
.firebase/
```

Configure Git to use the global ignore file:
If you placed the file in a custom location (like ~/.gitignore_global), you need to tell Git where to find it using the core.excludesfile configuration option.

```bash
    git config --global core.excludesfile ~/.gitignore_global
```

If you placed it in the default location (~/.config/git/ignore), Git should automatically recognize it without requiring this explicit configuration.