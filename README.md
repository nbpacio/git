# Git Usage Guide

This guide covers two common scenarios for working with Git repositories.

## Setting Up SSH Keys for GitHub

Before you can push code to GitHub using SSH (the `git@github.com:` URLs shown in this guide), you need to set up SSH keys. SSH keys provide a secure way to authenticate with GitHub without entering your password each time.

### Why SSH Keys?

SSH keys are recommended over HTTPS for Git operations because they:
- Provide secure authentication without passwords
- Allow seamless push/pull operations
- Are more secure than password authentication

### Step 1: Check for Existing SSH Keys

First, check if you already have SSH keys:

```bash
# List existing SSH keys
ls -al ~/.ssh
```

Look for files named `id_rsa.pub`, `id_ecdsa.pub`, or `id_ed25519.pub`. If you see one of these, you can skip to Step 3.

### Step 2: Generate a New SSH Key

If you don't have an SSH key, generate one:

```bash
# Generate a new SSH key (replace with your GitHub email)
ssh-keygen -t ed25519 -C "your_email@example.com"

# If your system doesn't support Ed25519, use RSA:
# ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

When prompted:
1. Press Enter to accept the default file location (`~/.ssh/id_ed25519`)
2. Enter a secure passphrase (optional but recommended)
3. Confirm the passphrase

### Step 3: Add Your SSH Key to the SSH Agent

Start the SSH agent and add your key:

```bash
# Start the SSH agent in the background
eval "$(ssh-agent -s)" - LINUX
Start-Service ssh-agent - WINDOWS

# Add your SSH private key to the ssh-agent
ssh-add ~/.ssh/id_ed25519 - LINUX
ssh-add .ssh/id_ed25519 - WINDOWS

# If you used RSA, use:
# ssh-add ~/.ssh/id_rsa
```

### Step 4: Add Your SSH Key to GitHub

1. Copy your SSH public key to the clipboard:

```bash
# Copy the SSH key to clipboard (Linux)
cat ~/.ssh/id_ed25519.pub

# On macOS, you can use:
# pbcopy < ~/.ssh/id_ed25519.pub

# On Windows (Git Bash), you can use:
clip < ~/.ssh/id_ed25519.pub - LINUX
Get-Content .ssh/id_ed25519.pub | clip - WINDOWS

```

2. Go to GitHub and add the key:
   - Navigate to **Settings** > **SSH and GPG keys** > **New SSH key**
   - Give your key a descriptive title (e.g., "My Laptop")
   - Paste your key into the "Key" field
   - Click **Add SSH key**

### Step 5: Test Your SSH Connection

Verify that your SSH key is working:

```bash
# Test SSH connection to GitHub
ssh -T git@github.com
```

You should see a message like: `Hi username! You've successfully authenticated, but GitHub does not provide shell access.`

### Additional Resources

For more detailed information, see the official GitHub documentation:
- [Generating a new SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- [Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
- [Testing your SSH connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)

---

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

-END OF FILE-
