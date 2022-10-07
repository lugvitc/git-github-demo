ma# Git Commands/How to
## Making an offline version of a remote repository
```bash
git clone <url> # copy the repo
```

## Pushing Edits to the repo
- Pull from the remote repo in case there are any changes
- Edit your files however you want
- Stage the edits to be edited
- Commit the edits (with a suitable commit message)
- Push the commits to the remote repo
```bash
git pull <remote-name> <branch-name> # get any changes from the remote repository
# edit files
git add <file-name> # stage specific files
git add --all # stage all edited files
git commit -m 'message' # commit the staged edits with a message
git push <remote-name> <branch-name> # sends the changes to the remote repo eg: git push origin main
```

## Branches
```bash
git checkout <branch-name> # switch to an existing branch
git checkout -b <branch-name> # Create a new branch
git branch # see local branches
git branch -a # see all branches
git branch -d <local-branch-name> # delete a local branch
git push <remote-name> --delete <remote-branch-name>

git fetch <remote-name> # bring all branches from remote to local
```

## Forking
> [Reference](https://www.dataschool.io/how-to-contribute-on-github/)
- Fork a repo in github.
- Clone it to your local machine
- Set the original repo as the 'upstream' one and your fork as the 'origin'
- To edit:
	- Pull from upstream
	- Edit
	- Push to origin
	- Create a pull request on github
	- The creator of the original repo can now merge them
```bash
# fork a repo in github
git remote add origin <url-of-fork> # add your forked repo as the origin branch
git remote add upstream <url-of-repo> # add the original repo as the upstream branch
git remote -v # checking the names for the urls
git pull upstream <branch-name>
git push origin <branch-name>
# then make a pull request in github
```
WORKFLOW:
> Pull from the original, edit, push to yours and create a pull request
> Any further commits to your branch will be automatically added to the pull request
> ???
> profit

## Resolving Merge Conflicts
- Pull the repo
- Merge branches
- `git diff` can be used to see differences (i haven't used it though)
- See conflicts
- Types:
	- Deleted by us or deleted by them: a file has been deleted in one of the branches
	- both modified: both branches have conflicting changes which need to be resolved
```bash
git pull origin # pull the repo
git checkout <branch-name> # move to the branch into which you wanna merge
git merge <other-branch-name> # merge the branch you want to merge
# if you see a merge-conflict (you might notice branch-name|MERGING where the branch's name usually is)
git status # to see merge conflict
# for deleted by us/them files:
git rm <file-name> # to remove the file
git add <file-name> # to keep the file
# for both modified branches:
# edit the files in vim or whatever
# when edited:
git add <file-name> # add the file you just edited
git status # just check if there are no other remaining conflicts
git commit -m 'message' # commit it all and the merge is complete
```
REMEBER:
> - Stage every file after it has no conflicts and then commit at the end
> - All else will be taken care of

### Editing the files
> Add more about `>>>>>>>`, `<<<<<<<` and `=========` and other stuff

## Miscellaneous
### Config
```bash
git config --global --list
```

### Credential Helper for Windows
- Types of credential managers:
	- Store: keeps the credentials in an unencrypted file
	- Git credential manager-core: the one I use, needs authorization once
- If you don't have saved credentials, every push will require the username and password(personal access token in reality)
```bash
git config --global --unset credential.helper # to remove any credential manager
git config --global credential.helper <type>
```