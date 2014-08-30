<b><code>git-uncommit</code></b>: Undo git commits to patch files, and reapply them.

<b><i>git-uncommit</i></b> does exactly what it says: it uncommits the last Git commit, saving the patch.

<b><i>git-recommit</i></b> applies back the last uncommitted patch; after the patch is applied, the patch file is deleted.

## Example usage

Imagine you have just committed experimental changes to your branch, after much mork.

````sh
$ git commit -m "Experimental changes"
````

You are unsatisfied with the result, but do not want to discard the work, so you run <b><i>git-uncommit</i></b>


````sh
$ git uncommit
Uncommit: 2edf199-experimental-changes.patch
````

This undoes your experimental commit and creates <b><i>2edf199-experimental-changes.patch</i></b>.

You can undo in this way any number of commits; <b><i>git-recommit</i></b> can be used to apply the patches back.

To apply the last uncommitted patch:


````sh
$ git recommit
````

To run <b><i>git-recommit</i></b> with any saved patch file to reapply it in the order you want:

````sh
$ git recommit <patch-file>.patch
````

## Patch files

Patch files can be readily edited, shared with others and applied in a new order.

The patches are created using ```git format-patch```, and thus can also be applied using ```git am```.

Readable file names, extracted from your commit messages, are given to the patch files created.

## Comparison with related Git commands

```git stash``` can sometimes be used for similar purposes as <i>git-uncommit</i>, the differences are:
* <i>git stash</i> operates on changes to the work tree or index, not already committed changes
* <i>git stash</i> does not create a patch file, but saves the changes in the Git archive

```git reset HEAD^``` can also be used to revert the last commit, however the changes are not saved to a patch file, they are either discarded or left in the index or work tree, depending on the options

```STGit```: a tool that can also be used to reorder or edit commits, the main differences are:
* <i>STGit</i> has a much more complex set of command
* <i>STGit</i> does not save patch files automatically

## Installation

<i>git-uncommit</i> and <i>git-recommit</i> are stand-alone shell scripts, simply requiring Git to be installed.

In a Unix or Linux system, you can quickly install ```git-recommit``` and ```git-uncommit``` by copying the files to ```/usr/local/bin```.

Installing ```uni2ascii``` will help <i>git-uncommit</i> create better filenames for patches, when your commit messages have non-ascii characters.

## Author and licensing terms

````
Copyright (c) 2012, 2013, 2014 Michele Bini <michele.bini@gmail.com>

This program is free software: you can redistribute it and/or modify
it under the terms of the version 3 of the GNU General Public License
as published by the Free Software Foundation.

This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
````
