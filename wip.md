

# Testing branches

Say you want to test out your branch you have been working on but your setup is only configured to work on master, then you can push a branch from one repository to the master (or any other branch) of another repository.


For example, heroku only deploys from master.  You can use git to deploy your *developing* branch to your *heroku-test* application using the following notation:

    git push repository local-branch:remote-branch

    git push heroku-test developing:master

In this example we are pushing the local *developing* branch to the master branch of the heroku-test remote repository.  This allows you to use heroku-test application to run some web application tests (eg. selinum).  

You dont need to merge your developing branch until after you are happy with oyour testing.




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
