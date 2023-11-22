# Day 80

Tags: Front-end, Github
Date: October 2, 2023
Status: Done

**Task of the day**

Version control systems

- Git

Repo hosting services

- Github
- Gitlab
- BitBucket

Frontend Frameworks

- React
- Angular
- Vue

---

### Version control systems

Version control, also known as source control, is the practice of tracking and managing changes to software code. Version control systems are software tools that help software teams manage changes to source code over time. As development environments have accelerated, version control systems help software teams work faster and smarter. They are especially useful for [DevOps](https://www.atlassian.com/devops/what-is-devops) teams since they help them to reduce development time and increase successful deployments.

Version control software keeps track of every modification to the code in a special kind of database. If a mistake is made, developers can turn back the clock and compare earlier versions of the code to help fix the mistake while minimizing disruption to all team members.

Software developers working in teams are continually writing new source code and changing existing source code. The code for a project, app or software component is typically organized in a folder structure or "file tree". One developer on the team may be working on a new feature while another developer fixes an unrelated bug by changing code, each developer may make their changes in several parts of the file tree.

Version control helps teams solve these kinds of problems, tracking every individual change by each contributor and helping prevent concurrent work from conflicting. Changes made in one part of the software can be incompatible with those made by another developer working at the same time. This problem should be discovered and solved in an orderly manner without blocking the work of the rest of the team. Further, in all software development, any change can introduce new bugs on its own and new software can't be trusted until it's tested. So testing and development proceed together until a new version is ready.

Good version control software supports a developer's preferred workflow without imposing one particular way of working. Ideally it also works on any platform, rather than dictate what operating system or tool chain developers must use. Great version control systems facilitate a smooth and continuous flow of changes to the code rather than the frustrating and clumsy mechanism of file locking - giving the green light to one developer at the expense of blocking the progress of others.

Software teams that do not use any form of version control often run into problems like not knowing which changes that have been made are available to users or the creation of incompatible changes between two unrelated pieces of work that must then be painstakingly untangled and reworked. If you're a developer who has never used version control you may have added versions to your files, perhaps with suffixes like "final" or "latest" and then had to later deal with a new final version. Perhaps you've commented out code blocks because you want to disable certain functionality without deleting the code, fearing that there may be a use for it later. Version control is a way out of these problems.

Version control software is an essential part of the every-day of the modern software team's professional practices. Individual software developers who are accustomed to working with a capable version control system in their teams typically recognize the incredible value version control also gives them even on small solo projects. Once accustomed to the powerful benefits of version control systems, many developers wouldn't consider working without it even for non-software projects.

**Benefits of version control systems**

Using version control software is a best practice for high performing software and [DevOps](https://www.atlassian.com/devops/what-is-devops) teams. Version control also helps developers move faster and allows software teams to preserve efficiency and agility as the team scales to include more developers.

Version Control Systems (VCS) have seen great improvements over the past few decades and some are better than others. VCS are sometimes known as SCM (Source Code Management) tools or RCS (Revision Control System). One of the most popular VCS tools in use today is called Git. Git is a *Distributed* VCS, a category known as DVCS, more on that later. Like many of the most popular VCS systems available today, Git is free and open source. Regardless of what they are called, or which system is used, the primary benefits you should expect from version control are as follows.

1. **A complete long-term change history of every file**. This means every change made by many individuals over the years. Changes include the creation and deletion of files as well as edits to their contents. Different VCS tools differ on how well they handle renaming and moving of files. This history should also include the author, date and written notes on the purpose of each change. Having the complete history enables going back to previous versions to help in root cause analysis for bugs and it is crucial when needing to fix problems in older versions of software. If the software is being actively worked on, almost everything can be considered an "older version" of the software.
2. **Branching and merging**. Having team members work concurrently is a no-brainer, but even individuals working on their own can benefit from the ability to work on independent streams of changes. Creating a "branch" in VCS tools keeps multiple streams of work independent from each other while also providing the facility to merge that work back together, enabling developers to verify that the changes on each branch do not conflict. Many software teams adopt a practice of branching for each feature or perhaps branching for each release, or both. There are many different workflows that teams can choose from when they decide how to make use of branching and merging facilities in VCS.
3. **Traceability**. Being able to trace each change made to the software and connect it to project management and bug tracking software such as [Jira](https://www.atlassian.com/software/jira), and being able to annotate each change with a message describing the purpose and intent of the change can help not only with root cause analysis and other forensics. Having the annotated history of the code at your fingertips when you are reading the code, trying to understand what it is doing and why it is so designed can enable developers to make correct and harmonious changes that are in accord with the intended long-term design of the system. This can be especially important for working effectively with legacy code and is crucial in enabling developers to estimate future work with any accuracy.

While it is possible to develop software without using any version control, doing so subjects the project to a huge risk that no professional team would be advised to accept. So the question is not whether to use version control but which version control system to use.

Visit the following resources to learn more:

- **[Git](https://git-scm.com/)**
- **[Mercurial](https://www.mercurial-scm.org/)**
- **[What is Version Control?](https://www.atlassian.com/git/tutorials/what-is-version-control)**

---

### Repo hosting services

When working on a team, you often need a remote place to put your code so others can access it, create their own branches, and create or review pull requests. These services often include issue tracking, code review, and continuous integration features. A few popular choices are GitHub, GitLab, BitBucket, and AWS CodeCommit.

**How to choose the best source code repository**

- **Choosing a repository tool:** There are a variety of modern software repository hosting tools available to choose from. Each code repository system has its own strength and weaknesses. Additionally, each repository hosting tool has various support for underlying version control systems. This guide is intended to walk you through the requirements that may impact which code repository management tool is best suited for your team’s needs.

**The difference between a repository hosting services and a version control system.**

It’s important to acknowledge that repository hosting services and version control systems are two separate entities. Version control systems are the low level command line utilities that are used to manage the software development life cycle changes to a collection of sources code files.

Repository hosting services are third-party web applications that wrap and enhance a version control system. You cannot fully utilize a repository hosting service without using an underlying version control system.

---

### Frontend Frameworks

Web frameworks are designed to write web applications. Frameworks are collections of libraries that aid in the development of a software product or website. Frameworks for web application development are collections of various tools. Frameworks vary in their capabilities and functions, depending on the tasks set. They define the structure, establish the rules, and provide the development tools required.

[https://www.youtube.com/watch?v=D_MO9vIRBcA](https://www.youtube.com/watch?v=D_MO9vIRBcA)

Visit the following resources to learn more:

- **[Web3 Frontend – Everything You Need to Learn About Building Dapp Frontends](https://moralis.io/web3-frontend-everything-you-need-to-learn-about-building-dapp-frontends/)**
- **[What is the difference between a framework and a library?](https://www.youtube.com/watch?v=D_MO9vIRBcA)**
- **[Which JS Framework is best?](https://www.youtube.com/watch?v=cuHDQhDhvPE)**

---