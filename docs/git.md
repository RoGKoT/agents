---
name: Git
description: Branch management and workflow for Git
---

# Git — Branch Management and Workflow

# Branching Strategy
- main is the common reference branch:
  - stable
  - clean
  - starting point for new agents branches
  - no direct development

# Branch names and contents
## Main (main)
  Only common and base files to all branchs
## Full (full)
  All workspace files
## Release (release)
  Production's files only
  Mainly .github/agents/ and .github/prompts/ folders
  Do not merge the root development workspace into release.
## Agent Name (agent-name)
  Agent files
## Subagent Name (subagent-name)
  Agent and subagent files


# [*Conflicts*](#conflicts)
  Always resolve any conflict prior to proceeding.
  Always use rebase to keep a clean history and avoid merge commits.
  git stash push -m "Explicit Label"
  git switch <branch>
  git stash pop
  [backup](#backup)

# [*Create*](#create)
  git switch [<source branch>](#source-branchs-derivation)
  git branch <new branch>
  git switch <branch>

# [*Satisfied Customer*](#satisfied-customer)
  Always commit/push/stash any modification to current branch prior to work elsewhere.
  Always resolve any conflict prior to proceeding.
  Prior to do any modification 
    Always check all status (branchs, remote tracking, etc.). 
    Always check all status are up to date.
    Ensure active branch is correct.
  Ensure right parent branch before deriving a new branch from it.

# [*Backup*](#backup)
  Usually done after work on <branch>.
  if not, [refer to](#satisfied-customer), git switch <branch>
  git add <files>
  git commit -m "Explicit Comment"
  git push -u origin <branch>
  always merge in `full`
  merge in `release` only the necessary production files, typically `.github/agents/...` and `.github/prompts/...`
  never merge in `main`

# [*Merge*](#merge)
  # Usual use case
    ▸ source: agents
    ▸ target: full, release
  # Or
    ▸ source: main
    ▸ target: agents
  git fetch origin  
  git switch <source branch>
    git pull --rebase
    git push --force-with-lease, if needed
  git switch <target branch>
    git pull --rebase
    git push --force-with-lease, if needed
  git merge <source branch>
  - Resolve any conflict if needed
  git push  origin <target branch>

# [*Rebase*](#rebase)
  # Only use if
    ↳ branch is not shared
    ↳ branch history is not clean
    ↳ All collaborators are aware of the rebase and its implications
  # Usual use case
    ▸ source: main
    ▸ target: agents
  git fetch origin  
  git switch <source branch>
    git pull --rebase
    git push --force-with-lease, if needed
  git switch <target branch>
    git pull --rebase
    git push --force-with-lease, if needed
  git rebase <source branch>
  git push --force-with-lease origin <target branch>

# [Source Branchs Derivation](#source-branchs-derivation)
  `main` for a new agent
  `<agent-name>` for a new subagent
  For nested subagents, derive from the parent agent branch, e.g. `time-management/timestamps`

# New Agent/Prompt Work Process
  [Create branch for agent/the prompt and make it active](#create)  

# Modification Agent/Prompt Work Process
  [🔎](#satisfied-customer) before starting any modification on an existing branch.

# Workflow
  rebase/merge from `main` when needed
  development
  tests/validation
  [save your work](#backup)


# Usefuls commands
  rename branch : git branch -m <old-name> <new-name>
  delete branch : git branch -d <branch-name>
  remove staged files (git add) : git restore --staged <file>
  active branch status: git status : état de la branche courante
  all local branches status:  git branch -vv
  remote tracking status: git remote show origin 