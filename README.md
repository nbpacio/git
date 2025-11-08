# Git Usage Guide

This guide covers two common scenarios for working with Git repositories.

## A. Creating a New Repository on the Command Line

Use this approach when you're starting a project from scratch locally:

```bash
# Create a README file
echo "# TESTING" >> README.md

# Initialize a new Git repository
git init

# Stage the README file
git add README.md

# Create your first commit
git commit -m "first commit"

# Rename the default branch to 'main'
git branch -M main

# Add remote repository (skip if repository was created on GitHub)
# Use this command only when the repository was created locally
git remote add origin git@github.com:nbpacio/TESTING.git

# Push your commits to the remote repository
git push -u origin main
```

**Note:** The `git remote add origin` command should be skipped if you created the repository on GitHub first. Use it only when you've created the repository locally and need to connect it to a GitHub repository.

## B. Pushing an Existing Repository from the Command Line

Use this approach when you already have a local repository with commits:

```bash
# Add the remote repository
git remote add origin git@github.com:nbpacio/TESTING.git

# Rename the current branch to 'main'
git branch -M main

# Push your commits to the remote repository
git push -u origin main
```

## Key Commands Explained

- `git init` - Initializes a new Git repository in the current directory
- `git add` - Stages files for commit
- `git commit -m "message"` - Creates a commit with the staged changes
- `git branch -M main` - Renames the current branch to 'main'
- `git remote add origin <url>` - Connects your local repository to a remote repository
- `git push -u origin main` - Pushes your commits to the remote repository and sets up tracking

## When to Use Each Approach

- **Approach A**: Starting a brand new project locally
- **Approach B**: You have an existing local repository that needs to be pushed towards GitHub


## To push changes from a local main branch to a remote master branch on GitHub
Assuming you have made commits on your local main branch and wish to integrate them into the master branch on the remote repository, follow these steps: 
 
## Switch to the master branch.

    git checkout master

## Pull the latest changes from the remote master branch: This ensures your local master is up-to-date before merging.

    git pull origin master

## Merge the main branch into master.


    git merge main

## This command integrates the changes from your local main branch into your local master branch. Resolve any merge conflicts that may arise during this step.
Push the updated master branch to the remote repository:

    git push origin master

## This command sends your local master branch, now containing the changes from main, to the master branch on your GitHub repository.
