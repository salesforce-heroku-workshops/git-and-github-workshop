<link href="index.css" rel="stylesheet" type="text/css">

<a id="top">Git workshop</a>
============================

    Document Date: March 11, 2013
    Document Home: http://git-and-github-workshop.herokuapp.com


This workshop will give you an introduction to using the Git version control tool for managing changes to source code and configuration files.  It will also cover collaborating in teams using Github public repositories.

* [Chapter 1: Git overview](#chapter1)
* [Chapter 2: Choose your git client](#chapter2)
* [Chapter 3: Create an account on Github](#chapter3)
* [Chapter 4: ](#chapter4)
* [Chapter 5: ](#chapter5)
* [Appendix A: Where to go next](#appendix-a)


<a id="#chapter1">Git overview</a>
------------
Git is a very powerful tool for managing changes in text files, such as source code and configuration files.  Binary files such as images and propriatory document formats benefit veri little from git.

Until recently most versioning tools for source code used a central model.  Tools like CVS and SVN manage code changes in a single central server, shared across teams and the whole company.  When developers work on code they only get a copy of current code locally on their development machine.  To actually do any commits to version the code then they have to connect with the server.  When looking at history and any other activitiy, developers have to communicate with the central server.

Git uses a distributed approach to managing changes (as does bazar & mercurial).  This may seem more complicated at first, but adds far more power and flexibility.

A distributed model means that everyone involved gets a complete copy of the project repository.  It is still common to have a shared repository that holds all the code, although this can easily be changed and may evolve over time.

Using Git, developers create a copy of a project repository on their development machine, this is called cloning.  This creates a local copy of the repository, including all the code changes and full history.

One of the benefits of git therefore is to be able to constantly commit changes, regardless of if you are connected to a shared repository.  You commit all your changes locally first (even if you are connected) and then when ready push your changes to a shared repository.

It is common to have a common shared repository that is seen as the canonical version of the code of a project.  The core members of the project team have direct access to update the code (committers).  Anyone with access to the project repository can take a copy (clone).

Should you wish to work on the project you can create your own copy, called a fork.  Your fork is your own exact copy of the oringinal repository, including all the history.  As this is your repository, you can commit changes directly.

Should you wish to submit your chages back to the original project, you can create a pull request from your fork.  A pull request is a message and one or more commits that are sent to the original project team, inviting them to pull in the changes from your forked repository.

[Back to top...](#top)


<a id="chapter2">Choose your git client</a>
------------------------------------------

For the workshop the command line will be used so you can focus on understanding the commands that are used.

You can follow along with either a command line or graphical git tool.  Please note that installing a graphical tool for git should also provide git on the command line, so no need to install both!

*Command Line tools*

You can simply install the git command line tools from [www.git-scm.com](http://www.gitscm.com).

If you have Ubuntu, then you can use the Ubuntu software center or install git on the command line

    apt-get install git


*GUI tools*

The simplest graphical tools to install are from Github.  If you are browsing a repository on www.github.com you will notice a "Clone in Mac" or "Clone in Windows" button at the top left of the page.  Pressing this will send you to a page offering to install the Github graphical git client for you.

[Github client for MacOSX]
[SourceTree for MacOSX]

[Github client for Microsoft Windows]
[SourceTree for Microsoft Windows] (in beta, not currently available)

[Back to top...](#top)


<a id="chapter3">Create an account on Github</a>
---------------------------
Git hub adds extra collaborate features over git, providing a *social coding* service which is an excellent resource for open source projects.

To create an account, go to www.github.com

Create an account

Anyone can get a copy of code on your public repositories, whether or not they have an account on Github.  You cont need any access permissions to do so.

Any time you add code to github it is done over a secure connection and you have to identify yourself.  This means you either have to enter your username / password quite frequently or add your account to your ide.

Rather than use your username and password, pubic key encryption can be used to identify yourself to github (and other services like [heroku](http://www.heroku.com)).  Once you have added the public key to github, every time you connect to github then that key is used to automatically identify you. uses your public / private key approach, you can create a your public key

*You can create and add your public key uisng the excellent instructions on the gthub website*


[Back to top...](#top)

Git configuration
-----------------
There are several things you can add to your git configuration, but to start with the most important ones are your git user name and email so people know who is creating commits.  To add your username and email to git, either edit the ~/.gitconfig file or run the following two commands:

    git config --global user.name "your name"
    git config --global user.email "your.name@domain.com"

To check what git configuration has already been set up (some gui clients add information), you can list all your git configurations:

    git config --list


In the git configuration you can set up aliases for commands and options you regularly use, or event call out to scripts.  You can also specify tools for merging and viewing *diffs* (differences between files and commits).  We will cover setting up aliases and other configuration options in secition ...


[Back to top...](#top)

First version controlled project
--------------------------------

Create a new folder / project

    mkdir *my-project*
    *mvn new *my-project*
    lein new *my-project*
    play new *my-project*

Initialise a git repository inside your new project.

    git init

You have just created an empty local git repository.  In effect, you have created the .git folder that will contain all the change history and changes themselves for this project.


See what changes you have to commit

    git status

If you have files in your project they will show up as untracked files when you do a git status.  This means that these files have yet to be put under git version control.

To add files to git, you use the *git add* command.  You can specify a particular file or you can add all files at once.

To add a specific file

    git add filename.ext

To add all untracked files

    git add .


Adding files to git is not the same as doing a commit.  With *git add* you are preparing one or more files to be committed.  When you add a file, it is placed in what is called staging (or the index).  Staging files is a useful way to group changes over multiple files to make a meaningful commit.

To see what files are staged at any time, you use the *git status* command.




# Using the working directory and staging

As you have a local repository right there on your laptop,



https://help.github.com/articles/dealing-with-non-fast-forward-errors



## Removing files from staging / index

You can remove a file you have put in staging (git add filename) using the git command reset

    git reset --soft HEAD^


rolling back to the previous commit on the local repo
    git reset HEAD~1


To remove a file from the index
-------------------------------

    git rm --cached filename.txt


Conflict resolution
-------------------
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
