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

git stash:
    Lets say you made some changes and you want to park it somwhere. You want to Keep the changes somewhere so that you can later retrive it and currently do not want in your codebase.

    git stash - saves your current changes into stash and removes changes from your current working feature branch
    git stash list - shows all the changes that have been stashed
    git stash pop - pops/retrieve the latest changes that have been stashed in the stash list
    git stash clear - clears the stash
    git stash save <'add a meaningful comment'> - saves the changes on stash with the provided comment
    git stash pop 0 | git stash pop <index on the stash list> - retrives the change from stash list for the defined index
    By default stashing will save changes from modifed files/already git tracked files.So if you want to save tracked as well as untracked files use : git stash -u

    git diff <branch name> : gives differences between the current branch you are working on and branch name you suggested

    merge conflicts: When you are merging the code you basically would try to make your code in sync with main code and add the new feature. 
    1.When you are not in sync with main branch
    2.Someone has changed the same line and pushed in main, where I am also trying to make a change.So git doesnt know which change to keep. 
     