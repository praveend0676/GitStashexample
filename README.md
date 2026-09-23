# GitStashexample
# GitStashexample
# 📌 Problem Statement — Git Stash Workflow

Create a small Python project using Git and demonstrate how **Git Stash** can temporarily save unfinished work.

Start implementing a feature without committing it. When an urgent fix is required, use `git stash` to temporarily save the changes, switch to another branch, complete and commit the urgent fix, and then return to the original branch.

Demonstrate:

* `git stash`
* `git stash list`
* `git stash show`
* `git stash apply`
* `git stash pop`
* `git stash drop`

Finally, complete the feature, push the project to a public GitHub repository, and record a YouTube video explaining the complete stash workflow and the difference between **`stash apply`** and **`stash pop`**.

### 🎯 Real-World Scenario

> You are working on a new feature that is not ready to commit. Suddenly, an urgent production issue needs to be fixed. Instead of committing incomplete code, use **Git Stash** to temporarily save your work, switch branches, fix the urgent issue, and later


PS D:\Downloads\Super 30 exmples\GIT examples\git-stash-project> git log 
commit 107f487a1a477f117399a1a2a31d9d9c1cbdc5e9 (HEAD -> main, origin/main)
Merge: 3efe959 96a7d00
Author: praveend0676 <praveendevisetti0676@gmail.com>
:
commit 107f487a1a477f117399a1a2a31d9d9c1cbdc5e9 (HEAD -> main, origin/main)
Merge: 3efe959 96a7d00
Author: praveend0676 <praveendevisetti0676@gmail.com>
Date:   Wed Sep 23 20:36:16 2026 +0530

    merge conflicts

commit 3efe95956dfe7b8d3e719a39a908c89d08cb6d11
Author: praveend0676 <praveendevisetti0676@gmail.com>
Date:   Wed Sep 23 20:33:51 2026 +0530

    complete the feature

commit 96a7d00d596c6ebfcd1b4b5095e1ef060463e3ac (urgent_fix)
Author: praveend0676 <praveendevisetti0676@gmail.com>
Date:   Wed Sep 23 20:22:10 2026 +0530

    urgent fix is completed

commit 1271ebc632a613bc1e20a359d2503450b729f370
Author: praveend0676 <praveendevisetti0676@gmail.com>
Date:   Wed Sep 23 20:17:05 2026 +0530

    Stash example with procution fix scenario

commit f5aa7895910374ec512bfab966375e14076d8966
Author: praveend0676 <praveendevisetti0676@gmail.com>
Date:   Wed Sep 23 19:41:05 2026 +0530

    first commit

APPLY VS POP 
apply → restores the changes but keeps the stash.
pop → restores the changes and removes the stash if the operation succeeds.

    | Point                   | `git stash apply`             | `git stash pop`                |
| ----------------------- | ----------------------------- | ------------------------------ |
| Restores changes        | ✅ Yes                         | ✅ Yes                          |
| Removes stash           | ❌ No                          | ✅ Yes, if applied successfully |
| Can reuse same stash    | ✅ Yes                         | ❌ Normally no                  |
| Safer for demonstration | ✅ Yes                         | More destructive               |
| Command                 | `git stash apply "stash@{0}"` | `git stash pop "stash@{0}"`    |


git stash – Temporarily saves uncommitted changes and cleans the working directory.

git stash list – Displays all saved stashes.

git stash show – Shows a summary of changes in a stash.

git stash apply – Restores changes but keeps the stash.

git stash pop – Restores changes and removes the stash after successful application.

git stash drop – Permanently removes a specific stash.


Easy to remember:

👉 Apply = Restore + Keep

👉 Pop = Restore + Remove

👉 Drop = Delete Stash
