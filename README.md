# Git basic guide and commands

## recording changed to repository
<pre>
untracked                unmodified                modified                staged
   |-------------------------|------------------------|---------------------->|
                             |----------------------->|                       |
   |<------------------------|                        |---------------------->|
                             |<-----------------------|-----------------------|
</pre>

## basic git commands
* ### Git configuration :
   * ``` git config --global user.name [user name] ``` : to set the user name on git
   * ``` git config --global user.email [user email] ``` : to set user email on git
   * ``` git config --global user.name ``` or ``` git config user.name ``` : to print the user name on git
   * ``` git config --global user.email ``` or ``` git config user.email ``` : to print user email on git

* ``` git init ``` : initializing a git repository
* ``` git branch -M main ``` : to change the name of master branch to main
* ``` git commit -m [message] ``` : to commit any changes to the code with message
* ``` git status ``` or ``` git status -s ``` :
    * to know the changes made in project
    * ``` -s ``` to print the status in short
* ``` git diff [file name] ``` : to know that what changes have been made in file of project
* ``` git log ``` : lists that how many times 'git commit' is used and the name of person who commited the changes
* ``` git show ```
* ``` git branch ``` : lists all the branches in project
* ``` git checkout -b [branch name] ``` or ``` git branch [branch name] ``` : to make a new branch
* ``` git checkout [branch name] ``` : to switch to another branch
* ``` git checkout -d [branch name] ``` : deleting a branch (note : we should be in master branch to delete any branch)
* merging two branches :
   * first switch to the branch into which you want to merge a branch using ``` git checkout [branch 1] ```
   * merge the branch using ``` git merge [branch 2] ```
   * branch 2 will be merged in branch 1
* ``` git add [file name] ``` : sending the file to staged area
* ``` git reset --[hard/soft] ```
* ``` git restore [file name] ```

* ### commands to communicate with remote repository from local pc :
   * ``` git remote add origin [project url] ``` : adding origin in local pc to [project url]
      * "project url" looks like "git@github.com:[github userame]/[repository name].git"
   * ``` git push -u origin [branch name] ``` : to push [branch name] to remote repository
   * ``` git clone [projcet url] ``` : cloning repository from remote
   * ``` git remote -v ``` : to print the remote origin on the clone
   * #### to push changes to a perticular branch :
      * switch to that branch in git bash
      * type ``` git push ```

   
## guide for open source contributiosn
* step 1 : fork the project repository into your github account in which you want to contribute
* step 2 : clone the repository into your local machine
```sh
git clone [projcet url]
```
* step 3 : make and commit changes to the local repository using git commands
* step 4 : push the repository to your github account after making changes
* step 5 : make a pull request to the author of the repository by navigating to the pull request section of the project repository
* step 6 : If author accepts the pull request then he/she will pull changes from your remote forked repository
