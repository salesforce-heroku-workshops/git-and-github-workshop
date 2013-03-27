<link href="index.css" rel="stylesheet" type="text/css">

# <a id="top">Git workshop</a>


    Last update: March 19, 2013
    Workshop website: [http://git-and-github-workshop.herokuapp.com](http://git-and-github-workshop.herokuapp.com)


This workshop will give you an introduction to using the Git version control tool for managing changes to source code and configuration files.  It will also cover collaborating in teams using Github public repositories.

* [Chapter 1: Git overview](#chapter1)
* [Chapter 2: Choose your git client](chapter2-choose-your-git-client.html)
* [Chapter 3: Create an account on Github](chapter3-create-accont-on-github.html)
* [Chapter 4: Identify yourself to Git](chapter04-identify-yourself-to-git.html)
* [Chapter 5: Creating a Git managed project](chapter05-git-managed-project.html)
* [Chapter 6: Ignoring files](#chapter6)
* [Chapter 7: The local git workflow](#chapter7)
* [Appendix A: Where to go next](#appendix-a)


# <a id="#chapter1">Git overview</a>

Git is a very powerful tool for managing the changes you make as you develop a software projects.  Typically those changes tracked are the ones made to source code and configuration files.  Git understands how to merge text files together, allowing you to pull in changes from others.  It also helps you compare changes in different versions of text files using the diff tool.

You can also manage binary files such as images and propriatory document formats, although git does not typically come with tools that help you merge or compare differences.

Before the creation of Git (and Mercurial, Bazar and a few others), most versioning tools for source code used what is called a central model.  Tools like CVS and SVN manage code changes in a single central server, shared across teams and the whole company.  When developers work on code they only get a copy of current code locally on their development machine.  To actually do any commits, to version the code, then they have to connect with the server.  When looking at history and any other activitiy, developers have to communicate with the central server.  If this server is off line or slow, then this can lead to problems working effectively together as a team.

Git uses a distributed approach to managing changes (as does bazar & mercurial).  This approach may seema little more complicated at first, but adds far more control and visiblity to your projects.

A distributed model means that everyone involved gets a complete copy of the project repository.  It is still common to have a shared repository that holds all the code (e.g. on Github), although this can easily be changed and may evolve over time.

Using Git, developers create a copy of a project repository on their development machine, this is called *cloning*.  This creates a local copy of the repository along with all the files managed by git in your project.  As you have a local repository, all the code changes that  have ever been made are right there giving you a full history of the project.

One of the benefits of git therefore is to be able to constantly commit changes, regardless of if you are connected to a shared repository.  You commit all your changes locally first (even if you are connected) and then when ready you can push your changes to a shared repository.

It is common to have a common shared repository that is seen as the canonical version of the code for a project.  The core members of the project team, refered to as *committers* have direct access to update this shared repository.  Anyone with access to the project repository can take a copy (clone).

Should you wish to work on the project you can create your own copy, called a fork.  Your fork is your own exact copy of the oringinal repository, including all the history.  As this is your repository, you can commit changes directly.

Should you wish to submit your chages back to the original project, you can create a pull request from your fork.  A pull request is a message and one or more commits that are sent to the original project team, inviting them to pull in the changes from your forked repository.

[Back to top...](#top)







# <a id="chapter6">Ignoring files</a>

There are often files inside your project that you do not want to put into git, these typically includes

* Backup files
* Developer tool configurations
* Compiled source code
* Graphics, sound and video files
* Binary document formats

Telling Git to exclude these types of files will prevent them appearing in your git status report as *untracked files* and help you focus on managing those files that should be versioned.

You can add your project exclusions using filennames, folders and filename patterns.  All these exclusions go into a project file called

    my-project-folder/.gitignore

To keep your project .gitignore file simple and focused on the project, any files and patterns you want to ignore that are created by your own development environment (IDE, build tools, etc.) should be placed in a global ignore file, typically:

    ~/.gitignore_global

Github has a [large collection of .gitignore files](https://github.com/github/gitignore/) for different programming languages and tools.


[Back to top...](#top)



# <a id="chapter7">The local git workflow</a>

To recap, we have our working copy of our files on our laptop.  When we add those files using git, a copy is placed in what git calls Staging.  This allows you to assemble several files for the commit.

As we have a local repository right there on our laptop, we can commit all the files added to the staging area.  If you can add a series of small commits and do this often, it gives you a more detaled version history and gives you more points to jump back in time.  Regular commits helps to reduce merge conflicts when working in teams and using smaller commits gives other developers lots of details about how the project has evolved.

In this visual representation you can see the different git stages in which commits can reside.

<img src="images/git-cheat-sheet-visual-git-stages.png">


## Understanding git add and the staging area

When you add a file, you are telling git that you want it to be part of the change you are going to commit.

Lets say you create a new file with 10 lines of content and then use *git add filenname.ext* to add it to git.  Then you continue to add another 5 lines the contents of that file.  If you do a commit without adding that file to git again, only the first 10 lines of content will be in that commit.

If you do a second *git add filenname.ext* before you commit, then all 15 lines of content will be included in the commit.

Having to add changes in this way helps you control exactly what makes up your commit without restricting the files you are working on.  Please note that it is advisable to either git add & git commit often so that your changes form part of a meaningful history.


## What has been added - What has changed (using diff)

Once you have added files to the staging area with *git add*, you can compare any changes made to files in your workspace.  Using git diff you can see all changes or specifying a file will show only the differences in that one file.

    git diff
    git diff filename

You can also compare the files you have added to the staging area to those you have committed using the diff option *--staging*

    git diff --staging
    git diff --staging filename




## Removing files from staging / index

You can remove a file you have put in staging (git add filename) using the git command reset

    git reset --soft HEAD^


rolling back to the previous commit on the local repo
    git reset HEAD~1


## To remove a file from the index


    git rm --cached filename.txt






# Conflict resolution - managing the merge process

Sometimes when you merge the changes between one commit and another make it impossible to do this automatically.

If you have a pull request that cant be automatically merged.  A committer on the project can offer suggestions on how the submitter can fix the pull request so it can be merged.  This typically includes
* ensuring the submitter of the pull request has pulled all the changes down from the latest version of the original project.
* merging any changes between their code and the original project

Once any merge conflicts are resolved, the submitter of the pull request can do another commit locally and to their forked repository on github and that will update the pull request automatically.


[Back to top...](#top)

Collaborating with Git
======================

Everyone has their own repository locally

Everyone has their own local development environment - using their ide & foreman

Developers can spin up another application on heroku as a different environment.  Every time a new heorku app is created, a new git repository is created.  This gives a lot of flexibility when it comes to managing changes, although you need to manage the progression of your changes through each repository.

Using git log --decorate you can see the relative progression of your changes as commits to each repositories.

When you are working with multiple heroku applications, then using environment variables will allow you to manage resource configuration in each environment.  Hard coding configuration information in your application will not lead to a very secure, stable or scalable application.



Keeping up to date with changes

https://help.github.com/articles/dealing-with-non-fast-forward-errors



[Back to top...](#top)



Branch & merge
--------------

Unless branches represent a completely isolated component in your project, then branches should be short lived.  This makes them easier to work with, easier to merge and easier to get rid of when you dont need them.

Rebasing (I dont like doing this on shared repos, your loosing tracability because you are rewriting history).  There may be some merit when a team is working very closely on the same part of the code, where there is a lot of communicaton going on.


Can use ... from labs to automatically deploy onto heroku from Github - probably dont want to do this for production - or at least make sure than anyone who triggers an automatic deploy knows that they are doing so.


[Back to top...](#top)




additional topics

    Repositories
    Commits
    Viewing changes
    Alias
    Going forward to fix mistakes
    Tags
    Remotes
    Github
    Branching & merging - when to do it
    Stashing
    Rebasing is evil !!!
    Cherry picking
    Patches
    Bisect
    Rerere
    Blame
    Common workflows
    Continuous Integration with Travis
