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
  Only common files to all branchs
## Full (full)
  All workspace files
## Release (release)
  Production's files only
## Agent Name (agent-name)
  Agent files
## Subagent Name (subagent-name)
  Agent and subagent files
## Prompts Hub (prompts-hub)
  Base for prompts system (shortcuts)
## Prompt (prompt)
  Shortcut file that call agents to resolve task
  Agents involved in task resolution.

# [*Create*](#create)
  git switch [<source branch>](#source-branchs-derivation)
  git branch <new branch>
  git switch <branch>

# [*Satisfied Customer*](#satisfied-customer)
  Always commit/push/stash any modification to current branch prior to working elsewhere.
  Always check all status before beginning any work. 
  Always check that source branch is up to date before creating a new branch from it.
  Always check the active branch before working on it.
  Always check the active branch before deriving a new branch from it.
  Always resolve any conflict prior to proceeding.

# [*Backup*](#backup)
  Usually done after work on <branch>.
  if not, [refer to](#satisfied-customer), git switch <branch>
  git add <files>
  git commit -m "Explicit Comment"
  git push -u origin <branch>

# [*Merge*](#merge)
  source is to merge from
  target is to merge into
  git switch <source branch>
  git pull
  git switch <target branch>
  git pull
  git merge <source branch>
  Resolve any conflict if needed
  git push origin <target branch>

# [Source Branchs Derivation](#source-branchs-derivation)
  `main` for a new agent
  `prompts-hub` for a new prompt
  <agent-name> for a new subagent 

# New Agent/Prompt Work Process
  [Create branch for agent/the prompt and make it active](#create)  

# Modification Agent/Prompt Work Process
  [Check](#satisfied-customer) before starting any modification on an existing branch.

# Workflow
  Development
  Tests / Validation
  [Save your work](#backup)
  Merge in `full`
  Merge in `release`
  Never merge in `main`

# Usefuls commands
  rename branch : git branch -m <old-name> <new-name>
  delete branch : git branch -d <branch-name>
  remove staged files (git add) : git restore --staged <file>
  active branch status: git status : état de la branche courante
  all local branches status:  git branch -vv
  remote tracking status: git remote show origin 