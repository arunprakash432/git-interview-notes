
---

# 🧠 What is `git rebase`?

`git rebase` is used to **move or reapply commits** from one branch onto another **base commit**.

It helps create a **clean, linear history** — as if your feature branch was built directly on top of the latest main branch.

---

# ⚙️ In Simple Terms:

* `git merge` → **Combines** histories (can create a merge commit)
* `git rebase` → **Rewrites** history (moves your commits to a new base)

---

# 🎯 Basic Example

You branched off `main` to make a feature:

```
(main)    A --- B
             \
(feature)     C --- D
```

Now, someone added a new commit (**E**) to `main` while you were working.

```
(main)    A --- B --- E
             \
(feature)     C --- D
```

You want your feature to be built *on top of the latest main* (including commit E).
That’s where **rebase** comes in.

---

# 🔁 After Rebase

Run:

```bash
git checkout feature
git rebase main
```

Git will:

1. Take commits `C` and `D` (your feature commits)
2. Replay them **on top of** `main`’s latest commit (`E`)

Result:

```
(main)    A --- B --- E --- C' --- D'
                      ↑
                  (feature rebased)
```

👉 Notice that:

* The commit history is now **linear**
* The new commits `C'` and `D'` are **copies** of `C` and `D`
* The old ones are replaced (history rewritten)

---

# 🔍 Visual Comparison

| Action     | Diagram                                                                                                       | Result                                                  |
| ---------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| **Merge**  | A --- B --- E  ← main  <br>  \                <br>   C --- D ← feature <br> → **Merge commit (F)** joins both | Keeps all history (non-linear)                          |
| **Rebase** | A --- B --- E --- C' --- D'                                                                                   | Creates linear history (as if feature was made after E) |

---

# 💡 When to Use `git rebase`

✅ To keep history clean (no extra merge commits)
✅ Before merging a feature branch into main
✅ To "catch up" with updated main branch before pushing

---

# ⚠️ Important Rule

> 🔥 **Never rebase a branch that has already been pushed and shared!**

Because rebase **changes commit history**, it can confuse collaborators who based their work on the old commits.

Use it safely for **local branches** you haven’t shared yet.

---

# 🧩 Common Commands

```bash
# Rebase current branch onto main
git rebase main

# Continue rebase after fixing conflicts
git rebase --continue

# Abort (undo) rebase
git rebase --abort

# Skip a problematic commit
git rebase --skip
```

---

# 🧭 Summary Table

| Command           | Purpose                        | Visual Outcome                              |
| ----------------- | ------------------------------ | ------------------------------------------- |
| `git merge`       | Combine branches               | Keeps both histories (may add merge commit) |
| `git rebase`      | Replay commits on a new base   | Linear, rewritten history                   |
| `git rebase main` | Put your branch on top of main | Updates your branch cleanly                 |

---

# 🪄 Mnemonic

> 🧩 **Merge = Mix histories**
> 🪶 **Rebase = Rewrite history**

---

