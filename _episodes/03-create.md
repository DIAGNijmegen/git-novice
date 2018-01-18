---
title: Creating a Repository
teaching: 10
exercises: 0
questions:
- "Where does Git store information?"
objectives:
- "Create a local Git repository."
keypoints:
- "`git init` initializes a repository."
---

Once Git is configured,
we can start using it.
Let's create a directory for our work and then move into that directory:

~~~
$ mkdir digits-classifier
$ cd digits-classifier
~~~
{: .bash}

Then we tell Git to make `digits-classifier` a [repository]({{ page.root }}/reference/#repository)—a place where
Git can store versions of our files:

~~~
$ git init
~~~
{: .bash}

If we use `ls` to show the directory's contents,
it appears that nothing has changed:

~~~
$ ls
~~~
{: .bash}

But if we add the `-a` flag to show everything,
we can see that Git has created a hidden directory within `digits-classifier` called `.git`:

~~~
$ ls -a
~~~
{: .bash}

~~~
.	..	.git
~~~
{: .output}

Git stores information about the project in this special sub-directory.
If we ever delete it,
we will lose the project's history.

We can check that everything is set up correctly
by asking Git to tell us the status of our project:

~~~
$ git status
~~~
{: .bash}

If you are using a different version of git than I am, then then the exact
wording of the output might be slightly different.

~~~
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)
~~~
{: .output}

> ## Places to Create Git Repositories
>
> Bob starts a new project to work on a Support Vector Machine, `svm`, 
> for his `digits-classifier` project.
> Despite Alice's concerns, he enters the following sequence of commands to
> create one Git repository inside another:
>
> ~~~
> $ cd                       # return to home directory
> $ mkdir digits-classifier  # make a new directory digits-classifier
> $ cd digits-classifier     # go into digits-classifier
> $ git init                 # make the digits-classifier directory a Git repository
> $ mkdir svm                # make a sub-directory digits-classifier/svm
> $ cd svm                   # go into digits-classifier/svm
> $ git init                 # make the svm sub-directory a Git repository
> ~~~
> {: .bash}
>
> Why is it a bad idea to do this? (Notice here that the `digits-classifier` project is now also tracking the entire `svm` repository.)
> How can Bob undo his last `git init`?
>
> > ## Solution
> >
> > Git repositories can interfere with each other if they are "nested" in the
> > directory of another: the outer repository will try to version-control
> > the inner repository. Therefore, it's best to create each new Git
> > repository in a separate directory. 
> >
> > To recover from this little mistake, Bob can just remove the `.git`
> > folder in the svm subdirectory. To do so he can run the following command from inside the `digits-classifier` directory:
> >
> > ~~~
> > $ rm -rf svm/.git
> > ~~~
> > {: .bash}
> >
> > But be careful! Running this command in the wrong directory, will remove
> > the entire git-history of a project you might wanted to keep. Therefore, always check your current directory using the
> > command `pwd`.
> >
> > To be sure that there is no conflicting
> > repository in the directory, check the output of `git status`. If it looks
> > like the following, you are good to go to create a new repository as shown
> > above:
> >
> > ~~~
> > $ git status
> > ~~~
> > {: .bash}
> > ~~~
> > fatal: Not a git repository (or any of the parent directories): .git
> > ~~~
> > {: .output}
> >
> > Note that we can track files in directories within a Git:
> >
> > ~~~
> > $ touch svm.py                  # create svm files
> > $ cd ..                         # return to digits-classifier directory
> > $ ls svm                        # list contents of the svm directory
> > $ git add svm/*                 # add all contents of digits-classifier/svm
> > $ git status                    # show svm files in staging area
> > $ git commit -m "add svm files" # commit digits-classifier/svm to digits-classifier Git repository
> > ~~~
> > {: .bash}
> >
> > Similarly, we can ignore (as discussed later) entire directories, such as the `svm` directory:
> >
> > ~~~
> > $ nano .gitignore # open the .gitignore file in the text editor to add the svm directory
> > $ cat .gitignore # if you run cat afterwards, it should look like this:
> > ~~~
> > {: .bash}
> >
> > ~~~
> > svm
> > ~~~
> > {: .output}
> >
> {: .solution}
{: .challenge}
