git-prev-next allows you to easily navigate your commits, and amend them. It is built on top of interactive rebase.

Have you ever begun an interactive rebase to edit a commit, and then find that you also want to edit the parent commit? Or just wanted to edit a few commits back without going through the interactive rebase rigamarole?

## Example

    > # Oops, I need to make a change three commits up
    > git prev 3
    ...hack hack hack...
    > git commit --amend
    > # oh I need to fix the next commit too
    > git next
    ...hack hack hack...
    > git commit --amend
    > # all done
    > git rebase --continue
    

## `git prev`

This takes the current HEAD commit and prepends it to the rebase todo list (as 'pick'). It then resets to the parent commit.

If there is not a current interactive rebase, `git prev` will begin one.

You can pass a number like `git prev 3` to go up 3 commits.

## `git next`

This takes the next entry in the todo list, switches it to 'edit', and then invokes `git rebase --continue`. Note this terminates the interactive rebase if it reaches the top.

You can also pass a number to `git next`.

## Installation

Install through copying or symlinking into your `$PATH`. For example:

    ln -s $PWD/git-prev ~/.bin
    ln -s $PWD/git-next ~/.bin

## Safety

`git prev` and `git next` will refuse to enter or exit merge commits. They also will error if your worktree is not clean.
