# What is Git?
A version control system typicaly used in software engineering. Keeps track of changes... makes it easier to revert back to previous versions. Makes it easier for collaboration or working on new features in parallel.

# Installing Git
Mac OS: `brew install git`
Verify Intallation: `git --version`

# Initializing a Git Repo
Navigate to your project directory and enter: `git init`

# Linking local Git Repo to Github 
Create a new repo in GitHub.
Then link your local repo to the GitHub repository: `git remote add origin github_url`

Verify remote connection: `git remote -v`

Push to remote GitHub repo: 
`git push origin branch_name`

# Checking Status
`git status`

# Committing Changes
Stage a change:
`git add filename.txt`

Stage all changes: `git add -A`

Commit: `git commit -m "message"`

# Branching
Create and move to a new branch: `git chekcout -b branch_name`

Make changes and commit as usualy withing the new branch. 

See existing branch: `git branch`

Deleting a branch: `git branch -d branch_name`

# .gitignore
- A `.gitignore` file tells Git which files or directories to ignore when tracking changes. Lives in the root of your repo. 
  ```
  .DS_Store
  __pycache__/
  *.pyc
  ```