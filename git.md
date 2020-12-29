# Git Version Control

## DEFINITIONS

- Git: Version control software
- Github: Server to store repositories
- Repository (Repo): Place to store codes
- Commit: Save file
- Commit hash: Personal identifier for the commit
- Branch: Ramification of the master branc
- Pull request: Suggests that the master pull your branch to incorporate
- Merge: The action of merging the branch into a master
- Fork: Copy the whole repository of another person to yours. After that pull requests can be done
- Clone: Copy a repo to your local machine

## Initial Setup

```bash
# Initial configuration
git config --global user.name "Henrique Vitoi"
git config --global user.email "hvitoi@gmail.com"
git config --list

## Start a git project
git init # Remove the folder .git to delete the git config

## Clone repository
git clone 'repo'
```

## File changes

```bash
# File change status
git status

# Show diferences between the git and the local file
git diff

# Add files to staging area
git add -A
git add .
git add 'file'

# Remove files from staging area
git rm 'file'
git reset # Remove everything
```

## Commit changes

```bash
# Commit files
git commit -m "description" # -m stands for "message"
git commit -a -m "description" # -a commits all the files
```

## Remotes

```bash
# Show information about remotes
git remote
git remote -v # verbose

# Add/remove remote
git remote add 'remote-name' 'remote-uri' # Name is usually origin
git remote remove 'remote-name' 'remote-uri'
```

## Logging

```bash
# Logs all the commits
git log
```

## Copy changes from another branch

```sh
git cherry-pick `commit-id`
```

## Pull - Push

```bash
# Pull changes from the (remote - branch)
git pull origin master

# Push changes to (remote - branch)
git push origin master
git push -u origin master # -u save remote and branch as default

# Ignore the new modifications on the remote and force push
git push origin master --force
```

- If the .git folder is deleted on the local machine, the --force parameter will wipe completely the repo including the commit history

## Navigate through version

```bash
# Go back to last commit
git stash

## Go back to previous commit
git checkout 'commit-number'
```

## Branches

```bash
# Show all branches on the repository. \* means the branch currently working on
git branch
git branch -a

# Create a new branch
git branch 'branch-name'

# Delete branch
git branch -d 'branch-name'
git push origin --delete 'branch-name' # Delete branch remotely

## Select branch
git checkout 'branch-name' # Select existing branch
git checkout -b 'brach-name' # Create and select new branch
```

## Branch merging (Pull Request)

- Merge a secondary branch (feature) into the primary branch (master)
- A PR must be made to ask the owner to merge the dev branch into the master
  - GitHub/Pull requests tab -> New pull request
  - Base (master) <- compare (dev)
- After a PR is created, all the future commits to dev branch will appear in the PR until it's closed
- `Close PR` finishes the PR with no merge
- `Merge PR` finishes the PR with merge to the master branch (all commits from dev are copied into master)
- When checking out to/from different branches the modifications are carried (moved) together! Until a commit is performed

```bash
## Merge branch into master
git merge 'branch'

## Show merged branches
git branch --merged
```

## Configure SSH

```bash
# List existing keys
ls ~/.ssh

# Create the SSD key-pair
ssh-keygen -t rsa -b 4096 -C "hvitoi@gmail.com"
# -t (type): rsa protocol
# -b (bits): bits fr the key
# -C: label/comment

- Must be run in ~/.ssh
- Accept defaults
- id_rsa (secret file and never share)
- id_rsa.pub (share with github and heroku)

# Start the ssh-agent in background (and print the process id)
eval "$(ssh-agent -s)"

# Register the SSH key
ssh-add -K ~/.ssh/id_rsa

# Add SSH key to GitHub/Gitlab -> Settings/SSH
- Title: Personal Laptop
- Key: Content of `~/.ssh/id_rsa.pub`

# Test github connection
ssh -T git@github.com # Accept 'yes'

```

## GitHub Action

- An action to be performed on triggering an event. E.g.,
  - Code pushed
  - Pull Request Created
  - Pull Request Closed
  - Repository is Forked
- Actions Tab are the Repository
  - Setup a new workflow
- Actions `main.yml` must be committed to master branch on the GitHub platform

- `Test Script`

```yml
name: tests # Name of the workflow

on: pull_request # Trigger on pull request (open, closed, updated)

jobs:
  build: # Build a container
    runs-on: ubuntu-latest # with ubuntu
    steps:
      - uses: actions/checkout@v2 # take all the code in the repo
      - run: cd auth && npm install && npm run test:ci # Run the tests for auth
```

- `secrets` must be added to Repo Settings/Secrets. E.g.
  - JWT keys
  - API keys
  - Docker credentials
- Secrets are encrypted and only exposed to selected actions
- Secrets are NOT passed to workflows triggered by PR

- `Deploy Script`

```yml
name: deploy-myservice

on:
  push:
    branches:
      - master
    paths:
      - 'myservice/**'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Setup repository
        uses: actions/checkout@v2

      - name: Build docker image
        run: docker build -t hvitoi/myservice myservice

      - name: Login to DockerHub
        run: docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD
        env:
          DOCKER_USERNAME: ${{ secrets.DOCKER_USERNAME }}
          DOCKER_PASSWORD: ${{ secrets.DOCKER_PASSWORD }}

      - name: Push image to DockerHub
        run: docker push hvitoi/myservice

      - name: Setup Digital Ocean doctl
        uses: digitalocean/action-doctl@v2
        with:
          token: ${{ secrets.DIGITALOCEAN_ACCESS_TOKEN }}

      - name: Create kubectl context
        run: doctl kubernetes cluster kubeconfig save mycluster

      - name: Restart the deployment
        run: kubectl rollout restart deployment myservice-depl
```

- A script to apply all the config files must the included
- The script to apply config files is named manifest

```yml
name: deploy-manifests

on:
  push:
    branches:
      - master
    paths:
      - 'infra/**'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Setup repository
        uses: actions/checkout@v2

      - name: Setup Digital Ocean doctl
        uses: digitalocean/action-doctl@v2
        with:
          token: ${{ secrets.DIGITALOCEAN_ACCESS_TOKEN }}

      - name: Create kubectl context
        run: doctl kubernetes cluster kubeconfig save mycluster

      - name: Apply all the config files to the Kubernetes cluster
        run: kubectl apply -f infra/k8s && kubectl apply -f infra/k8s-prod
```
