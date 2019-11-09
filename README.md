Have you ever begun an interactive rebase to edit a commit, and then find that you also want to edit the parent commit? Or just wanted to edit a few commits back without going through the interactive rebase rigamarole?

git-prev-next is a pair of custom git commands to make it easier to navigate and rebase in a git commit history. It is built on top of interactive rebase.

# `git prev`

This takes the current HEAD commit and prepends it to the rebase todo list (as 'pick'). It then resets to the parent commit.

`git prev` will begin an interactive rebase if necesssary. It also refuse merge commits.

You can pass a number like `git prev 3` to go up 3 commits.

# `git next`

This takes the next entry in the todo list, switches it to an `edit`, and then invokes `git rebase --continue`. Note this terminates the interactive rebase if it reaches the top.

You can also pass a number to `git next`.

# Installation

Install through copying or symlinking into your `$PATH`. For example:

    ln -s $PWD/git-prev ~/.bin
    ln -s $PWD/git-next ~/.bin

## Safety

`git prev` and `git next` will refuse to enter or exit merge commits, or if your worktree is not clean.
