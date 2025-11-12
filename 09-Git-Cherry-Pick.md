
---

# 🍒 What is `git cherry-pick`?

**`git cherry-pick`** is used to **copy a specific commit** (or several commits) from one branch and **apply it to another branch**.

Think of it like:

> “Take *that* one good commit from another branch, and put it *here* — without merging everything else.”

---

# 🧠 Why Use It?

✅ You fixed a bug on one branch and want the same fix on another
✅ You added a useful commit on a feature branch and want it in main
✅ You want **specific** commits, not the whole branch history

---

# ⚙️ Basic Syntax

```bash
git cherry-pick <commit-hash>
```

You can get the `<commit-hash>` from:

```bash
git log
```

---

# 🧩 Example Scenario

You have two branches:

```
main:     A --- B
feature:  A --- B --- C --- D
```

Let’s say commit `C` is a **bug fix** that you want in `main`,
but you **don’t** want to merge the whole feature branch.

---

# 🍒 Using `git cherry-pick`

1️⃣ Switch to the branch you want to apply it to:

```bash
git checkout main
```

2️⃣ Cherry-pick the commit:

```bash
git cherry-pick C
```

---

# 🔄 Resulting History

```
Before:
main:     A --- B
feature:  A --- B --- C --- D
```

```
After:
main:     A --- B --- C'
feature:  A --- B --- C --- D
```

👉 Notice:

* The new commit on `main` is **C′** (a copy of C)
* C and C′ have the same changes but **different commit IDs**
* History remains **separate** — no merge commit

---

# 🧱 If You Cherry-Pick Multiple Commits

You can do:

```bash
git cherry-pick C D
```

Result:

```
main: A --- B --- C' --- D'
feature: A --- B --- C --- D
```

---

# ⚠️ Cherry-Pick Conflicts

If the file changes overlap, you’ll see a **merge conflict** just like in `git merge` or `git rebase`.

Git will tell you:

```
error: could not apply C
```

You fix conflicts manually, then continue:

```bash
git add .
git cherry-pick --continue
```

---

# 🔍 Visual Summary

| Action          | What It Does                            | Result                          |
| --------------- | --------------------------------------- | ------------------------------- |
| **Merge**       | Combine all commits from another branch | Adds all commits + merge commit |
| **Rebase**      | Replay all commits onto a new base      | Moves entire branch linearly    |
| **Cherry-pick** | Copy specific commits                   | Duplicates chosen commits only  |

---

# 🧭 Diagram Summary

### Before

```
main:     A --- B
feature:  A --- B --- C --- D
```

### After cherry-picking C

```
main:     A --- B --- C'
feature:  A --- B --- C --- D
```

*(C′ is a “cherry-picked” copy of C)*

---

# ✅ In Short

| Command           | Description                              | History Effect                    |
| ----------------- | ---------------------------------------- | --------------------------------- |
| `git merge`       | Bring in all commits from another branch | Combines histories                |
| `git rebase`      | Replay branch commits on a new base      | Linear, rewritten                 |
| `git cherry-pick` | Copy one or more specific commits        | Keeps history clean and selective |

---

# 💡 Real-World Example

Let’s say you accidentally fixed a bug on your feature branch but need that fix on main right now:

```bash
git log --oneline      # find commit hash (say abc123)
git checkout main
git cherry-pick abc123
git push origin main
```

Boom 💥 — that fix is now on main without merging the whole feature.

---

