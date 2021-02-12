
## Chapter 3 Assignment

From this point onwards, you will be managing your assignments with `git` and submitting them through GitHub. The aim of this assignment is to get you familiarized with a common version control workflow.

#### Getting Started
Make sure you've <em>forked</em> this repository under your own GitHub account, and then clone your own repository to your computer. You will push the changes you've made to this document as submission to GitHub.

If the version control concepts or `git` commands are still confusing to you, consider re-reading and following the online notes, or check out an interactive tutorial like [Learn Git Branching](https://learngitbranching.js.org/).

#### The Assignment:
 0. Create a branch in this assignment repository named `submission`, then list all the branches you have:

    ```bash
    # git checkout -b submission

    # git branch

    ## Ouput:

    main

    submission
    ```


 1. List the current `remote` name and hyperlink destination of this assignment repository. 

    ```bash
   # git remote -v

   ## Ouput:
   
    origin https://github.com/yanistazi/version_control_assignment.git (fetch)


    origin https://github.com/yanistazi/version_control_assignment.git (push)
    ```


 2. Add a second remote destination named `upstream` to your assignment repository, `upstream` is a common name used for the repository that people have forked from, in our case, the `upstream` will be at `https://github.com/WCM-datascibasics/version_control_assignment`. List the new list of remotes after you've added the new remote. 
 
    ```bash
    
    # git remote add upstream https://github.com/WCM-datascibasics/version_control_assignment
    # git remote -v

    ## Ouput:

    origin https://github.com/yanistazi/version_control_assignment.git (fetch)
    origin https://github.com/yanistazi/version_control_assignment.git (push)
    upstream https://github.com/WCM-datascibasics/version_control_assignment (fetch)
    upstream https://github.com/WCM-datascibasics/version_control_assignment (push)
    ```


 3. Save your modifications to this file so far and create a commit indicating you've answered the first 2 questions. Then try pushing the changes to the `upstream` destination on GitHub. What happens? Explain in your own words why does this happen? What are the benefits of having this `upstream` remote added when working collaboratively?

    ```bash
    # git commit -am " answered first two questions "
    
    # git push upstream
    
    It is not working obviously because we do not want any person to modify a repository that is working well and that is why people can clone/fork and work locally and then submit a pull request for the main repository that is working well and ask the main contributors whether or not they want to integrate those changes. The benefits are that everyone can work locally, make changes but keep one upstram version that is known for sure to work well.
    
    ## Output
    
    remote: Permission to WCM-datascibasics/version_control_assignment.git denied to yanistazi.
    fatal: unable to access 'https://github.com/WCM-datascibasics/version_control_assignment/': The requested URL returned error: 403
    ```



 4. Now clone the repository for the [class website](https://github.com/WCM-datascibasics/wcm-datascibasics.github.io), and in the class website repository:
    - a. Explore the version history by visualizing it as a graph.
        ```bash
        # git log --graph --decorate --oneline
        ```

    - b. Who was the last person to modify `README.md`? (Hint: use `git log` with an argument)
        ```bash
        # git log -n 1 -- README.md 
        
        It was you :) 
        
        ## Output
        Author: Xihe Xie <axiezai@gmail.com>
        Date:   Mon Dec 28 16:01:51 2020 -0500
        readme and try new size
        ```
    
    - c. What was the commit message associated with the last modification to the `-Week 2` line of `index.md` file? (Hint: use `git blame` and `git show`, check out their help pages if you are not sure what to do)
        ```bash
            # The commit message was : added ch2 assignment.
    
            # I used :
    
            # git blame index.md
            # git show c152f3c8 index.md
        ```


 5. In the course website repository (or another repository you want to clone from GitHub), modify one of its existing files:
     - a. What happens when you do `git stash`?
       Saved working directory and index state WIP on master: 7462142 update lecture link for week 3
       Unncommited changes have been saved away and reverted for later use
       
       git stash adds changes to your local system but won't add them to the tree
     - b. What do you see when you run `git log --all --oneline` after stashing your modification?
     86878de (refs/stash) WIP on master: 7462142 update lecture link for week 3
7556346 index on master: 7462142 update lecture link for week 3
7462142 (HEAD -> master, origin/master, origin/HEAD) update lecture link for week 3

     - c. Run `git stash pop` to undo what you did with `stash`, in what scenario might this be useful?
       It is useful when there are conflicts with other changes.

 6. One common mistake when learning `git` is to commit large files that should not be managed by `git` or adding sensitive information like security keypairs for Amazon Cloud Services. Navigate back to your assignment repository and try adding a random text file to the repository, making some modifications and commits to your repository, and deleting that file from history. (Simply deleting a file with `rm` in a repository will not remove version controlled history, you may want to look at [this](https://help.github.com/articles/removing-sensitive-data-from-a-repository/))

git filter-branch --force --index-filter "git rm --cached --ignore-unmatch sensible_info.txt" --prune-empty --tag-name-filter cat -- --all
    > Perform the commits and deletion, this question will be graded based on your commit history on GitHub.


 7. Like many command line tools, `git` provides a configuration file (or dotfile) called `~/.gitconfig`. Create an alias in `~/.gitconfig` so that when you run `git graph`, you get the output of `git log --all --graph --decorate --oneline`. You can do this by directly modifying the `~/.gitconfig` file or by using the `git` command line functionality.
    ```bash
    # git config --global alias.graph "log --all --graph --decorate --oneline"
    ```
    This is also a good opportunity to turn your dotfiles folder into a version controlled repo (Use `git init` in your dotfiles folder), make it private if you have sensitive `ssh` configurations there (IP Addresses), else feel free to make it public. (This is for your own benefit, not part of the assignment grading)

 8. You can define global ignore patterns in `~/.gitignore_global` after running `git config --global core.excludesfile ~/.gitignore_global`. Do this, and set up your global `gitignore` file to ignore OS-specific or editor-specific temporary files, like `.DS_Store`, or `.vscode`. Feel free to Google around for common gitignore entries for Python projects or other projects of your interest.

    ```bash
    # .DS_Store
    .vscode
    ```

 9. Push the `submission` branch of your repository to your GitHub remote. Your remote `main`/`master` branch should be unchanged since your fork. Now go to your GitHub repository settings and add `axiezai` as a collaborator. Now create a pull request to merge the changes from `submission` to `main`/`master`, assign your TA `axiezai` as a reviewer. You will receive feedback and grades through the pull request review.
