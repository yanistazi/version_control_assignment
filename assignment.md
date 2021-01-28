## Chapter 3 Assignment

From this point onwards, you will be managing your assignments with `git` and submitting them through GitHub. The aim of this assignment is to get you familiarized with the common version control workflow.

#### Getting Started
Make sure you've <em>forked</em> this repository under your own GitHub account, and then clone your own repository to your computer. Complete the assignment by modifying this file in your <em>own branch</em> and create the appropriate commits as you see fit, you will push the changes you've made in your own branch as submission to GitHub.

If the version control concepts or `git` commands are still confusing to you, consider re-reading and following the online notes, or check out an interactive tutorial like [Learn Git Branching](https://learngitbranching.js.org/).

#### The Assignment:
 1. Use `git` to list the current `remote` destination of this assignment repository. 

    ```bash
    # your git command and output here
    ```


 2. Add a second remote destination named `upstream` to your assignment repository, `upstream` is a common name used for the repository that people forked from, in our case, the `upstream` will be at `https://github.com/WCM-datascibasics/version_control_assignment`. List the new list of remotes after you've added the new remote. 
 
    ```bash
    # list the new list of remotes here
    ```

 3. Save your modifications to this file so far and create a commit indicating you've answered the first 2 questions. Then try pushing the changes to the `upstream` destination on GitHub. What happens? Explain in your own words why does this happen? What are the benefits of having this `upstream` remote added when working collaboratively?

 > Your answer here


 4. Now clone the repository for the [class website](https://github.com/WCM-datascibasics/wcm-datascibasics.github.io), and in the class website repository:
    - a. Explore the version history by visualizing it as a graph.
        ```bash
        # git command and output here
        ```

    - b. Who was the last person to modify `README.md`? (Hint: use `git log` with an argument)
        ```bash
        # git command and output here
        ```
    
    - c. What was the commit message associated with the last modification to the `-Week 2` line of `index.md` file? (Hint: use `git blame` and `git show`, check out their help pages if you are not sure what to do)

 5. One common mistake when learning `git` is to commit large files that should not be managed by `git` or adding sensitive information like security keypairs for Amazon Cloud Services. Try adding a random text file to your assignment repository, making some modifications and commits to your repository, and deleting that file from history. (Simply deleting a file with `rm` in a repository will not remove version controlled history, you may want to look at [this](https://help.github.com/articles/removing-sensitive-data-from-a-repository/))

    > Perform the commits and deletion, this question will be graded based on your commit history on GitHub.

 6. In the course website repository (or another repository you want to clone from GitHub), modify one of its existing files:
     - a. What happens when you do `git stash`?
     > Answer here
     - b. What do you see when you run `git log --all --oneline` after stashing your modification?
     > Answer here
     - c. Run `git stash pop` to undo what you did with `stash`, in what scenario might this be useful?
     > Answer here

 7. Like many command line tools, `git` provides a configuration file (or dotfile) called `~/.gitconfig`. Create an alias in `~/.gitconfig` so that when you run `git graph`, you get the output of `git log --all --graph --decorate --oneline`. You can do this by directly modifying the `~/.gitconfig` file or by using the `git` command line functionality.
    ```bash
    # Your alias entry or git config command here
    ```
    This is also a good opportunity to turn your dotfiles folder into a version controlled repo, make it private if you have sensitive `ssh` configurations there (IP Addresses), else feel free to make it public. (This is for your own benefit, not part of the assignment grading)

 8. You can define global ignore patterns in `~/.gitignore_global` after running `git config --global core.excludesfile ~/.gitignore_global`. Do this, and set up your rglobal gitignore file to ignore OS-specific or editor-specific temporary files, like `.DS_Store`, or `.vscode`. Feel free to Google around for common gitignore entries for Python projects or other projects of your interest.
    ```bash
    # Your .gitignore_global entries here
    ```
 9. Push your completed assignment to GitHub, and submit the assignment by creating a pull request. 