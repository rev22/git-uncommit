git-uncommit: uncommit and recommit commands for Git, save your commits to patch files

Git uncommit does exactly what it says: it uncommits the last Git commit, saving the patch.

Git recommit applies back the last uncommitted patch; after the patch is applied, the patch file is deleted.

Usage:

Let's suppose after much work you have just committed experimental changes to your branch.

````shell
$ git-commit -m "Experimental changes"
````

You are unsatisfied with the result, but do not want to discard the work, so you run ```git-uncommit```


````shell
$ git-uncommit
Uncommit: 2edf199-experimental-changes.patch
````
The patch created by ```git-uncommit``` using ```git format-patch``` and is saved to a file: 2edf199-experimental-changes.patch

Comparison with related git commands:

```git stash``` can sometimes be used for similar purposes as ```git-uncommit```, the differences are:
* git stash operates on changes to the work tree or index, not already committed changes
* git stash does not create a patch file, but saves the changes in the git archive

```git reset HEAD^``` can also be used to revert the last commit, however the changes are not saved to a patch file, they are either discarded or left in the index or work tree, depending on the options you give to '''git reset'''

```stg``` or ```STGit```: a tool that can also be used to reorder or edit commits, the main differences are:
* ```STGit``` has a much more complex set of command
* it does not save patch files automatically
