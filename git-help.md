git status 
git add .
git commit -m 'meesage' - commit to local repository
git push origin main - pushes to main repository

git init - to tell git to manage your local folder as git repo
git add remote origin -repo url

git branch -which branch you are working on
git branch -m renaming the branch
git branch feature-rutuja - to create a new branch , copies the entire code base from your current working branch to newly created branch , it depends on which branch your creating a new branch
git checkout feature-rutuja - to change branch from main to feature
git checkout -b feature-rutuja2 = to create new branch and switch to the new branch
git checkout -b feature-ved feature-rutuja - to create new branch for ved based on rutujas brach and then seitch to veds branch
git branch -d feature-rutuja - to delete feature-rutuja branch

git remote -v - to see where origin is pointing

pull request - to merge the changes you made in your branch to other branch

****When to Use git pull - git pull origin release
✅ When collaborating with a team and you want the latest updates before making new changes.
✅ Before pushing your work to ensure you are working with the latest code.
✅ When switching branches to ensure you have the most up-to-date code.

For removing changes:
scenario1: I have made changes, but havent staged yet 
    use command: git restore file_name
    and changes will be removed

scenario2: I have made changes, and I have staged them
    use command: git restore --staged <file> to unstage the changes and
                 git restore file_name to completely remove the changes

scenario3: I have made changes, and I have commited them
    use command: 
    git log :to check commit log history, the most recent commit will be at the top. Choose whiccommit       you want to go back to and copy hash value.
    git reset #commit value :the changes will go back to staged
    git reset --hard #commit value : the changes will be completely gone, from staging as well


git remote -v 
    - to see where origin is pointing
    - to see where upstream is pointing

Git fork and working with project hosted in different git account:
   1. Serch the project in github search and once you find the repository , fork the repository.
   2. Forking the repository will create a copy of that project in your github.
   3. Fork repository url is called upstream
   4. git clone your repository on your local.
   5. Create a feature branch and make your changes.
   6. stage and commit them into local
   7. push the changes to remote feature branch. 
   8. create pull request- and by default the PR is created from origin/feature -> upstream/main
   9. The owner of upstream repository will review PR and merge ito main
   10. To sync upstream main to your main , set upstream in your local :  
        git remote add upstream <forked repo url> 
        and the use git pull upstream main - to copy upstream main intou ur local main
   11. Then push your local main (newly synched with upstream) to github main - git push origin main

  git stash:
    Lets say you made some changes and you want to park it somwhere. You want to Keep the changes somewhere so that you can later retrive it and currently do not want in your codebase.

    git stash - saves your current changes into stash and removes changes from your current working feature branch
    git stash list - shows all the changes that have been stashed
    git stash pop - pops/retrieve the latest changes that have been stashed in the stash list
    git stash clear - clears the stash
    git stash save <'add a meaningful comment'> - saves the changes on stash with the provided comment
    git stash pop 0 | git stash pop <index on the stash list> - retrives the change from stash list for the defined index

    git stash -u :By default stashing will save changes from modifed files/already git tracked files.
                  So if you want to save tracked as well as untracked files use : git stash -u

    git diff <branch name> : gives differences between the current branch you are working on and branch name you suggested

    merge conflicts: When you are merging the code you basically would try to make your code in sync with main code and add the new feature. 
    1.When you are not in sync with main branch
    2.Someone has changed the same line and pushed in main, where I am also trying to make a change.So git doesnt know which change to keep. 

Best practices:
    1. Before starting any work, always sync your local repository with the latest remote changes. Regularly pull changes from main to avoid large merge conflicts later.
        git checkout main
        git pull origin main  # Fetch and merge latest changes from remote
    2. Never work directly on main. Always create a feature branch for your work.
        git checkout -b feature-branch main
        Keeps main stable and makes it easier to track changes per feature.
    3. Make small, atomic commits instead of large ones. Use meaningful commit messages.
        git commit -m "Fix issue #123: Improve query performance in reports"
            Best Practice: Follow a structured commit format:
            feat: New feature
            fix: Bug fix
            refactor: Code improvements
            docs: Documentation changes
    4.Instead of directly pulling, use git fetch to review changes before merging.
        git fetch origin main
        git diff main origin/main  # See the differences
        git merge origin/main      # Merge when ready
    5.use git rebase instead git pull - Rebasing keeps the commit history clean by applying changes on top of the latest main.
        git checkout feature-branch
        git pull --rebase origin main
    6.If you need to switch branches but have uncommitted changes, stash them.
        git stash save "WIP: refactoring API"
        git checkout main
        git pull origin main
        git checkout feature-branch
        git stash pop
    7.Push to Remote Frequently
        To avoid conflicts with teammates, push your changes regularly. 
        git push origin feature-branch
        💡 Best Practice: Use git push --force-with-lease (instead of git push --force) when rebasing, to prevent overwriting teammates' changes.
        git push --force-with-lease
    
    8.Keep Your PRs Small & Focused
        Before merging, raise a Pull Request (PR) with a small, focused change.
        git push origin feature-branch
    💡 Best Practice:
        Keep PRs under 500 lines of code for easier review.
        Write a clear PR description explaining the changes.
        
    9.Uncommit / remove the changes
        git reset --soft HEAD~1  # Keep changes
        git reset --hard HEAD~1  # Discard changes


