# ALXprodev-advanced_git - Git-Flow Project

## Overview

Git-Flow is a branching model for Git, proposed by Vincent Driessen, that helps developers manage features, releases, and hotfixes in a consistent and scalable way. It introduces well-defined roles for branches and helps teams coordinate code changes more effectively. Git-Flow is particularly beneficial for large-scale projects where multiple developers work simultaneously on various aspects of the codebase.

## What is Git-Flow?

Git-Flow revolves around five primary branch types:

- **main** (or master) – production-ready code
- **develop** – ongoing development
- **feature/\*** – new features in progress
- **release/\*** – preparation for production releases
- **hotfix/\*** – critical bug fixes on the main branch

## Relevance in the Development Process

Git-Flow improves:

- **Code organization** by clearly separating development stages
- **Team collaboration** through structured branching and merging workflows
- **Code stability** by allowing features to be tested and integrated before reaching production
- **Release management** by isolating release-specific tasks

Git-Flow is widely adopted in agile and CI/CD environments, ensuring seamless integration and deployment pipelines while reducing conflicts and regression bugs.

## Learning Objectives

By the end of this project, learners should be able to:

- Understand the purpose and structure of Git-Flow
- Identify the different branch types and their roles
- Apply Git-Flow in real-world collaborative development projects
- Manage feature development, hotfixes, and release cycles using Git best practices

## Learning Outcomes

Learners will be able to:

- Explain how Git-Flow helps manage large codebases and team contributions
- Create and manage branches following the Git-Flow model
- Use Git commands to initiate features, releases, and hotfix branches
- Integrate Git-Flow into CI/CD pipelines for automated testing and deployments

## Prerequisites

- Git installed on your system
- GitHub account
- Basic understanding of Git commands

## Installation

### 1. Install Git-Flow

**On macOS (using Homebrew):**

```bash
brew install git-flow-avh
```

**On Linux (Ubuntu/Debian):**

```bash
sudo apt-get install git-flow
```

**On Windows:**
Download and install from [Git-Flow for Windows](https://github.com/nvie/gitflow/wiki/Windows)

**Alternative Installation (using Git):**

```bash
# Clone the git-flow repository
git clone --recursive https://github.com/nvie/gitflow.git
cd gitflow
sudo make install
```

### 2. Verify Installation

```bash
git flow version
```

## Project Setup

### Initial Setup

1. **Create and clone the repository:**

   ```bash
   # Create an empty repository on GitHub named: ALXprodev-advanced_git
   git clone <your-repository-url>
   cd ALXprodev-advanced_git
   ```

2. **Create and push the develop branch:**

   ```bash
   git checkout -b develop
   git push -u origin develop
   ```

3. **Initialize Git-Flow:**

   ```bash
   git flow init -d
   ```

   This command uses default settings:

   - Branch name for production releases: `main`
   - Branch name for "next release" development: `develop`
   - Feature branches: `feature/`
   - Release branches: `release/`
   - Hotfix branches: `hotfix/`
   - Support branches: `support/`
   - Version tag prefix: (empty)

4. **Create and commit README.md:**
   ```bash
   touch README.md
   git add README.md
   git commit -m "docs: initial README.md"
   git push
   ```

## Git-Flow Branch Structure

```
main (production)
  │
  ├── develop (integration)
  │   ├── feature/implement-login
  │   ├── feature/implement-signup
  │   └── release/1.0.0
  │
  └── hotfix/1.0.1 (emergency fixes)
```

## Common Git-Flow Commands

### Feature Branches

```bash
# Start a new feature branch
git flow feature start <feature-name>

# Example: Start login feature
git flow feature start implement-login

# Finish a feature (merges into develop)
git flow feature finish <feature-name>

# Publish feature to remote
git flow feature publish <feature-name>
```

### Release Branches

```bash
# Start a new release branch
git flow release start <version>

# Example: Start release 1.0.0
git flow release start 1.0.0

# Finish a release (merges into main and develop, creates tag)
git flow release finish <version>

# Publish release to remote
git flow release publish <version>
```

### Hotfix Branches

```bash
# Start a new hotfix branch
git flow hotfix start <version>

# Example: Start hotfix 1.0.1
git flow hotfix start 1.0.1

# Finish a hotfix (merges into main and develop, creates tag)
git flow hotfix finish <version>
```

### Support Branches

```bash
# Start a support branch
git flow support start <version> <base>
```

## Git-Flow Best Practices

| Best Practice                     | Description                                                                                  |
| --------------------------------- | -------------------------------------------------------------------------------------------- |
| **Start with develop**            | Always branch off from develop for new features, not main                                    |
| **Feature Isolation**             | Keep each feature in its own branch to reduce merge conflicts                                |
| **Merge via Pull Requests**       | Use pull/merge requests for all merges to ensure code review                                 |
| **Keep main clean**               | Only production-ready code goes into main. Never push untested code here                     |
| **Tag Releases**                  | Use Git tags on the main branch to mark official release points                              |
| **Use hotfix/\* for urgent bugs** | Apply emergency fixes directly to main via a hotfix/ branch and merge them back into develop |
| **Document your workflow**        | Maintain clear documentation of your Git-Flow in your project's README or internal wiki      |

## Project Tasks

### Task 0: Setting up Git-Flow

✅ **Objective:** Understand and initialize a GitFlow workflow

**Steps:**

1. Install git-flow if not already installed
2. Create an empty repository `ALXprodev-advanced_git`
3. Clone your repository to have it available locally
4. Create a branch `develop`
5. Push the develop branch to the remote repository
6. Initialize Git Flow within the repository using default settings: `git flow init -d`
7. Create an empty README.md file
8. Commit your file to staging and push

**Files:**

- `README.md`

### Task 1: Creating a Feature Branch

✅ **Objective:** Learn how to work with feature branches in GitFlow

**Steps:**

1. Create a new feature branch `feature/implement-login` from the develop branch
2. In the `feature/implement-login` create a new directory called `login-page`
3. Inside `login-page`, create a `README.md` file with the message: `Login Feature Coming soon`
4. Commit your changes and push to GitHub
5. Use commit message: `feat: scaffolding login page`

**Files:**

- `login-page/README.md`

**Commands:**

```bash
git flow feature start implement-login
mkdir login-page
echo "Login Feature Coming soon" > login-page/README.md
git add login-page/README.md
git commit -m "feat: scaffolding login page"
git flow feature publish implement-login
```

### Task 2: Creating a Release Branch

✅ **Objective:** Understand the release process in GitFlow

**Steps:**

1. Create a new feature branch `feature/implement-signup` from the develop branch
2. Create a directory called `signup-page` with a `README.md` file with the message: `feature coming soon`
3. Commit the changes and push to GitHub
4. Merge the 2 branches (`feature/implement-login` and `feature/implement-signup`) to the develop branch. Fix conflicts if any
5. Create a new release branch `release/1.0.0`
6. Make changes to `signup-page/README.md` file by adding the following text: `data requirements: email, firstName, lastName, profilePic` inside the release branch
7. Commit and push changes to GitHub
8. Merge the release branch to the main branch and the develop branch
9. Tag the release with `v1.0.0` and push the tags to the remote repository

**Files:**

- `login-page/README.md`
- `signup-page/README.md`

**Commands:**

```bash
# Create signup feature
git flow feature start implement-signup
mkdir signup-page
echo "feature coming soon" > signup-page/README.md
git add signup-page/README.md
git commit -m "feat: scaffolding signup page"
git flow feature publish implement-signup

# Merge features to develop
git checkout develop
git merge feature/implement-login
git merge feature/implement-signup
# Fix conflicts if any
git push origin develop

# Create release branch
git flow release start 1.0.0

# Update signup README
echo -e "feature coming soon\ndata requirements: email, firstName, lastName, profilePic" > signup-page/README.md
git add signup-page/README.md
git commit -m "docs: add data requirements to signup page"
git flow release publish 1.0.0

# Finish release (merges to main and develop, creates tag)
git flow release finish 1.0.0

# Push tags
git push origin --tags
git push origin main
git push origin develop
```

### Task 3: Git Hooks and Automation

✅ **Objective:** Implement Git hooks to automate parts of the GitFlow process

**Steps:**

1. Implement a pre-commit hook in the file `.git/hooks/pre-commit` that checks if each directory in a Git repository has a README file
2. Implement a post-merge hook that logs the merge after completing a merge into the main branch

**Files:**

- `.git/hooks/pre-commit`
- `.git/hooks/post-merge`

**Pre-commit Hook Example:**

```bash
#!/bin/bash
# .git/hooks/pre-commit

# Check if each directory has a README file
for dir in $(find . -type d -not -path '*/\.*' -not -path '.'); do
    if [ ! -f "$dir/README.md" ] && [ ! -f "$dir/README" ] && [ ! -f "$dir/readme.md" ]; then
        echo "Error: Directory $dir does not have a README file"
        exit 1
    fi
done

exit 0
```

**Post-merge Hook Example:**

```bash
#!/bin/bash
# .git/hooks/post-merge

# Check if merge was into main branch
current_branch=$(git rev-parse --abbrev-ref HEAD)

if [ "$current_branch" = "main" ]; then
    echo "Merge completed into main branch at $(date)" >> .git/merge-log.txt
    echo "Merge logged to .git/merge-log.txt"
fi
```

**Making Hooks Executable:**

```bash
chmod +x .git/hooks/pre-commit
chmod +x .git/hooks/post-merge
```

## Project Structure

```
ALXprodev-advanced_git/
│
├── .git/
│   └── hooks/
│       ├── pre-commit          # Pre-commit hook for README validation
│       └── post-merge          # Post-merge hook for main branch logging
│
├── login-page/
│   └── README.md               # Login feature documentation
│
├── signup-page/
│   └── README.md               # Signup feature documentation
│
└── README.md                   # This file
```

## Branch Workflow Diagram

```
main ──────────────────────────────────────● (v1.0.0)
 │                                          │
 │                                          │
develop ────────────●───────────────────────●
         │          │                       │
         │          │                       │
         │    feature/implement-login       │
         │          │                       │
         │          ●                       │
         │                                  │
         │    feature/implement-signup      │
         │          │                       │
         │          ●                       │
         │                                  │
         │    release/1.0.0                 │
         │          │                       │
         │          ●───────────────────────●
```

## Commit Message Convention

This project follows conventional commit messages:

- `feat:` - A new feature
- `fix:` - A bug fix
- `docs:` - Documentation only changes
- `style:` - Code style changes (formatting, missing semi colons, etc)
- `refactor:` - Code refactoring
- `perf:` - Performance improvements
- `test:` - Adding or updating tests
- `chore:` - Changes to build process or auxiliary tools

## Troubleshooting

### Common Issues

**Issue: Git-Flow command not found**

```bash
# Solution: Install git-flow using your package manager
# See Installation section above
```

**Issue: Merge conflicts**

```bash
# Resolve conflicts manually, then:
git add .
git commit -m "fix: resolve merge conflicts"
```

**Issue: Hooks not executing**

```bash
# Make sure hooks are executable:
chmod +x .git/hooks/pre-commit
chmod +x .git/hooks/post-merge
```

## Resources

- [Git-Flow Documentation](https://github.com/nvie/gitflow)
- [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)
- [Git Hooks Documentation](https://git-scm.com/docs/githooks)
- [Conventional Commits](https://www.conventionalcommits.org/)

## Thanks 

**Happy coding! ✨**
