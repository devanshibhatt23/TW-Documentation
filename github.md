# GitHub – Hosting and Collaboration

## 1. Introduction
GitHub is an online platform for hosting Git repositories and collaborating on software projects. Git tracks file changes and commits, while GitHub hosts remote repositories and provides tools for teamwork.

## 2. Main features
A GitHub repository page commonly provides:
- **Code:** project files and directories.
- **Issues:** bug reports, questions and task discussions.
- **Pull requests:** proposed changes for review.
- **Actions:** automated workflows and checks.
- **Settings:** permissions and repository configuration.

GitHub Projects can help organize tasks and track progress.

## 3. Creating an account and repository
1. Visit [github.com](https://github.com/).
2. Create an account and verify the email if prompted.
3. Enable two-factor authentication for better security.
4. Select **New repository**.
5. Enter a repository name.
6. Choose public or private visibility.
7. Optionally add a README and `.gitignore`.
8. Create the repository.

A public repository can be viewed by anyone. A private repository is limited to authorized users.

## 4. README file
A README introduces the project and explains how to use it. It is usually written in Markdown and appears on the repository's main page.

A useful README may contain the project purpose, features, installation requirements, usage examples, contributors and licensing information.

```markdown
# Calculator

A simple Python calculator.

## Features
- Addition
- Subtraction

## Run
python main.py
```

## 5. Connecting a local repository
After creating a remote repository on GitHub, connect it to the local repository:

```bash
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git remote -v
git branch -M main
git push -u origin main
```

Replace the placeholders with the actual values. The local repository must contain commits, the remote must be configured, and the user must have permission to push.

## 6. Cloning a repository
Cloning creates a local copy of a remote repository, including its history.

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
```

This is useful when starting work on a project that already exists on GitHub.

## 7. Fetching and pulling
```bash
git fetch origin
git pull
```

Fetch downloads remote updates without integrating them into the current branch. Pull fetches and integrates the changes. Fetch is useful when I want to inspect updates first.

## 8. Branches and pull requests
A branch keeps feature work separate from the main branch. After making and testing changes, push the branch and open a pull request.

```bash
git switch -c feature-login
# Make and test changes
git add .
git commit -m "Add login feature"
git push -u origin feature-login
```

On GitHub, create a pull request with `main` as the base branch and `feature-login` as the compare branch. Explain the changes, request a review, address feedback and merge after approval.

A pull request is not the same as the `git pull` command. A pull request is a review and integration process on a hosting platform.

## 9. Code review
Code review helps improve code quality before changes are integrated. A reviewer checks correctness, identifies possible bugs, suggests improvements and verifies tests and readability. The contributor explains the changes, responds to feedback and updates the branch.

Pull requests should be focused and small enough to review comfortably.

## 10. Fork vs. clone
| Fork | Clone |
|---|---|
| Creates a separate hosted repository copy | Creates a local repository copy |
| Happens on GitHub or another hosting platform | Happens on the local computer |
| Useful for independent contributions | Useful for local development |

A common open-source workflow is to fork a project, clone the fork, make changes and propose them to the original project through a pull request.

## 11. Issues and Projects
GitHub Issues help teams report bugs, suggest features, assign tasks and discuss possible solutions. An issue should have a clear title and enough detail for another contributor to understand it.

GitHub Projects organizes work using tables or board views. A simple board might have these statuses:

| Status | Example task |
|---|---|
| Todo | Design calculator interface |
| In Progress | Implement division |
| In Review | Review input validation |
| Done | Write project README |

Projects can link tasks to Issues and pull requests.

## 12. Tags and releases
Git tags identify important points in repository history, often software versions. GitHub Releases can attach notes and downloadable files to a version tag.

```bash
git tag -a v1.0.0 -m "Version 1.0.0"
git push origin v1.0.0
```

## 13. Security
GitHub repositories can use HTTPS or SSH. Personal access tokens and SSH private keys must be kept private. Never commit passwords, API keys or tokens. Check repository visibility and permissions before sharing.

## 14. Complete collaborative workflow
1. Create or clone a repository.
2. Create a branch for a feature.
3. Modify files and test the changes.
4. Stage and commit the changes.
5. Push the branch to GitHub.
6. Open a pull request and request review.
7. Address feedback.
8. Merge the approved changes.

```text
Edit → Stage → Commit → Push → Review → Merge
```

## 15. What I learned
GitHub makes it easier to share projects and work with other people. Branches isolate new work, commits record changes and pull requests provide a place for review before integration. Issues and Projects help organize tasks, while a README introduces the repository to visitors.

## 16. Further reading
- [GitHub Docs](https://docs.github.com/)
- [Git documentation](https://git-scm.com/doc)
