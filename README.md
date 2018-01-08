# GitHub Workflow Activity

Participants, in teams of 2-3, work through a series of scenarios to learn how to contribute to a remote git repository using a common workflow.

The activity first has students practice contributing to a repository in which they are owners/maintainers. Later parts of the activity have the students contribute to a repository that they do not own or maintain.

## Required Resources

- Participants: 4+, working in teams of 2-3.
- Each team needs
  - A computer with
    - git installed and configured
    - A plaintext editor
    - A command-line interface
    - A browser
    - A working Internet connection with ports open for SSH, HTTPS, and HTTP
  - A GitHub account (at least one member of each team)

## Required Knowledge and Skills

Participants must be able to:

- Local git repository operations:
  - Stage changes
  - Commit changes
  - Check the status of the repository
- Command-line operations:
  - Change working directory (cd)
- Filesystem operations:
  - Create, rename, move, and delete directories and files
- Plaintext editor operations:
  - Edit and save a file

## Learning Outcomes

Participants will be able to:

- Use a common workflow to contribute code to a project on GitHub
  - Clone a local repository from a remote repository on GitHub
  - Create a remote in local repository to a remote repository
  - (advanced) Prepare a fork and local repository to contribute changes to an upstream project on GitHub
  - Prepare a branch to work on a feature or bug
    - Create a local branch
    - Push a local branch to a remote
  - Update repository with changes from upstream
    - Fetch upstream changes into local repository
    - Rebase feature branch onto upstream development branch
    - Resolve conflicts
  - Push changes to remote
  - Force push changes to remote
  - Squash commits
  - (advanced) Issue a pull-request on GitHub

## Contents

- activity.md - Activity participants work through.
- reference.md - Detailed description of the workflow.
- virefcard.pdf - Quick reference of vi commands

## Facilitation

I have found that it typically takes about 1.5 70 minute class periods to complete this activity.

Day 1:
- 5 min:
  - Form teams
  - Hand out activity.md and reference.md, one hardcopy per team
  - Hand out vi reference card
- 65 min:
  - Teams work through activity.md

Day 2:
- 5-10 min: Do a quick overview of the workflow (what does push do, what does checkout do, how are the local and remote repositories related to each other, etc.)
- 30-35 min: Continue working through activity.md

## License

(c) 2018 Amy Csizmar Dalal, modified from the original. 
(c) 2016 Darci Burdge and Stoney Jackson SOME RIGHTS RESERVED

This work is licensed under the Creative Commons Attribution-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-sa/4.0/ .
