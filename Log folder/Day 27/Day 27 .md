# Day 27

Tags: Github
Date: July 29, 2023
Status: Done

Tasks of the day

- ****[Creative Summit | AI Ethics - which lessons to draw for the new economy - Imane Bello](https://www.youtube.com/watch?v=Uhp2ASUuXQM&list=PLXzKMXK2aHh4ReviSGoUdlMYSsc1iRfAm&index=35)****
- ****Introduction: Git & GitHub****
- Learned Git functions + basic github flow
********

---

### **Introduction to our Learn Git & GitHub course.**

[https://www.youtube.com/watch?v=eNw8MgguLsQ&t=4s](https://www.youtube.com/watch?v=eNw8MgguLsQ&t=4s)

The video includes examples of using cloning repositories, Git terminal commands such as `git log`, `git commit`, and `git add`, as well as GitHub features like pull requests, pull request reviews, and adding collaborators to repositories.

## **Git Workflow**

Nice! We have a Git project. A Git project can be thought of as having three parts:

1. A *Working Directory*: where you’ll be doing all the work: creating, editing, deleting and organizing files
2. A *Staging Area*: where you’ll list changes you make to the working directory
3. A *Repository*: where Git permanently stores those changes as different *versions* of the project

**BASIC GIT WORKFLOW**

## **Generalizations**

You have now been introduced to the fundamental Git workflow. You learned a lot! Let’s take a moment to generalize:

- Git is the industry-standard version control system for web developers
- Use Git commands to help keep track of changes made to a project:
    - `git init` creates a new Git repository
    - `git status` inspects the contents of the working directory and staging area
    - `git add` adds files from the working directory to the staging area
    - `git diff` shows the difference between the working directory and the staging area
    - `git commit` permanently stores file changes from the staging area in the repository
    - `git log` shows a list of all previous commits
    
    ---
    
    ### ****Handy Git Operations****
    
    ****Git stash****
    
    When working on experimental code on a new branch, you may realize that you forgot to add something to a previous commit. However, you cannot switch branches unless you are at a clean commit point. To avoid losing your local changes, use `git stash` to temporarily save your work before updating the previous commit and retrieving your changes later.
    
    ![https://static-assets.codecademy.com/Courses/learn-git-github/handy-git-operations/git-stash-pop-diagram.svg](https://static-assets.codecademy.com/Courses/learn-git-github/handy-git-operations/git-stash-pop-diagram.svg)
    
    ### ****Git log****
    
    • **`git log --oneline`** shows the list of commits in one line format.
    
    • **`git log -S "keyword"`** displays a list of commits that contain the keyword in the message. In the screenshot below, we use **`git log -S "Add"`** to find any commits with “Add” in the message.
    
    • **`git log --oneline --graph`** - **`--graph`** Displays a visual representation of how the branches and commits were created in order to help you make sense of your repository history. When used alone, the description can be very lengthy, so you can combine the command with **`--oneline`** in order to shorten the description.
    
    ### Git commit amend
    
    Git's `-amend` flag is useful for correcting mistakes and updating commits without creating a new one. For example, if you realize you missed a few semicolons after committing your work on a lengthy feature, you can stage your changes with `git add` and then use `git commit --amend` to update your previous commit instead of creating a new one. It's important to note that `-amend` actually replaces the whole previous commit, so your terminal editor will ask you to update your commit message.
    
    ---
    
    ## ****What is GitHub?****
    
    This tutorial refers to Git and GitHub repeatedly. *Git* is a widely-used version control system used to manage code. Git allows you to save drafts of your code so that you can look back at previous versions and potentially undo complicated errors. A project managed with Git is called a *Git repository*.
    
    *GitHub* is a popular hosting service for Git repositories. GitHub allows you to store your local Git repositories in the cloud. With GitHub, you can backup your personal files, share your code, and collaborate with others.
    
    In short, GitHub is a tool for working with Git. There are other services to host Git repositories, but GitHub is a trusted, free service used by organizations across the world, big and small.