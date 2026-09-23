# Git Stash - Command Evidence

Date: 23 Sep 2026
Branch: main
Repo: git-stash-project
File under test: `main.py`

## Scenario

A WIP (work-in-progress) feature change and an urgent hotfix change were made to `main.py` and stashed away so the working tree could be kept clean.

## 1. git stash (create a stash)

Command:
```
git stash push -m "WIP feature change"
git stash push -m "hotfix change"
```

Output:
```
Saved working directory and index state On main: WIP feature change
Saved working directory and index state On main: hotfix change
```

Result: both changes were saved and the working tree became clean.

## 2. git stash list (view saved stashes)

Command:
```
git stash list
```

Output:
```
stash@{0}: On main: hotfix change
stash@{1}: On main: WIP feature change
```

Explanation:
- `stash@{0}` is the most recent stash (hotfix change).
- `stash@{1}` is the older stash (WIP feature change).

## 3. git stash show (inspect a stash)

Command:
```
git stash show
git stash show -p stash@{1}
```

Output (without `-p` - summary only):
```
 main.py | 1 +
 1 file changed, 1 insertion(+)
```

Output (with `-p` - full diff of stash@{1}, the WIP feature change):
```
diff --git a/main.py b/main.py
index 5f5e035..cd9b5fd 100644
--- a/main.py
+++ b/main.py
@@ -5,3 +5,4 @@ def welcome():
     print("Urgent production fix applied")

 welcome()
+WIP: work in progress feature
```

## 4. git stash apply (apply a stash but keep it)

Command:
```
git stash apply stash@{1}
```

Output:
```
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   main.py

no changes added to commit (use "git add" and/or "git commit -a")
```

Result: the WIP change was applied to the working tree, and the stash was KEPT (still present in `git stash list`).

## 5. git stash pop (apply a stash and remove it)

Command:
```
git stash pop stash@{0}
```

Output:
```
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   main.py

no changes added to commit (use "git add" and/or "git commit -a")
Dropped stash@{0} (d8a0a2450d3c770a99b9ecd20a95f8c61b251fe8)
```

Result:
- The hotfix change was applied to the working tree.
- The stash entry `stash@{0}` was DROPPED (removed) automatically.
- `git stash list` after pop shows only the remaining stash:

```
stash@{0}: On main: WIP feature change
```

## 6. git stash drop (delete a stash without applying)

Command:
```
git stash drop stash@{0}
```

Output:
```
Dropped refs/stash@{0} (a344932c4127f30a79531b3620b640721321a6be)
```

Result: the WIP stash was deleted. Final check - `git stash list` is empty:

```
(no output)
```

## Summary Table

| Command                     | Purpose                                | Stash removed? | Change applied? |
|-----------------------------|----------------------------------------|----------------|-----------------|
| `git stash push -m "msg"`   | Save uncommitted changes               | No             | No              |
| `git stash list`            | Show all saved stashes                 | No             | No              |
| `git stash show [-p]`       | Inspect summary/diff of a stash        | No             | No              |
| `git stash apply <stash>`   | Apply a stash, keep it saved           | No             | Yes             |
| `git stash pop <stash>`     | Apply a stash, then remove it          | Yes            | Yes             |
| `git stash drop <stash>`    | Delete a stash without applying        | Yes            | No              |

## Final State

The working tree was restored to a clean state:

```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```