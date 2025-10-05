###### (in this case) slides are better for practical attention 
## why version control?

collaboration
bug fixing / identification
adding or removing requirements
audit trial for managers or lawyers

version control systems allow us to keep a record of previous versions of files
have a canonical set of "latest" files that is easily updated
collaborate between multiple developers working on the same codebase, including automatically resolving or flagging conflicting changes made by different developers on the same code


• SCCS (1973)
• First widely used version control system for UNIX systems.
• Stores changes between file versions rather than entire new versions.
• RCS (1982)
• Individual files are tracked. One developer can “check out” a file so only they can
make changes to it until they “unlock it”.
• Practical problems: atomic changes across multiple files; locking a file then going on
holiday blocks everyone else!
• CVS (1986)
• Client-server model.
• Multiple developers can work on the same file concurrently. If a developer tries to
commit without having updated with the latest changes, cvs tries to automatically
merge the differences or asks the user to resolve the conflict.
• Can have different “branches” of a project that contain different file contents.
• Subversion (2000)
• Addresses problems with CVS that became more annoying over time but
basically the same (e.g., atomic commits to avoid corruption, retain history
when moving a file, allow symlinks & empty directories to be committed).
• Git (2005)
• The most popular distributed version control system (DVCS).
• Every “clone” is a full repository that others can treat as the “central” source if
they want to.
• Entire tree is versioned, not individual files.
• Lightweight branching encourages branch-based workflows.
• Git is the dominant VCS in current use.


###### Major VCS concepts

A repo is a collection of files and associated meta-data of a tree of files being version controlled

a revision is a particular version of a file or tree of files being version controlled

branches are sequences of revisions that have been given a name

###### Saving space

VCS usually store changes between revisions of files instead of the entire file for each revision

this is most often in the form of a "diff" between the two versions

some VCS's store a delta from version n to n + 1, other from n to n-1, giving slightly different performance characteristics

VCS's can generally only diff text files. storing binary files usually just results in storing a full copy of each new revision, taking lots of space

###### Collaborative editing

- developers work by "checking  out" a local copy of the repo from the central repo

###### conflicts and merges

if the developers changed different parts of the same file, then the system can combine the different parts of the same file, then the system can combine the different parts together resulting in a new file with both changed sections

	• If the developers changed the same parts of the same file, then the system
	can’t know which person’s changes to use. Throwing one of them away
	would lose data. So, it asks the developer who uploaded later to manually
	resolve the conflict by editing the file to combine both versions. The VCS
	will then take this new, hand-combined version as the latest version.


## Git distributed version control

##### remotes

remotes is the term git uses for the other locations online where the repo is available.

origin //  upstream

origin = originally cloned repo location

upstream = the authoritative home source of the code

if you have a fork of an existing project, manually adding an upstream remote for it allows you to keep track of that projects changes too


###### branches

-  a sequence of commits with a name, they're lightweight - quick to create with minimal storage overhead
- braces are local by default (in local repo), you can push a branch to a remote repo to make it available to others
- if you merge a branch into the main branch then you can (but don't have to) delete the branch. as long as commits are referenced from somewhere they will still be alive 

###### git workflows

there are lots of different workflows in use with git
there are ways of using git features to make working and collaborating on projects easier
lots of people have strong opinions about which workflow is best, so do some internet reading to from you own opinion
![[Pasted image 20250120153029.png]]

• When you start to do something (new feature, bug fix, etc.), always start a
new branch and switch to it, even if you think it will only be a few lines.
• git checkout –b fileopenfail_fix
• Develop in that branch, making 1 or more small commits to finish the task

• git add, git commit –m “Add new primitives to
support empty files.”
edit-compile-test cycle omitted <>
• git add, git commit –m “Use new file opening
primitives. Fixes bug #14”
• Switch back to the main branch.
• git checkout main
edit-compile-test omitted <>
Check main is up to date (others may have pushed changes while you worked)
• git pull
• If there were changes, go back to your topic branch and rebase the branch to the new,
latest version of main, and check it all still works.
• Git checkout fileopenfail_fix
• git rebase main
• If others have changed the files you were working on then you might have to manually resolve the
editing conflicts.
• Once it works with latest main, switch to main branch, merge the topic branch into it
• git merge fileopenfail_fix
• Git will give you a message about a fast-forward merge happening. This means it can
merge your changes just by adding them to the top of the main branch with no conflicts.
• Your local main branch now contains the new thing and you can share it.
• git push

###### frequent small changed to main are better for everyone

• Creating a long-lived branch per developer is a common student project
gotcha.
• Although it can work, it tends to discourage frequently merging small
changes back into main.
• This results in everyone’s branch diverging more and more from each other.
• if you are not confident about understanding pushing and merging it lets
you avoid them for a while but it stores up bigger problems for later!
• When everyone tries to merge back to main, lots of manual re-writing
needs to happen to match everyone’s individual changes.


#### git practical cookbook

git status 
git diff 
git init 

collaborating 

• Get the latest changes from the origin remote to your current branch.
• git pull
• This will actually do two things internally:
• git fetch – it will pull the latest changes from the origin remote
• git merge – it will merge those new changes with your local repo
• Uploading your latest changes for others
• git push
• Will push the current branch to the origin remote.
• The first time you may need to be explicit for Git to set the defaults.
• git push origin main