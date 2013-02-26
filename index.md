Git workshop
============


Git overview
------------
Git is a very powerful tool for managing changes in text files, such as source code and configuration files.

Until recently most versioning tools for source code used a central model.  Tools like CVS and SVN  manage code changes in a shared central server and only a working copy of files checked out exist on your development machine.

Git uses a distributed approach to managing changes (as does bazar & mercurial).  This may seem more complicated at first, but adds far more power and flexibility.

A distributed model means that everyone involved gets a complete copy of the project repository.  It is still common to have a shared repository that holds all the code, although this can easily be changed.

Using Git, developers create a copy of a project repository on their development machine, this is called cloning.  This creates a local copy of the repository, including all the code changes and full history.

One of the benefits of git therefore is to be able to constantly commit changes, regardless of if you are connected to a shared repository.  You commit all your changes locally first (even if you are connected) and then when ready push your changes to a shared repository.

It is common to have a common shared repository that is seen as the canonical version of the code of a project.  The core members of the project team have direct access to update the code (committers).  Anyone ith access to the project repository can take a copy (clone).

Should you wish to work on the project you can create your own copy, a fork and commit changes to that project directly.

Should you wish to submit your chages back to the original project, you can create a pull request.  This is a request for the original project team to pull in the changes from your forked repository.




Set up git client
-----------------

www.git-scm
git for windows
git for mac
apt-get install git


Create an account on Github
---------------------------
go to www.github.com
create an account
create & upload your public key


Git configuration
-----------------
set your user name and email

We will cover setting up aliases later


First version controlled project
--------------------------------

Create a new folder / project

Initialise a git repository
git init

See what changes you have
git status




Removing files from staging / index
-----------------------------------
You can remove a file you have put in staging (git add filename) using the git command reset

git reset --soft HEAD^


rolling back to the previous commit on the local repo
git reset HEAD~1


To remove a file from the index
-------------------------------
git rm --cached peter.txt


Conflict resolution
-------------------
Sometimes when you merge the changes between one commit and another make it impossible to do this automatically.

If you have a pull request that cant be automatically merged.  A committer on the project can offer suggestions on how the submitter can fix the pull request so it can be merged.  This typically includes
* ensuring the submitter of the pull request has pulled all the changes down from the latest version of the original project.
* merging any changes between their code and the original project

Once any merge conflicts are resolved, the submitter of the pull request can do another commit locally and to their forked repository on github and that will update the pull request automatically.



Collaborating with Git
=======================================================

Everyone has their own repository locally

Everyone has their own local development environment - using their ide & foreman

Developers can spin up another application on heroku as a different environment

Use environment variables to manage different environments

Branch & merge
Rebasing (I dont like doing this on shared repos, your loosing tracability because you are rewriting history).


Can use ... from labs to automatically deploy onto heroku from Github - probably dont want to do this for production - or at least make sure than anyone who triggers an automatic deploy knows that they are doing so.
