# Git

## What is Git?

Git is a version control system that allows you to track changes to files and folders over time. It is a distributed version control system, which means that the entire codebase and history is available on every developer's computer, which allows for easy branching and merging.

## Why use Git?

Git is a powerful tool that allows you to track changes to your codebase over time. It allows you to easily collaborate with other developers, and it allows you to easily revert changes if something goes wrong.

## GitHub

GitHub is a web-based hosting service for Git repositories. It provides a web interface for managing Git repositories, and it provides a web interface for managing issues and pull requests.

## Connect git to github

- Set name and email

```bash
git config --global user.name "Your Name"
git config --global user.email "Your Email"
```

- Logout from git

```bash
git config --global --unset user.name
git config --global --unset user.email
git config --global --unset credential.helper
```

### Using GitHub

- Create a git repository on GitHub Example: test-repo
- We can clone the repository to our local machine or push an existing repository to GitHub

#### Cloning a repository

```bash
git clone https://github.com/chanthornsp/test-repo.git
```

#### Pushing an existing repository

- cd into the directory
- Initialize the directory as a git repository

```bash
git init
```

- Add the files to the repository

```bash
git add .
```

- Commit the files to the repository

```bash
git commit -m "Initial commit"
```

- Add Branch name main

```bash
git branch -M main
```

- Add remote repository

```bash
git remote add origin https://github.com/chanthornsp/test-repo.git
```

- Push the files to the repository

```bash
git push -u origin main
```

## Basic Git Commands

- `git init` - Initialize a git repository
- `git add` - Add files to the staging area
- `git commit` - Commit changes to the repository
- `git status` - Show the status of the repository
- `git log` - Show the commit history
- `git branch` - List, create, or delete branches
- `git checkout` - Switch branches or restore working tree files
- `git merge` - Join two or more development histories together
- `git pull` - Fetch from and integrate with another repository or a local branch
- `git push` - Update remote refs along with associated objects
