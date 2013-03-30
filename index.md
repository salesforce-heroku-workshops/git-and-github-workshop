<link href="index.css" rel="stylesheet" type="text/css">

# <a id="top">Git workshop</a>


    Last update: March 19, 2013
    Workshop website: [http://git-and-github-workshop.herokuapp.com](http://git-and-github-workshop.herokuapp.com)


This workshop will give you an introduction to using the Git version control tool for managing changes to source code and configuration files.  It will also cover collaborating in teams using Github public repositories.

* [Chapter 1: Git overview](#chapter1)
* [Chapter 2: Choose your git client](chapter02-choose-your-git-client.html)
* [Chapter 3: Create an account on Github](chapter03-create-account-on-github.html)
* [Chapter 4: Identify yourself to Git](chapter04-identify-yourself-to-git.html)
* [Chapter 5: Creating a Git managed project](chapter05-creating-a-git-managed-project.html)
* [Chapter 6: Ignoring files](chapter06-ignoring-files.html)
* [Chapter 7: The local git workflow](chapter07-local-git-workflow.html)
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
