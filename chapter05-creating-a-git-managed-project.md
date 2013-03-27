# <a id="top">Creating a Git version controlled project</a>

Create a new folder / project by either creating the project structure yourself or using a build tool to create it for you:

    mkdir my-project
    mvn new my-project
    lein new my-project
    play new my-project

Change into the new folder created for your project.  Then create a new git repository using the git initialise command:

    cd my-project
    git init

You have just created an empty *local* git repository.  In effect, you have created the *.git* folder within your project that will contain all the change history and changes themselves as the project develops.  You dont need to understand what goes on in the .git folder, but you do need to remember that if you delete it then all your change history is deleted.

To see what changes you could commit to git, use the git status command:

    git status

If you have files in your project they will show up as untracked files when you do a git status.  This means that these files have yet to be put under git version control.  You will soon see that *git status* is used all the time to let you know what the current situation is with your changes.

To add files to git, you use the *git add* command.  You can specify a particular file or you can add all files at once.

To add a specific file

    git add filename.ext

To add all untracked files

    git add .

Adding files to git is not the same as doing a commit.  With *git add* you are preparing one or more files to be committed.  When you add a file, it is placed in what is called the staging area (or index).  Staging files is a useful way to group changes over multiple files in order to make a meaningful commit.  In [Chapter 7 - the local git workflow](#chapter07), we will cover the staging area and other steps in Git.

To see what files are staged at any time, you use the *git status* command.


[Back to top...](#top)

[Workshop homepage](index.html)
