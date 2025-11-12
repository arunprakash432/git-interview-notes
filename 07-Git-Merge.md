
---

# 🧠 What is `git merge`?

**`git merge`** combines changes from one branch into another.
Usually, you **merge a feature branch** into your **main branch** after finishing some work.

You start from the branch you *want to merge into*, and then run:

```bash
git merge <branch-name>
```

Example:

```bash
git checkout main
git merge feature
```

---

# ⚙️ Types of Merge

There are **two main types** of merges in Git:

1. 🟢 **Fast-Forward Merge**
2. 🌀 **Three-Way (Non–Fast-Forward) Merge**

Let’s go step-by-step 👇

---

## 🟢 1️⃣ Fast-Forward Merge

This happens when **no new commits** exist on `main` since the branch was created.
Git can just *move the pointer forward*.

### Before Merge

```
main:    A
             \
feature:      B --- C
```

### After Merge (Fast-Forward)

```
main: A --- B --- C
```

✅ No new “merge commit” is created — it’s just a straight line of history.

---

## 🌀 2️⃣ Three-Way Merge (Normal Merge)

This happens when **both branches have new commits**,
so Git needs to *combine* the changes.

### Before Merge

```
         (common ancestor)
               A
             /   \
main:      B      feature: C --- D
```

Both branches diverged from commit **A**.

### Merge Command

```bash
git checkout main
git merge feature
```

### After Merge

```
             A
           /   \
        B       C --- D
          \         /
            \     /
              E (merge commit)
```

Git creates a new **merge commit (E)** to join histories.

📝 This merge commit stores:

* parent 1 → `main`’s last commit (B)
* parent 2 → `feature`’s last commit (D)

---

# 🔍 Visual Summary

| Type                | When It Happens         | What Happens          | Example Diagram |
| ------------------- | ----------------------- | --------------------- | --------------- |
| **Fast-forward**    | Main has no new commits | Moves pointer forward | `A → B → C`     |
| **Three-way merge** | Both branches changed   | Creates merge commit  | `A → B ↘ E ↙ C` |

---

# 🧩 Example in Commands

```bash
# Create and switch to a new branch
git checkout -b feature

# Make some changes and commit
git add .
git commit -m "Add feature work"

# Switch back to main
git checkout main

# Merge feature branch
git merge feature
```

If there were no new commits on main → **fast-forward**
If main had new commits → **three-way merge**

---

# ⚠️ Merge Conflicts

If Git cannot automatically merge (both branches edit the same lines),
you’ll get a **merge conflict**:

```
Auto-merging file.txt
CONFLICT (content): Merge conflict in file.txt
```

You’ll need to **manually fix** the conflict and then:

```bash
git add file.txt
git commit
```

---

# 🎯 In Short

| Concept         | Meaning                    |
| --------------- | -------------------------- |
| `git merge`     | Combines two branches      |
| Fast-forward    | Simple pointer move        |
| Three-way merge | Creates merge commit       |
| Merge conflict  | Happens when edits overlap |

---

