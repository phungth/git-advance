# Git Commit Best Practices

## Basic Rules

### Commit Related Changes

A commit should be a wrapper for related changes. For example, fixing two different bugs should produce two separate commits. Small commits make it easier for other developers to understand the changes and roll them back if something went wrong.
With tools like the staging area and the ability to stage only parts of a file, Git makes it easy to create very granular commits.
 
### Commit Often

Committing often keeps your commits small and, again, helps you commit only related changes. Moreover, it allows you to share your code more frequently with others. That way it‘s easier for everyone to integrate changes regularly and avoid having merge conflicts. Having large commits and sharing them infrequently, in contrast, makes it hard to solve conflicts.

### Don't Commit Half-Done Work

You should only commit code when a logical component is completed.
Split a feature‘s implementation into logical chunks that can be completed quickly so that you can commit often. If you‘re tempted to commit just because you need a clean working copy (to check out a branch, pull in changes, etc.) consider using Git‘s «Stash» feature instead.

### Test Your Code Before You Commit

Resist the temptation to commit something that you «think» is completed. Test it thoroughly to make sure it really is completed and has no side effects (as far as one can tell). While committing half-baked things in your local repository only requires you to forgive yourself, having your code tested is even more important when it comes to pushing/sharing your code with others.

### Write Good Commit Messages

Begin your message with a short summary of your changes (up to 50 characters as a guideline). Separate it from
the following body by including a blank line. The body of your message should provide detailed answers to the following questions:
– What was the motivation for the change? – How does it differ from the previous
implementation?
Use the imperative, present tense («change», not «changed» or «changes») to be consistent with generated messages from commands like git merge.
Having your files backed up on a remote server is a nice side effect of having a version control system. But you should not use your VCS like it was a backup system. When doing version control, you should pay attention to committing semantically (see «related changes») - you shouldn‘t just cram in files.

### Use Branches

Branching is one of Git‘s most powerful features - and this is not by accident: quick and easy branching was a central requirement from day one. Branches are the perfect tool to help you avoid mixing up different lines of development. You should use branches extensively in your development workflows: for new features, bug fixes, ideas...

### Agree on A Workflow

Git lets you pick from a lot of different workflows: long-running branches, topic branches, merge or rebase, git-flow... Which one you choose depends on a couple of factors: your project, your overall development and deployment workflows and (maybe most importantly) on your and your teammates‘ personal preferences. However you choose to work, just make sure to agree on a common workflow that everyone follows.

The following document is based on experience doing code development, bug troubleshooting and code review across a number of projects using GIT, including libvirt, QEMU and OpenStack Nova. Examination of other open source projects such as the Kernel, CoreUtils, GNULIB and more suggested they all follow a fairly common practice. It is motivated by a desire to improve the quality of the Nova GIT history. Quality is a hard term to define in computing; one man's "Thing of Beauty" is another man's "Evil Hack". We can, however, come up with some general guidelines for what to do, or conversely what not to do, when publishing GIT commits for merge with a project, in this case, OpenStack.

This topic can be split into two areas of concern

* The structured set/split of the code changes
* The information provided in the commit message
