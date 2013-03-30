

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
