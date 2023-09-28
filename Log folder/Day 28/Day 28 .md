# Day 28

Tags: Github
Date: July 30, 2023
Status: Done

Tasks of the day 

- **[ETHParis**: Fundamentals of Dapp Development with Joseph Delong](https://www.youtube.com/watch?v=KRjvwLXrwKM&list=PLXzKMXK2aHh4BgIXgD0CVPP53d1mMrQRJ)
- Github & Markdown
- Git Branching
- Git Teamwork
- Deploying website using Git and Github
- Best practices for Github repositories
- Collaborating with the Github community
- Github Features: Issues, CLI, & Actions
- Review: Learn Git & Github

---

## Video of the day

### Fundamentals of Dapp development with Joseph Delong

[https://www.youtube.com/watch?v=KRjvwLXrwKM&list=PLXzKMXK2aHh4BgIXgD0CVPP53d1mMrQRJ](https://www.youtube.com/watch?v=KRjvwLXrwKM&list=PLXzKMXK2aHh4BgIXgD0CVPP53d1mMrQRJ)

## Notes

### Github & Markdown

[https://www.youtube.com/watch?v=f49LJV1i-_w](https://www.youtube.com/watch?v=f49LJV1i-_w)

## **Differences between HTML and Markdown**

Markdown translates to HTML, but Markdown is not a replacement for HTML. Markdown’s syntax can be converted to a small subset of HTML tags to do things like format text, add links, display images, and more. You can even incorporate HTML elements inside a Markdown document. To render Markdown in HTML, though, you would need a tool called a Markdown parser (more about this parser later on).

## **Markdown Applications**

Since Markdown has gained a lot of popularity, you will find Markdown content being accepted in many applications.

- Website publishers that accept Markdown content include [Wordpress.com](https://wordpress.com/support/can-i-use-markdown-on-wordpress-com), [Ghost](https://www.markdownguide.org/tools/ghost/) and [BeakerBrowser](https://beakerbrowser.com/docs/guides/create-a-markdown-site). Tools such as [Jekyll](https://www.markdownguide.org/tools/jekyll/), [Docusaurus](https://www.markdownguide.org/tools/docusaurus/) and [MkDocs](https://www.markdownguide.org/tools/mkdocs/)can convert Markdown documents into a static website geared for technical documentation. Take a look at this [page](https://daringfireball.net/projects/markdown/basics) rendered in HTML, and its text [source](https://daringfireball.net/projects/markdown/basics.text) styled in Markdown.
- Book publishers such as [LeanHub](http://help.leanpub.com/en/articles/2941344-leanpub-flavoured-markdown-vs-markua-for-writing-in-plain-text) accepts Markdown manuscripts and convert them to books for publication.
- Slide-show presentations such as [Remark](https://remarkjs.com/) and [Cleaver](https://jdan.github.io/cleaver/#2) can convert Markdown slides into HTML for web viewing.

## **The Markdown Flavors**

Because the core Markdown language supports only a subset of HTML features, many independent developers have extended the Markdown syntax to incorporate more HTML compatibilities and customize it for their own organizations. Here are a few popular flavors of Markdown:

- [CommonMark](https://commonmark.org/) is a body of special-interest developers who work side-by-side on a proposal to standardize the Markdown syntax and offer extensive test suites to validate Markdown implementations against this specification. This standard has been used by other developers to base their code upon.
- GitHub Flavored Markup, or [GFM](https://github.github.com/gfm/) is GitHub’s expanded dialect of Markdown based on CommonMark and is used throughout the GitHub platform by its active community.
- [Trello](https://help.trello.com/article/821-using-markdown-in-trello), a popular collaborative tool that organizes and tracks information through virtual boards and cards, implements a custom version of Markdown as well.

[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

---

****How To Write a Good README for Your Project****

This article explains the purpose, conventional structure, and proper formatting of a README file, and best practices to follow when writing one.

## **Conventions of a Good README File**

Your README file should be as good as your project itself.

Make your project stand out and look professional by at least including the following elements in your README:

- **Project Title**: the name of your project
- **Description**: This is an extremely important component of the README. You should describe the main purpose of your project. Answer questions like “why did you build this project?” and “what problem(s) does it solve?”. It also helps to include your motivations for the project and what you learned from it.
- **Features**: If your project has multiple features, list them here. Don’t be afraid to brag if your project has unique features that make it stand out. You can even add screenshots and gifs to show off the features.
- **How to use**: Here, you should write step-by-step instructions on how to install and use your project. Any software or package requirements should also be listed here.
- **Technologies**: List all the technologies and/or frameworks you used and what purpose they serve in your project.
- **Collaborators**: If others have contributed to your project in any way, it is important to give them credit for their work. Write your team members’ or collaborators’ names here along with a link to their GitHub profile.
- **License**: It’s also important to list a license on your README so other developers can understand what they can and cannot do with your project. You can use [this guide](https://choosealicense.com/) to help you choose a license.

****What are Docs?****

[Codecademy Docs](https://www.codecademy.com/resources/docs) is a free, easily accessible reference for coding terms and concepts, available to developers all over the world.

**GIT BRANCHING**

## **Generalizations**

Let’s take a moment to review the main concepts and commands from the lesson before moving on.

- Git *branching* allows users to experiment with different versions of a project by checking out separate *branches* to work on.

The following commands are useful in the Git branch workflow.

- `git branch`: Lists all a Git project’s branches.
- `git branch branch_name`: Creates a new branch.
- `git checkout branch_name`: Used to switch from one branch to another.
- `git merge branch_name`: Used to join file changes from one branch to another.
- `git branch -d branch_name`: Deletes the branch specified.

---

**GIT TEAMWORK**

## **Generalizations**

Congratulations, you now know enough to start collaborating on Git projects! Let’s review.

- A *remote* is a Git repository that lives *outside* your Git project folder. Remotes can live on the web, on a shared network or even in a separate folder on your local computer.
- The *Git Collaborative Workflow* are steps that enable smooth project development when multiple collaborators are working on the same Git project.

We also learned the following commands

- `git clone`: Creates a local copy of a remote.
- `git remote -v`: Lists a Git project’s remotes.
- `git fetch`: Fetches work from the remote into the local copy.
- `git merge origin/master`: Merges `origin/master` into your local branch.
- `git push origin <branch_name>`: Pushes a local branch to the `origin` remote.

Git projects are usually managed on Github, a website that hosts Git projects for millions of users. With Github you can access your projects from anywhere in the world by using the basic workflow you learned here.

---

## **Deployment on GitHub Pages**

Deploying to GitHub Pages is automatic. Once it’s set up, deploying happens whenever you push your local changes to your remote, GitHub-hosted repository. Head to GitHub Pages’ [setup instructions](https://pages.github.com/) and follow the steps exactly to get your main GitHub Pages page setup.

When you first navigate to your newly deployed site it is possible that you will receive a 404 error. If this happens, and you are confident that you have followed all the steps as written, check back in 30 minutes to see if the deploy has successfully gone through.

---

## ****How To Write a Good Pull Request****

### What is a pull request?

Sonia, a new member of Codecademy’s engineering team, has just finished a snazzy navigation menu on a branch titled, “sonia_feature_navigation_menu”. Her changes will not be merged to the main branch until her pull request is approved. A [pull request](https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) is a feature of GitHub and other source code management tools to review code before merging it from one branch to another, usually the main branch.

When Sonia creates a new pull request, her repository will automatically be set as the source repository and the project’s repository will be set as the destination repository. She will get the option to specify the source branch and the destination branch. She will be greeted with a preview of the changes between the two codebases and whether the branches can be merged automatically depending on code conflicts. In the Pull Request description field, Sonia must describe the code changes and what feature(s) this merge will add to the main branch.

Sonia’s proposed changes can then be accepted or rejected by her teammates. Each pull request has its own discussion forum, creating a place for collaborators to leave feedback. They will review Sonia’s code, suggest what should be removed or changed, and how her code can be simplified or improved. Any further commits Sonia makes to the source branch will automatically be reflected in the pull request. Once her changes are accepted by the project’s collaborators, her branch can be merged into the repository’s main branch. GitHub will keep this pull request in history as a record of the code change, Sonia’s contribution, and the discussion that took place.

This pull request process is not only a way to increase group knowledge or improve product quality but also an exceptional way to develop professional skills through group critique. Next, we will discuss how to write a good pull request.

### **Follow a Pull Request Structure – What, Why, and How?**

Concisely explain the purpose of the pull request in the title. If the pull request adds a new feature, go for something like “Add frontend component for settings page”. If it’s to fix a typo, be specific and say “Fix name typos on the Contact Us page”.

The description is where all the juicy details are. You want the reviewers to know the thought process behind code changes and the options you have considered. It also helps to embed screenshots, GIFs, or even videos of your application so reviewers can anticipate what the code change in the pull request looks like.

Some developers even have preconfigured templates or checklists on their repositories to ensure all pull requests contain just the relevant information. Following these guidelines help speed up collaborative critiques so the code can get merged faster!

Examples of pullrequests

- A short pull request to [remove trailing spaces](https://github.com/Codecademy/docs/pull/384) on the Codecademy [docs](https://github.com/Codecademy/docs)repository which is immediately approved.
- A long pull request to [add a new component](https://github.com/Codecademy/gamut/pull/1598) on the Codecademy [gamut](https://github.com/Codecademy/gamut)repository which includes screenshots, comments, and a lively discussion before being approved

---

## ****How To Use Git Rebase****

**Learn how to use Git Rebase in order to rewrite the history of your repository.**

When working with a Git repository, there will be a time when we need to combine changes from a working branch into another one. This can be accomplished with the use of the commands **`merge`** or  **`rebase`**. In this article, we’ll focus on **`rebase`** and see how it can work some magic in order to manage the future development of a product by simplifying git history.

### What is Git rebase

At a high level, rebasing can be understood as “moving the base of a branch onto a different position”. Think of it like a redo - “I meant to start here”.

A high level, rebasing can be understood as “moving the base of a branch onto a different position”. Think of it like redo.

Consider that a team just completed a production release. While working on a completely new feature branch called **`new_feature`**, a co-worker finds a bug in the production release (**`main`** branch). In order to fix this, a team member creates a **`quick_fix`** branch, squashes the bug, and merges their code in to the **`main`** branch. At this point, the **`main`** branch and the **`new_feature`** branch have diverged and they each have a different commit history. We can visualize this in the image below:

![https://static-assets.codecademy.com/Courses/learn-git-github/git-rebase/before-rebase.svg](https://static-assets.codecademy.com/Courses/learn-git-github/git-rebase/before-rebase.svg)

If we want to bring the updated changes from **`main`** into **`new_feature`** one could use the **`merge`** command, but with **`rebase`** we can keep the Git commit history clean and easy to follow. By “rebasing” the **`new_feature`** branch onto the **`main`** one, we move all the changes made from **`new_feature`** to the front of **`main`** and incorporate the new commits by rewriting its history. We can see how this is done below:

![https://static-assets.codecademy.com/Courses/learn-git-github/git-rebase/after-rebase.svg](https://static-assets.codecademy.com/Courses/learn-git-github/git-rebase/after-rebase.svg)

We can see above that the new “base” of our “new_feature” branch is the updated main branch with the previous changes from the bug fix implemented.

One of the major benefits of using Git rebase is that it eliminates unnecessary merge commits required by **`git merge`**. Most importantly, the history of the changes made in the main repository remains linear and follows a clear path of changes. This allows us to navigate the changes easier when viewing the changes in a **`log`** or **`graph`**.

### Merge vs Rebase

Although **`git rebase`** is an extremely useful tool to keep a Git repository clean and easy to follow, it doesn’t mean that one should *always* stick to that command when integrating code changes. Let’s go over the definitions of **`rebase`** and **`merge`** one more time:

- Git rebase: Reapplies commits on top of another base branch.
- Git merge: joins two or more development histories together (creating a new merge commit).

![https://static-assets.codecademy.com/Courses/learn-git-github/git-rebase/git-merge-vs-git-rebase.svg](https://static-assets.codecademy.com/Courses/learn-git-github/git-rebase/git-merge-vs-git-rebase.svg)

Generally, it’s useful to use **`merge`** whenever we want to add changes of a branch **back** into the base branch. And **`rebase`** is useful whenever we want to add **changes of a base branch** back to a branched out branch.

[https://www.youtube.com/watch?v=85Lx8s_i4Yk&t=3s](https://www.youtube.com/watch?v=85Lx8s_i4Yk&t=3s)

---

### Managing a Github Repository

## **Tools**

So far, we’ve already discussed the GitHub features we will be using most of the time. However, GitHub has a ton of advanced tools and settings we should definitely take advantage of. While we will not be diving deep into these, we still want you to be aware of them so you can revisit them when the need arises. Each of the following features has a dedicated tab in the GitHub repository settings:

- **Security & Analysis**: We can enable or disable a variety of security features for our repository.
- **[Webhooks](https://docs.github.com/en/developers/webhooks-and-events/webhooks/about-webhooks)**: We can use webhooks to get notifications when certain events happen.
- **Notifications**: We can receive email notifications when push events are triggered.
- **Integrations**: Any open source applications we use to extend our GitHub workflow or any third-party tools we integrate with GitHub will appear here. For example, Slack or CircleCI.
- **[Deploy Keys](https://docs.github.com/en/developers/overview/managing-deploy-keys#deploy-keys)**: We can use the SSH keys generated here to grant servers access to a repository for deployment.
- **Actions**: [GitHub Actions](https://docs.github.com/en/actions) is a powerful tool to automate, customize, and execute software workflows such as testing The [Actions tab](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository) allows us to change the permissions.
- **Secrets**: Secrets are encrypted environment variables that can be used in Actions.
- **Pages**: GitHub [Pages](https://pages.github.com/) allows us to host simple web pages straight from the repository.

---

## ****What is a .gitignore file?****

### **Why use a .gitignore file?**

Each line in **.gitignore** corresponds to a file, directory, or pattern we would like to ignore when staging. Using a **.gitignore** file results in cleaner staging areas and prevent files containing sensitive information from being committed. Some of the files or folders we should ignore include:

- Configuration files with API or secret keys such as **.env**
- Compiled binary files or production directories such as **build** or **dist**
- Log files
- Dependencies downloaded from a package manager such as **node_modules**
- System files such as **thumbs.db** on Windows or **.DS_Store** on macOS

### **.gitignore Patterns**

We can take advantage of [patterns](https://git-scm.com/docs/gitignore#_pattern_format) to match multiple filenames. These help us handle special cases such as ignoring specific file types or ignoring all but one file inside a directory.

---

### Forking a Repository

[https://www.youtube.com/watch?v=WEyVM7rAyjo&embeds_referring_euri=https://www.codecademy.com/&source_ve_path=Mjg2NjY&feature=emb_logo](https://www.youtube.com/watch?v=WEyVM7rAyjo&embeds_referring_euri=https://www.codecademy.com/&source_ve_path=Mjg2NjY&feature=emb_logo)

---

# **Project Prompt**

## **Contributing to the Codecademy Docs Repository**

Codecademy Docs is a free and open-contribution resource that contains entries spanning many common languages, libraries, frameworks, and more. Users worldwide are encouraged to share their knowledge and expertise by creating an entry about a chosen topic. In this project, we will show you how to break up the task of contributing an entry into bite-sized sub-tasks so that you too can make a contribution. The steps to contribute are explained in detail in [this article](https://dev.to/codecademy/how-to-contribute-to-codecademy-docs-1a77).

Contributing to Codecademy Docs is an excellent way for beginners to practice their GitHub and open-source contribution skills. It also looks great to potential employers!

---

### Project Management: Issues and Projects

An example of a laid-out GitHub project board is [Github’s own public roadmap project](https://github.com/orgs/github/projects/4247/views/1), shown next. This is an example of a Project with no repository, as a roadmap can be used for organizational purposes.

---

# **Review**

Congratulations on reaching the end of this course!

Through lessons, projects, articles, and tutorials, you’ve practiced using basic Git commands in the terminal to add version control to your project.

You’ve learned how to integrate Git with GitHub, one of the most-used web applications by developers across the world to collaborate in teams and share code.

These are all the skills we’ve practiced:

- Create a Git project and setup a remote copy on GitHub. Label code changes and move between different versions of your project.
- Write text on the GitHub interface using Markdown to describe your project and code changes.
- Create branches in your Git project so you can collaborate with others.
- Use Git commands to make sure your local copy of code matches the remote copy on GitHub.
- Use GitHub pull requests to discuss code changes with others.
- Be familiar with Git rebase, GitHub repository settings, and how to keep a remote repository organized.
- Create a GitHub profile and explore code written by others
- Be familiar with intermediate to advanced GitHub features that allow you manage tasks within GitHub itself and automate actions.

Through the off-platform projects, you’ve used your GitHub account to interact with several repositories. We encourage you to continue the streak of uploading and contributing to code! Explore GitHub and setup your next team project with Git & GitHub!

At this point, feel free to go back to any of this course to gain some practice.