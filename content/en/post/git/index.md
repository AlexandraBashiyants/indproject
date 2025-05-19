---
title: Version Control. Git
summary: 
date: 2023-10-25
authors:
  - admin
tags:
  - Git
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com)'
---

## Version control systems. General concepts

Version Control Systems (VCS) are used when several people work on the same project. Usually, the main project tree is stored in a local or remote repository, to which access is configured for project participants. When making changes to the project content, the version control system allows you to fix them, combine changes made by different project participants, and roll back to any earlier version of the project, if required.

Classical version control systems use a centralized model that assumes a single repository for storing files. Most version control functions are performed by a dedicated server. The project participant (user) receives the required version of files through certain commands before starting work. After making changes, the user places the new version in the repository. However, previous versions are not deleted from the central repository and you can return to them at any time. The server may not save the full version of the modified files, but rather perform so-called delta compression — save only changes between successive versions, which reduces the amount of data stored.

Version control systems support the ability to track and resolve conflicts that may arise when multiple people are working on a single file. You can merge (merge) the changes made by different participants (automatically or manually), manually select the desired version, cancel the changes altogether, or lock the files for modification. Depending on the settings, the lock prevents other users from obtaining a working copy or prevents the OS file system from changing the working copy of the file, thus providing privileged access to only one user working with the file.

Version control systems can also provide additional, more flexible functionality. For example, they can support working with multiple versions of a single file, maintaining a common revision history up to the point of branching versions and their own revision histories of each branch. In addition, information is usually available about which of the participants made changes, when and what. Usually, this kind of information is stored in the changelog, access to which can be restricted.

Unlike classical systems, a central repository is not mandatory in distributed version control systems.

Among the classic VCS, CVS and Subversion are the most well—known, while among the distributed ones are Git, Bazaar, and Mercurial. The principles of their work are similar, they differ mainly in the syntax of the commands used in their work.


## Examples of using git
The Git version control system is a set of command-line programs. They can be accessed from the terminal by entering the git command with various options.
Due to the fact that Git is a distributed version control system, a backup copy of the local storage can be made by simply copying or archiving.

### Basic git commands

Let's list the most frequently used git commands.

Creating the main repository tree:

- git init

Getting updates (changes) to the current tree from the central repository:

- git pull

Sending all changes made to the local tree to the central repository:

- git push

View the list of changed files in the current directory:

- git status

View current changes:

- git diff

Saving current changes:

add all modified and/or created files and/or directories:

- git add .

add specific modified and/or created files and/or directories:

- git add file_name

delete a file and/or directory from the repository index (while the file and/or directory remains in the local directory):

- git rm file_name

Saving added changes:

save all added changes and all modified files:

- git commit -am 'Description of the commit'

save the added changes with a comment via the built-in editor:

- git commit

creating a new branch based on the current one:

- git checkout -b_name

switching to a certain branch:

- git checkout branch name_

(when switching to a branch that is not yet in the local repository, it will be created and linked to the remote one)
sending changes to a specific branch to the central repository:

- git push origin_name

merging a branch with the current tree:

- git merge --no-ff branch name

Deleting a branch:

deleting a local branch that has already merged with the main tree:

- git branch -d branch_name

forced deletion of a local branch:

- git branch -D branch_name

deleting a branch from a central repository:

- git push origin :branch name

## Standard operating procedures with a central repository

The user's work with his branch begins with checking and receiving changes from the central repository (at the same time, no changes should have been made to the local tree before starting this procedure):

- git checkout master
- git pull
- git checkout -b_name

Then you can make changes in the local tree and/or branch.

After completing any changes to the project files and/or directories, they must be placed in the central repository. To do this, you need to check which files have changed to the current moment.:

- git status

If necessary, we delete unnecessary files that we do not want to send to the central repository.

Then it is useful to review the text of the changes for compliance with the rules for maintaining clean commits.:

- git diff

If any files should not be included in the commit, then we mark only those files whose changes need to be saved. To do this, we use the add and/or remove commands with the necessary options.:

- git add … 
- git rm …

If you need to save all the changes in the current directory, then use:

- git add .

Then we save the changes, explaining what was done.:

- git commit -am "Some commit message"

Sending the changes to the central repository:

- git push origin_name

or

- git push
