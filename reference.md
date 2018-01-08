# GitHub Workflow Reference


## Prerequisites

- You have a GitHub account and you know your username and password. If you
  don't have one, create one now.
- You have Git installed and configured.
- You know how to open a terminal and generally work from the command-line.
- You know enough of vi or vim to edit, move around in, save, and quit files.


## Workflow Overview

The workflow description below covers the typical operations in the order
they are often performed to develop and contribute work to an existing project.
Most of the operations are issued from the command line. These lines start with`$`.
Do not type `$`. This is the prompt that the command line displays to you to
indicate that it is ready for you to type a command. Lines that start with `###`
are performed using GitHub through a browser. The numbers at the end of each
line are for quick reference and should not be typed either. When you see a term in all capital letters surrounded by angle
brackets, e.g., `<MY_URL>`, replace it with a value appropriate to the project
you are working on. A list of these placeholders and their meaning is below:

- `<MY_URL>` - The URL to your GitHub hosted repository. To find it, navigate to
  your repository on GitHub. Click on the green "Clone" button. You get a pop-up that contains a URL in a text-box. Unless you have configured your GitHub account to authenticate with SSH, you'll want a URL that starts with https://. If the URL starts with git@github... click `Use HTTPS`.
- `<THEIR_URL>` - (advanced) The URL for the project's repository that you would like to
  contribute to, that you do not own or maintain. Find it by navigating to their repository on GitHub and copy
  the URL in the box right of the `SSH` or `HTTPS` button. Use `HTTPS` since
  this is not your repository.
- `<DIR>` - This is any directory name you like. But use the same directory for
  each occurrence of `<DIR>`.
- `<BRANCH_NAME>` - This is a branch name of your choosing. Choose one that is
  related to the bug your are fixing or the feature you are implementing.
  Whatever you choose, use the same branch name throughout the example.

Also note, lines marked with `*` represent modifications being made to files in
the project. The exact modifications you might make, and the tools that you use
to make them, depend on what you are trying to do and your preferences. In
short, these lines should not be typed in literally, but must be interpreted in
terms of the task you are performing.

## Quick vi/vim commands

i       Insert into a file
ESC     Exits insert mode
:w      Save changes to file
:q      Quit vi/vim
:wq     Save changes and quit


## Setup: (1-3)

When you first start working on a project, you'll need to clone your repository locally (2-3), and create a remote back to the project in your local repository (4). Once you've done this setup for a project, you will
not need to do it again unless you delete your local clone or the remote.

```bash
$ git clone <MY_URL> <DIR>                              (1)
$ cd <DIR>                                              (2)
$ git remote add upstream <MY_URL>                      (3)
```


## Starting your contribution: (5-13)

When you start working on a contribution, you need to create a branch to hold
your work (5), do a little work and commit it (6-8), push your new branch to
your repository on GitHub (9), and create a pull-request from your new branch
to master in the project's repository on GitHub (10-11).

The purpose of the pull-request isn't to get the maintainer to accept your work
(yet). It starts a conversation with the maintainer. They can review what you
are trying to do and give you feedback early. That way, if you are on the wrong
track or the maintainer is not interested in your idea, you can find out before
you waste too much time implementing your idea.

Also, remember, line (6) is marked with `*`, so must be interpreted for the
task you are performing.

```bash
$ git checkout -b <BRANCH_NAME>                        (4)
$ vim file1                                           (*5)
$ git add .                                            (6)
$ git commit -v                                        (7)
$ git push -u origin <BRANCH_NAME>                     (8)
```


## Work (9-12)

Keep working on your idea, committing and publishing your work as you go
(12-15). The pull-request will automatically be updated with the new commits you
push to your repository on GitHub, allowing the maintainer to follow your
progress as you go.

Also, remember, lines (12) is marked with `*`, so must be interpreted for the
task you are performing.

```bash
$ vim file4                                           (*9)
$ git add .                                            (10)
$ git commit -v                                        (11)
$ git push origin <BRANCH_NAME>                        (12)
```


## Keep your repositories up-to-date (13-19)

While you are working on your idea, the maintainer may have accepted work from
other contributors. As that happens, the project's master branch will contain
commits that yours do not. You'll need to pull and fetch these commits into your local
master (13-14), rebase your work on top of those commits (15), and push your
branches to your repository on GitHub (19). When you rebase your work (15) you
might find that your changes are incompatible with those you fetched from
upstream. You will need to resolve any conflicts that git identifies (16-18).
GitHub has a lovely tutorial on resolving conflicts [1].

It's a good idea to update your repositories regularly so that your work does
not become too stale.

Again, as you push your work to your repository on GitHub, the pull-request
is updated automatically.

Also, remember, line (16) is marked with `*`, so must be interpreted for the
task you are performing.


```bash
$ git pull <MY-URL>                                    (13)
$ git fetch upstream master:master                     (14) *** is this necessary?
$ git rebase master                                    (15)
$ vim file1                                           (*16)
$ git add .                                            (17)
$ git rebase --continue                                (18)
$ git push -f origin master <BRANCH_NAME>              (19)
```


**If you are on master, (14) will fail. Now what?**

If you are on master branch, (14) will fail. Instead replace that line with `git pull upstream master`. This will fetch and merge the changes from upstream's master branch into your current local branch (master in this case). After that, (15-18) are unnecessary. However, don't forget to update master in your origin repository by running (19).


**Updating other branches**

After you have updated your master branch (14), if you have other branches, you may need to update them as well. To do that, checkout each branch one at a time (e.g., `git checkout <OTHER_BRANCH_NAME>`) and perform (15-18) for each.


## Squash your commits (20-21)

If you are following best practices, you will make many small commits as you
develop your idea. Sometimes earlier commits are invalidated/corrected by later
commits as you refine your solution. Your commit log becomes a diary of how you
developed your solution. This log is sometimes useful to you as you develop your
idea, but usually maintainers will ask you to squash your commits (20) into just
a few (often one) logical commit that implements your feature, or fixes the bug.
That helps keep the log of the main project cleaner, and more clearly identifies
which commits are responsible for implementing which features or fixing which
bugs. Usually you squash when you near completion of your implementation, but a
maintainer may ask you to squash periodically as you go because it may make it
easier for them to review your changes.

In any case, you will periodically squash your commits (20) and push the
squashed version to your repository on GitHub (21). 

To squash commits, we perform an interactive rebase (20). This will put us into
and editor (vim most likely) with a list of the commits that we are rebasing at
the top. To squash them into one commit, change the first word in every line
after the first from `pick` to `squash`. Save and quit. Git will combine all the
commits into the first and will again put you into an editor to create the final
commit message for the newly squashed commit. If you have been providing good
commit messages as you go along, writing a good final commit message should be
relatively easy.

GitHub has a nice article on interactive rebases [2].

```bash
$ git rebase -i master                                 (20)
$ git push -f origin <BRANCH_NAME>                     (21)
```


## Maintainer accepts your pull-request (22)

After all your hard work, hopefully the maintainer will eventually accept your
pull-request, which will merge your changes into their master branch.

```bash
### Maintainer accepts your pull-request               (22)
```


## Update your master (23-24)

After the maintainer has accepted your pull-request, your need to update your
master with the new changes in upstream, which are yours (25-26)! You follow the
same procedure as in "Keeping your repositories up-to-date", except that you
don't need to rebase. That's because your work is already included in master.

```bash
$ git fetch upstream master:master                     (23)
$ git push origin master                               (24)
```


## Delete unneeded branches (25-27)

Now that your work has been accepted in upstream, you can safely delete the
branches you were working on both in your local and remote repositories (27-29). If you ever abandon your effort before
a pull-request is accepted, you can also delete your branch; but you'll need
to use -D (capital D) in (28).

```bash
$ git checkout master                                  (25)
$ git branch -d <BRANCH_NAME>                          (26)
$ git push origin :<BRANCH_NAME>                       (27)
```


## Update your repositories before starting the next fix/feature

OK, it's been a month since you worked on the project. Now you're back from the Bahamas and are ready to start working again. However, while you were sunning yourself, others have been hard at work contributing changes to upstream. So before you start working again, you need to update your repositories with changes from upstream. Follow steps in section _Keep your repositories up-to-date (13-19)_ to get this done.

Nice tan. Now get back to work!


## References

[1] GitHub. _Resolving a Merge Conflict from the Command Line_. Accessed April
2016.
<https://help.github.com/articles/resolving-a-merge-conflict-from-the-command-line/>.

[2] GitHub. _About Git Rebase_. Accessed April 2016. <https://help.github.com/articles/about-git-rebase/>.


## Copyright and Licensing

This lab was modified by Amy Csizmar Dalal from a lab by Darci Burdge and Stoney Jackson.

Copyright 2016 Darci Burdge and Stoney Jackson SOME RIGHTS RESERVED

This work is licensed under the Creative Commons Attribution-ShareAlike 4.0
International License. To view a copy of this license, visit
http://creativecommons.org/licenses/by-sa/4.0/ .
