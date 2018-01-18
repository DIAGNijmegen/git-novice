---
layout: lesson
root: .
---

Version control is the lab notebook of the digital world: it's what
professionals use to keep track of what they've done and to
collaborate with other people.  Every large software development
project relies on it, and most programmers use it for their small jobs
as well.  And it isn't just for software: books,
papers, small data sets, and anything that changes over time or needs
to be shared can and should be stored in a version control system.

The advantages of version control over, say, emailing files back 
and forth, are:

*   Nothing that is committed to version control is ever lost, unless
    you work really, really hard at it. Since all old versions of
    files are saved, it's always possible to go back in time to see
    exactly who wrote what on a particular day, or what version of a
    program was used to generate a particular set of results.

*   As we have this record of who made what changes when, we know who to ask
    if we have questions later on, and, if needed, revert to a previous
    version, much like the "undo" feature in an editor.

*   When several people collaborate in the same project, it's possible to
    accidentally overlook or overwrite someone's changes. The version control
    system automatically notifies users whenever there's a conflict between one
    person's work and another's.

Teams are not the only ones to benefit from version control: lone
researchers can benefit immensely.  Keeping a record of what was
changed, when, and why is extremely useful for all researchers if they
ever need to come back to the project later on (e.g., a year later,
when memory has faded).

> ## Prerequisites
>
> In this lesson we use Git from the Unix Shell.
> Some previous experience with the shell is expected,
> *but isn't mandatory*.
{: .prereq}

## Git is not Github

It's important to note that git and github are not the same thing. Git is
the version control system, that stores history is a repository. Github
is a website that hosts git repositories. 

In this workshop we will use git on your local machine first to create a 
toy experiment, where Alice and Bob will collaborate on creating a Support
Vector Machine to classify digits (like MNIST). We'll
 then learn how we can store this repo on github.
