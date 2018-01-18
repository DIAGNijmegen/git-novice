---
title: Tags 
teaching: 5
exercises: 0
questions:
- "How do I label my work?"
objectives:
- "Understand tags."
keypoints:
- "Use tags to label the code at different time points."
---

If you're developing an experiment or a paper in git 
you may want to label the repo at relevant timepoints.
This makes going back and finding exactly what code you ran much easier.

To create a tag at the current revision:

~~~
$ git tag experiment-20180118
$ git push --tags
~~~
{: .bash}

The above will first tag your local repo with `experiment-20180118`,
and then push all of the tags to github.

> ## Delete a tag
>
> Use `git tag --help` to work out how to delete a tag, and do it.
{: .challenge}

> ## Make a tag for an earlier timepoint
>
> How would you create a tag for an earlier timepoint? Try it.
{: .challenge}
