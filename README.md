# CarCar Git Tutorial POC

## Overview
This proof of concept introduces freshmen students to version control and collaboration using Git and GitHub.  
It demonstrates how GitHub Classroom and GitHub Actions can be used to distribute assignments and automate feedback.

---

## Topics Covered

### 1. Essence of Git and GitHub
- Version management and history tracking 
- Online collaboration and workflow basics 

### 2. Using GitHub
- Using the GitHub GUI
- Logging in with SSH keys or personal access tokens 
- Creating, forking, and cloning repositories 

### 3. Basic Git Usage
- Installing Git (on windows) and configuring user information
- Core commands: `add`, `commit`, `push` 
- Branching and merging 
- Updating code with `fetch`, `pull`, and `rebase` 
- Undoing changes with `reset` and `revert` 
- Using `.gitignore` 
- Pull requests, issues, and code review 

---

## Teaching Method

### Interactive Assignments
Students complete short exercises that simulate real development tasks:
- Commit and push changes 
- Submit code that passes automated checks 
- Optional (may be too hard to setup):
    - Open a pull request and request a review 
    - Resolve merge conflicts 

Assignments are distributed using **GitHub Classroom**. 
Each student receives a private repository to work in.

### Automated Feedback
GitHub Actions workflows will:
- Verify required files are present 
- Check commit messages or naming formats 
- Run tests

Example workflow (`.github/workflows/check.yml`):

```yaml
name: Check Homework Submission
on: [push]
jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Verify required file
        run: |
          if [ ! -f "homework1.txt" ]; then
            echo "Missing homework file." && exit 1
          fi
          echo "Submission verified."
