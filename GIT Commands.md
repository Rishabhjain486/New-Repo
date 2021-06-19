# USING GIT WITH VSCODE: COMMANDS TO BE USED

## Working with an existing repo on GITHUB:

1. Open the git folder on the local machine
2. Cloning a repo:
`git clone <SSH Link>`
3. See the files in the folder:
 * To see all the files with details: `ls -la`
 * To see jus the file names: `ls -a`
 * To see just the folders: `ls`
4. Change directory into the repo:
`cd hello-javascript`
5. make the changes and save the file using cmd+s
6. Check the status of the files created, updated or deleted:
`git status`
7. Make GIT track all the files:
`git add .`
 * Make GIT track a specific file instead:
`git add <name of new file created>`
8. Now check the status again and see that all files are green, ie, all files are tracked:
`git status`
9. Now we will commit the changes to our repo:
`git commit -m "message title" -m "description"`
 * The -m means message, and it should specify what and why the changes being commited were made
 * if there are only modified files and no new created files, we can use a shortcut: `git commit -am "message"` directly after step 6. This will add and commit the files via single command
10. These changes are now saved locally, but still not saved on the github
11. Now we push these changes on the remote repository:
`git push origin master`
 * Origin is the word that stands for our git repo
 * Master is the branch that we want to push to
12. After running the above command go to github and refresh the page to see the changes
13. To clear the terminal:
`clear`
14. Update the local repo:
`git pull origin master`
 * This will update the files on the local machine
 * We can clone a repo only once, thus this is used to update the repos
 * if we have defined an upstream using `-u` then we only need to use `git pull` command


## Making a new repo on the local machine and pushing it onto GITHUB

1. go into the newly created repo:
`cd ../new_repo`
2. See the files in the folder:
 * To see all the files with details: `ls -la`
 * To see jus the file names: `ls -a`
 * To see just the folders: `ls`
 * this will come as a blank till we add a file in the folder
3. To convert this folder into a git repo:
`git init`
4. Steps 2-10 above can now be used here as required
5. Running `git push origin master` will give an error
 * This is because we did not clone this repo from the GITHUB, we created it locally
 * Git doesnt know where to push it to since it is not connected to anything
 * We need to create this connection
6. Go to Github, and create a new repo, give it a name, save it and copy the SSH Link
7. Now run the command:
`git remote add origin <SSH Link>`
8. To verify the remote repository that we connected to this repo:
`git remote -v`
9. Now we can push:
`git push origin master`
 * If we use `git push -u origin master` we will define an upstream, ie, next time just typing `git push` will by default push it to origin master and we dont have to type it again and again
 * This will push the code on the master branch
 * to push on the other branch, replace master with the branch name: `git push origin branch-name`
10. Refresh the Github page and see the changes


## GIT Branching

1. To see the branches:
`git branch`
 * if there are no branches, it will just show master
 * in case of multiple branches, the branch with the `*` will show the branch we are in currently
 * If you are using terminal outside VSCode, you may need to press `Q` to gome back to terminal
2. To create a new branch:
`git checkout -b Branch-name`
3. Check branches:
`git branch`
4. Switch between branches:
`git checkout branch-name`
 * we can hit the `tab` button and it will autocomplete the branch name
 * we can type any part of the branch-name and it will autocomplete it
 * to switch to master branch: `git checkout master`
 * check which branch you are on: `git branch`
5. Now we can use the steps 6-9
6. To check the differences between the master and the new branch:
 * Save the changes and push
 * change the branch to the master branch
 * now type: `git diff branch-name`
7. To merge:
`git merge branch-name`
 * we can also merge from the github website
8. if we type `git branch` it still shows the branch even though we have merged it to the master branch
 * we do not require the branch that is merged and can delete it
 * switch to the master branch and delete the new branch using: `git branch -d branch-name`
 * we can verify from command `git branch`
9. handling **merge conflicts** :
 * Go to the created branch `git checkout branch-name`
 * use `git diff master` to see the differences
 * use `git merge master` to merge this branch into the master branch
 * if the master branch also was updated and has a code in the same line number as yours, it will show a merge conflict
 * best way is to view the file in VSCode and manually fix it
 * now using `git diff` will show that we are removing and adding the same lines, but we still need to commit since we modified the file
 * since we only modified, we can add and commit together `git commit -am "message"`


 ## Undoing in GIT

 1. How to undo changes if we accidentally made a wrong commit etc
 2. to undo a `git add` command:
 `git reset` or `git reset filename`
 3. To undo a commit:
 `git reset HEAD~1`
  * HEAD is the pointer to the last commit
  * HEAD~1 means to go one commit back, so the HEAD will now point to the earlier commit, effectively undoing our latest commit
4. not `git status` will again show the files as unstaged again
5. There is no method to undo multiple commits or earlier commits
6. We can see a log of the commits made (in reverse chronological order):
`git log`
 * it displays the commit messages, that is why it is good practice to add a relevant commit message
7. git differentiates these commits with a hash number
 * we can copy that hash number and do:
 `git reset hashNumber`
 * now git will unstage all the changes after that commit
 * the local files will still show the changes, but they will not be saved on the github
8. To completely remove the changes (and not just unstage) we use the command:
`git reset --hard hashNumber`



### Additional stuff 
1. Run the
following command and follow the instructions in your editor to edit
your configuration file:
` git config --global --edit` 

After doing this, you may fix the identity used for this commit with:
` git commit --amend --reset-author`
