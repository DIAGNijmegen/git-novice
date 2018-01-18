---
title: Branching 
teaching: 15
exercises: 0
questions:
- "How can I work without affecting other people?"
objectives:
- "Understand branches and pull requests."
keypoints:
- "Create and work on your own branch while developing so that you don't break other peoples stuff."
- "When your new feature works, make a pull request to the master branch."
---

If several people are working on the same repository then 
conflicts are bound to occur. This is a particular problem on the repos
that contain _common_ code.
These are best avoided if people develop on their own `branch`.

So far, every new commit has be stacked on the last commit,
and this set of commits forms the history of the repo on the `master` branch.
When you create a new `branch`, you create a fork in the history,
such that any new commits are created on this new track, and do not 
interfere with anything happening on `master`. 

In DIAG, we have a policy that branches should be called
`<your-username>/<your-feature-name>`. 
So, if I wanted to create a branch where I implement the svm classifier
I would type:

~~~
$ git branch jmsmkn/svm-classifier
$ git checkout jmsmkn/svm-classifier
~~~
{: .bash}

The first command creates the branch, and the second sets your working
copy to that branch. Commiting works in the same way, only now
the commits are only updating the branch that your working copy is on.
You can always check which branch you're working on with `git status`.

Now, lets immplement the svm on the branch. Edit the contents of 
`svm/classifier.py`, commit the changes, and push to github:

~~~
from sklearn import datasets
from sklearn import svm
from sklearn.metrics import accuracy_score

if __name__ == '__main__':
    # Number of test cases
    tc = 100

    # Load some digits (10 classes)
    # http://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_digits.html#sklearn.datasets.load_digits
    digits = datasets.load_digits()

    # Create the train and test sets
    x_train, y_train = digits.data[:-tc], digits.target[:-tc]
    x_test, y_test = digits.data[-tc:], digits.target[-tc:]

    # Create the Support Vector Machine class
    # http://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html
    #   C is the penalty parameter
    #   gamma is the kernel coefficient
    clf = svm.SVC(C=1.0, gamma=0.01)

    # Fit the model given the training data
    clf.fit(x_train, y_train)

    # Predict the classes
    y_pred = clf.predict(x_test)

    # Get the accuracy
    print(accuracy_score(y_pred, y_test))
~~~
{: .python}

> ## Implement the SVM classifier
>
> Add the svm classifier code to `svm/classifier.py` and push the changes to
> github. Then, create a pull request to merge the branch to master.
{: .challenge}
