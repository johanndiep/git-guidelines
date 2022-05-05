# Oxford Dynamics Github Guidelines

This repository stores the guidelines for working with Github at Oxford Dynamics.

## Introduction to Git

These links covers the basics for managing and versioning your software projects. 
* Follow this [tutorial](https://www.theodinproject.com/lessons/foundations-setting-up-git) in order to create a Github account as well as install and setup Git on your laptop. 
* Follow this [tutorial](https://www.theodinproject.com/lessons/foundations-git-basics) in order to create a repository and connect it to your local machine.

In the following, the most common Git Bash commands are summarized:

### Local Git initialization

In case you want to start a project repository locally and update it to Github at a later stage. 

```console
git init
```

### Adding changes to the staging area

```console
git add <new_files>
```

### Committing to the local repository

```console
git commit -m "<comment>"
```

### Updating the remote repository

```console
git push
```

### Updating a specific branch of the remote repository 

```console
git push origin <branch>
```

### Updating local repository with a specific branch of the remote repository

```console
git pull origin <branch>
```

### Checking the current status 

The git status command displays the state of the working directory and the staging area.

```console
git status
```


## Gitflow Workflow

![Gitflow](https://i.imgur.com/pcb2IrK.png)

The goal is to encapsulate feature development in order to not disturb the main codebase. Instead of commiting directly to the master branch, developers create a seperate branches for a new features. In this context, Gitflow is a suggested workflow for managing larger projects with scheduled release cycle. Specifically, it assigns specific roles and interaction rules to different types of branches. For more information, refer to the following documentation by Bitbucket: 

* [Introduction to Gitflow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

**Develop and Master Branches**

There are two branches to record the history of the project. The master branch (light blue) stores the official release history (tagged with a version number), while the develop branch (purple) is used for integration of new features. At the beginning of a project, a parallel develop branch can be created locally and pushed to the server by the following bash command.

```console
git branch develop git push -u origin develop
```

**Feature Branches**

New features should reside in their own branches (green), which can be pushed to the central repository for backup and collaboration. Here, they should use develop as their parent branch. 

```console
git checkout develop git checkout -b feature_branch
```

After a feature is completed, the corresponding feature branch gets merged back into develop.

```console
git checkout develop git merge feature_branch
```

**Release Branches**

Once develop has acquired enough features for a release, a release branch (cyan) is forked off of develop. 

```console
git checkout develop git checkout -b release/0.1.0
```

In the release branch, no new features can be added. Only bug fixes, documentation generation and other release-oriented tasks should go into this branch. Once this process is completed, the release branch gets merged into master (tagged with a version number) as well as back into develop.

```console
git checkout master git merge release/0.1.0
git checkout develop git merge release/0.1.0
```

**Hotfix Branches**

A hotflix branch (orange) is used to quickly patch production releases. In contrast to release branches, hotflix branches are based on master. Dedicated lines for bug fixes are ideal for avoiding interruption with the rest of the development within a team.   

```console
git checkout master git checkout -b hotfix_branch
```

As soon as the fix is complete, it should merged into both master (tagged with a version number) and develop (or the current release branch).

```console
git checkout master git merge hotfix_branch 
git checkout develop git merge hotfix_branch
```

## To-Check

- [ ] Github Enterprise
