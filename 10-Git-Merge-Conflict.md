
---

# 💥 What is a Git Merge Conflict?

A **merge conflict** happens when **Git can’t automatically combine changes** from two branches.

Git tries to merge line by line, but if both branches **edit the same line(s)** in the same file (or one deletes while the other edits), Git doesn’t know which change to keep — so it asks **you** to decide.

---

# ⚙️ Example Scenario

You have a file called `hello.txt`:

```
Hello World
```

You create a feature branch and both branches modify the same line differently:

### On `main`

```
Hello from Main branch
```

### On `feature`

```
Hello from Feature branch
```

---

# 🔄 Visual Timeline

```
       A (common ancestor)
      / \
main B   C feature
```

* Commit **B** changes `hello.txt` to “Hello from Main branch”
* Commit **C** changes `hello.txt` to “Hello from Feature branch”

Now, you try to merge:

```bash
git checkout main
git merge feature
```

---

# 💣 Git Detects Conflict

Git stops the merge because it can’t decide which line to keep.

You’ll see a message:

```
Auto-merging hello.txt
CONFLICT (content): Merge conflict in hello.txt
Automatic merge failed; fix conflicts and then commit the result.
```

---

# 🧱 File Now Looks Like This

Git marks the conflicting area with special symbols:

```
<<<<<<< HEAD
Hello from Main branch
=======
Hello from Feature branch
>>>>>>> feature
```

### 🔍 Explanation:

* `<<<<<<< HEAD` → changes from **your current branch** (main)
* `=======` → separator between the two versions
* `>>>>>>> feature` → changes from **the branch you merged in**

---

# 🧰 How to Fix It

You manually edit the file to decide what should remain.

### Example resolution:

```
Hello from both branches
```

Then mark the conflict as resolved:

```bash
git add hello.txt
git commit
```

---

# ✅ Resulting History

After resolving and committing:

```
        A
       / \
    B     C
     \   /
      D (merge commit)
```

Where:

* **B** = main branch commit
* **C** = feature branch commit
* **D** = new merge commit after resolving conflicts

---

# 📊 Text-Based Diagram Summary

### Before Merge

```
(main)
A --- B
       \
        C --- (feature)
```

### During Merge → Conflict detected

```
(main) A --- B
          \
           C (feature)
          (conflict in hello.txt)
```

### After Resolving Conflict

```
A --- B --- D
     \     /
      C---
```

---

# 🧩 Common Causes of Merge Conflicts

| Cause                     | Example                                           |
| ------------------------- | ------------------------------------------------- |
| Both edited same line     | "Hello World" changed differently in two branches |
| One deleted, other edited | One branch deletes file, other modifies it        |
| File renamed differently  | File renamed in two branches differently          |
| Same new file added       | Two new files with same name in both branches     |

---

# 💡 Tips to Avoid or Handle Conflicts

✅ **Pull latest changes** before starting new work
✅ **Commit often** (smaller changes are easier to merge)
✅ Use tools like:

```bash
git mergetool
```

✅ If merge goes wrong:

```bash
git merge --abort
```

✅ Use `git diff` to understand differences before merging

---

# 🎯 Summary

| Concept              | Description                                       |
| -------------------- | ------------------------------------------------- |
| **Merge Conflict**   | Git can’t auto-merge because of overlapping edits |
| **Conflict Markers** | `<<<<<<<`, `=======`, `>>>>>>>` in files          |
| **Resolution**       | Edit manually → `git add` → `git commit`          |
| **Result**           | Merge commit created with resolved content        |

---

