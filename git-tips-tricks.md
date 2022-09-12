## Git Tips and Tricks

> Create by: phungth

- [Reword the previous commit message](#reword-the-previous-commit-message)
- [Amend author](#amend-author)
- [Resets the index and working tree](#resets-the-index-and-working-tree)
- [Resets the head to \<commit>. No touch index and working tree](#resets-the-head-to-commit-no-touch-index-and-working-tree)
- [Saving current state of tracked files without committing](#saving-current-state-of-tracked-files-without-committing)
- [Show list of all saved stashes](#show-list-of-all-saved-stashes)
- [Delete all stored stashes](#delete-all-stored-stashes)
- [Apply any stash without deleting from the stashed list](#apply-any-stash-without-deleting-from-the-stashed-list)
- [Apply last stashed state and delete it from stashed list](#apply-last-stashed-state-and-delete-it-from-stashed-list)
- [Squash latest commits](#squash-latest-commits)
- [Reword commit (change commit message)](#reword-commit-change-commit-message)
- [After resolving the conflicts and undo rebase](#after-resolving-the-conflicts-and-undo-rebase)
- [Pick commits across branches using cherry-pick](#pick-commits-across-branches-using-cherry-pick)
- [Generate the patch](#generate-the-patch)
- [Apply the diff](#apply-the-diff)
- [Restore file to a specific commit-hash](#restore-file-to-a-specific-commit-hash)
- [Untrack files without deleting](#untrack-files-without-deleting)
- [Checkout recent working branch](#checkout-recent-working-branch)
- [Keep empty folder](#keep-empty-folder)
- [Use Aliases](#use-aliases)
- [Pretty git log](#pretty-git-log)

### Reword the previous commit message

```sh
git commit –amend​
```

### Amend author

```sh
git commit --amend --author='Author Name <email@address.com>'​
```

### Resets the index and working tree

*Any changes to tracked files in the working tree since <commit> are discarded​*

```sh
git reset --hard <commit>​​
```

### Resets the head to \<commit>. No touch index and working tree

```sh
git reset --soft <commit>​​
```

### Saving current state of tracked files without committing

```sh
git stash | git stash push -m <message>​​​
```

### Show list of all saved stashes

```sh
git stash list​​​
```

### Delete all stored stashes

```sh
git stash clear​​​
```

### Apply any stash without deleting from the stashed list

```sh
git stash apply <stash@{n}>
```

### Apply last stashed state and delete it from stashed list

```sh
git stash pop
```

### Squash latest commits

```sh
git rebase –i <commit>
<find the commits want to squash, change pick to squash>
<edit commit message>
```

### Reword commit (change commit message)

```sh
git rebase –i <commit>
<find the commits want to squash, change pick to reword>
<edit commit message>
```

### After resolving the conflicts and undo rebase

```sh
git rebase –continue
git rebase --abort
```

### Pick commits across branches using cherry-pick

```sh
git cherry-pick <commit>

git cherry-pick <commit1> <commit2>

git cherry-pick <commit1>…<commit5>
```

### Generate the patch

```sh
git diff > some-changes.patch
```

### Apply the diff

```sh
git apply /path/to/some-changes.patch
```

### Restore file to a specific commit-hash

```sh
git checkout <commit> -- <file_path>
```

### Untrack files without deleting

```sh
git rm --cached <file_path>
git rm –cached -r <dir_path>
```

### Checkout recent working branch

```sh
git checkout -
```

### Keep empty folder

```sh
cd path/to/empty/folder
touch .gitkeep
```

### Use Aliases

Add lines to ~/.gitconfig

```sh
[alias]
  st = status
  ci = commit
  co = checkout
  br = branch
```

or use commands

```sh
git config --global alias.<handle> <command> 
git config --global alias.st status
```

### Pretty git log

```sh
[alias]
  lg1 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
  lg2 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all
  lg = !"git lg1"
```
