# Git - Version Control and Command Reference

## 1. Introduction
Git is a distributed version control system. It records changes to files over time so earlier versions can be inspected or recovered. It is widely used in software development because it avoids confusing copies such as `final`, `final-new` and `final-latest`.

Git works locally without a network connection. Each clone contains repository history, and changes can later be shared through a remote repository such as GitHub.

## 2. Why version control is needed
Without version control, files may be overwritten, old versions may be lost, and it can be difficult to find which change introduced an error. Combining changes from several contributors can also become complicated.

Version control helps track modifications, identify who changed a file and when, restore earlier versions, and support parallel work through branches.

## 3. Git and GitHub
| Git | GitHub |
|---|---|
| Version control system | Hosting and collaboration platform |
| Runs locally | Hosts remote repositories |
| Records commits and branches | Provides pull requests, Issues and project tools |
| Can be used offline | Online collaboration needs connectivity |

Git manages version history. GitHub hosts repositories and provides collaboration features.

## 4. How Git works
Git has three main areas:
1. **Working directory:** files currently being edited.
2. **Staging area:** selected changes prepared for the next commit.
3. **Repository:** committed project history.

The basic workflow is:

```text
Edit files → Stage changes → Commit → Push to remote
```

A commit is a recorded snapshot of staged changes. It includes a unique identifier, author, timestamp and message.

## 5. Installation and configuration
Download Git for Windows from [git-scm.com](https://git-scm.com/downloads). The supplied slides show these commands for Linux and macOS:

```bash
sudo apt update
sudo apt install git
brew install git
```

Check the installation:

```bash
git --version
```

Configure the author information used in commits:

```bash
git config --global user.name "Student Name"
git config --global user.email "student@example.com"
```

Use your own name and email. These settings identify the commit author; they do not authenticate you to GitHub.

## 6. Creating a repository
```bash
mkdir my-project
cd my-project
git init
```

`mkdir` creates a directory, `cd` enters it and `git init` initializes a repository. Git stores repository metadata in the hidden `.git` directory.

## 7. Status, staging and differences
Check the current state:

```bash
git status
```

Stage a file or multiple files:

```bash
git add main.py
git add .
git add file1.py file2.py
git add *.py
```

`git add` stages the contents as they exist at that moment. If a file changes after staging, stage it again.

Review changes:

```bash
git diff
git diff --staged
git diff HEAD
```

- `git diff`: unstaged changes to tracked files.
- `git diff --staged`: changes staged for commit.
- `git diff HEAD`: tracked changes compared with the current commit, including staged and unstaged changes.

## 8. Commits and history
```bash
git add main.py
git commit -m "Add main program"
git log
git log --oneline
```

A good commit message should be concise and specific. Examples: `Add input validation`, `Fix division by zero error`, and `Update project documentation`. `git log` shows detailed history; `git log --oneline` gives a compact view.

## 9. Listing and ignoring files
List files known to Git's index:

```bash
git ls-files
```

A `.gitignore` file lists untracked files and directories that Git should ignore. Example:

```gitignore
__pycache__/
*.pyc
.env
*.log
data/
```

This is useful for caches, local environment files, logs and generated data. Adding a secret to `.gitignore` does not remove it from history if it has already been committed.

## 10. Renaming and deleting
```bash
git mv old.py new.py
git rm old.py
```

`git mv` stages a rename or move. `git rm` removes a tracked file and stages the removal. Git commonly detects renames by comparing file contents.

## 11. Unstaging and discarding changes
Unstage a file while preserving its working-directory edits:

```bash
git restore --staged main.py
```

Discard unstaged modifications to a tracked file:

```bash
git restore main.py
```

**Caution:** the second command can permanently discard uncommitted edits. Inspect changes with `git diff` and save important work first.

## 12. Reverting a commit
```bash
git log --oneline
git revert COMMIT_ID
```

Replace `COMMIT_ID` with the actual identifier. `git revert` creates a new commit that reverses the earlier change, preserving the existing history. It is often suitable for undoing published changes.

## 13. Connecting to GitHub
After creating a remote repository:

```bash
git remote add origin REPOSITORY_URL
git remote -v
git branch -M main
git push -u origin main
```

`origin` is the conventional remote name. `git remote -v` lists fetch and push URLs. `git branch -M main` renames the current branch, and `-u` sets the upstream tracking relationship.

## 14. Clone, fetch and pull
```bash
git clone REPOSITORY_URL
git fetch origin
git pull
```

Cloning downloads the files and history and normally configures the source as `origin`. Fetch downloads remote updates without integrating them. Pull fetches and integrates changes into the current branch, typically by merge or rebase depending on configuration.

## 15. Branches
A branch is an independent line of development. It lets a feature be developed without directly changing the main branch.

```bash
git branch
git branch feature-login
git switch feature-login
git switch main
git switch -c feature-login
```

`git branch` lists local branches. The branch with an asterisk is current. Creating a branch does not automatically switch to it. `git switch -c` creates and switches in one command. Use descriptive names such as `feature-login`, `fix-navbar` and `docs-update`.

## 16. Merging branches
To merge a feature branch into `main`:

```bash
git switch main
git merge feature-login
```

The branch currently checked out is the target branch. Resolve any conflicts and test the result.

## 17. Merge conflicts
A conflict occurs when Git cannot automatically combine competing changes. A file may contain markers like:

```text
<<<<<<< HEAD
result = 10
=======
result = 20
>>>>>>> feature-login
```

Open the file, decide which change to keep or combine, remove the markers, stage the resolved file and complete the merge.

```bash
git add main.py
```

A conflict is not necessarily a sign that the repository is damaged; it requires a decision about how edits should be combined.

## 18. Merge vs. rebase
Merge combines branch histories and may create a merge commit:

```bash
git switch main
git merge feature
```

Rebase replays commits on a new base and can produce a linear history:

```bash
git switch feature
git rebase main
```

Rebase rewrites commit identities. Avoid rebasing shared commits unless the team understands the consequences of rewriting history.

## 19. Tags and releases
A tag identifies a particular point in repository history, often a software version.

```bash
git tag
git tag -a v1.0.0 -m "Version 1.0.0"
git show v1.0.0
git push origin v1.0.0
```

Semantic versioning commonly uses `MAJOR.MINOR.PATCH`. GitHub Releases can attach notes and downloadable files to a tag.

## 20. Common errors
| Problem | Possible action |
|---|---|
| Untracked files | Stage required files with `git add` |
| Push rejected | Fetch remote changes and integrate them |
| Merge conflict | Edit conflicting files and complete the merge |
| Wrong branch | Check using `git branch` |
| Nothing to commit | Inspect `git status` and staged changes |
| Authentication failed | Check credentials and repository permissions |

## 21. Authentication and security
GitHub can be accessed using HTTPS or SSH. HTTPS may require a personal access token; SSH uses SSH keys. Never commit passwords, API keys or private tokens. Review repository visibility and permissions. A secret already committed is not removed just by adding it to `.gitignore`.

## 22. Local practice example
The lecture includes a small calculator exercise:

```bash
mkdir calculator
cd calculator
git init
```

Create `main.py`, then run:

```bash
git status
git add main.py
git status
git commit -m "Add initial calculator"
git log --oneline
```

This practices initialization, status checking, staging, committing and viewing history.

## 23. What I learned
Git makes project changes traceable and helps keep history organized. A useful habit is to check status, review the changes, stage only the intended files and write a meaningful commit message. Branches and remotes make teamwork more manageable.

## 24. Git command checklist

```bash
git --version
git config --global user.name "Student Name"
git config --global user.email "student@example.com"
git config --global --list

mkdir my-project
cd my-project
git init

git status
git add main.py
git add .
git add file1.py file2.py
git add *.py
git diff
git diff --staged
git diff HEAD
git commit -m "message"
git log
git log --oneline
git ls-files

git mv old.py new.py
git rm old.py
git restore --staged main.py
git restore main.py
git revert COMMIT_ID

git remote add origin REPOSITORY_URL
git remote -v
git branch -M main
git push -u origin main
git clone REPOSITORY_URL
git fetch origin
git pull

git branch
git branch feature-login
git switch feature-login
git switch main
git switch -c feature-login
git merge feature-login
git rebase main

git tag
git tag -a v1.0.0 -m "Version 1.0.0"
git show v1.0.0
git push origin v1.0.0
```

## 25. Further reading
- [Git documentation](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/)