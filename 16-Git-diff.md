
---

# 🧠 What is `git diff`?

`git diff` shows the **differences (diff)** between:

* your **working directory** and the **staging area**
* your **staging area** and the **last commit**
* or between **any two commits/branches**

In short:

> 🧩 `git diff` = “Show me what’s changed.”

---

# ⚙️ Basic Use Cases

| Command                        | Compares                         | Description                            |
| ------------------------------ | -------------------------------- | -------------------------------------- |
| `git diff`                     | Working directory ↔ Staging area | See *unstaged* changes                 |
| `git diff --staged`            | Staging area ↔ Last commit       | See *staged* (ready-to-commit) changes |
| `git diff <commit1> <commit2>` | Two commits                      | See changes between commits            |
| `git diff branch1..branch2`    | Two branches                     | See what differs between branches      |

---

# 📘 Example Scenario

Let’s say you have a file named `app.js`:

**Original (committed) version:**

```js
console.log("Hello World");
```

You edit it to:

```js
console.log("Hello Universe");
console.log("Goodbye World");
```

---

# 🧩 Running `git diff`

When you run:

```bash
git diff
```

You’ll see something like this:

```
diff --git a/app.js b/app.js
index 1a2b3c..4d5e6f 100644
--- a/app.js
+++ b/app.js
@@ -1 +1,2 @@
-console.log("Hello World");
+console.log("Hello Universe");
+console.log("Goodbye World");
```

---

# 🧭 How to Read This

| Symbol      | Meaning                              |
| ----------- | ------------------------------------ |
| `-`         | Line removed (from previous version) |
| `+`         | Line added (in new version)          |
| `@@`        | Shows the affected line range        |
| `--- a/...` | Old file                             |
| `+++ b/...` | New file                             |

---

# 📊 Visual Diagram

```
Working Directory:   app.js (modified)
Staging Area:         unchanged
Last Commit:          app.js (old)

git diff
↓
Shows difference between:
Working Directory ↔ Staging Area
```

If you **stage** the change:

```bash
git add app.js
git diff
```

→ shows nothing (no unstaged changes).

But:

```bash
git diff --staged
```

→ shows differences between **staged version** and **last commit**.

---

# 🧱 Comparing Commits or Branches

You can also use `git diff` to compare any two commits or branches:

```bash
git diff main feature
```

Visual:

```
main:     A --- B --- C
                 \
feature:           D --- E

git diff main feature
↓
Shows what’s in feature but not in main
```

---

# 🧰 More Useful Variants

| Command                | Description                                             |
| ---------------------- | ------------------------------------------------------- |
| `git diff --name-only` | Shows only filenames changed                            |
| `git diff --stat`      | Shows summary of changes (how many lines added/removed) |
| `git diff HEAD`        | Compare working directory to last commit                |
| `git diff HEAD~1 HEAD` | Compare last two commits                                |
| `git diff origin/main` | Compare local branch to remote branch                   |

Example (summary view):

```
$ git diff --stat
 app.js | 2 +-
 style.css | 5 +++++
 2 files changed, 6 insertions(+), 1 deletion(-)
```

---

# ⚠️ Important Note

* `git diff` only shows changes that **aren’t committed yet** (by default).
* Once you commit, you need to specify commits or branches to see the diff.

---

# 🧩 Real-Life Example Workflow

```bash
# Modify a file
echo "New line" >> index.html

# Check unstaged changes
git diff

# Stage it
git add index.html

# Check staged changes
git diff --staged

# Commit it
git commit -m "Add new line"
```

---

# 🧭 Summary Table

| Command                        | Compares                   | Used For                   |
| ------------------------------ | -------------------------- | -------------------------- |
| `git diff`                     | Working dir ↔ Staging area | See unstaged changes       |
| `git diff --staged`            | Staging area ↔ Last commit | See staged changes         |
| `git diff HEAD`                | Working dir ↔ Last commit  | See all current changes    |
| `git diff branch1..branch2`    | Two branches               | Compare branch differences |
| `git diff <commit1> <commit2>` | Two commits                | Compare specific commits   |

---

# ✅ In Simple Terms

> 🪶 `git diff` is like Git’s “preview changes” tool —
> it shows **what changed, where, and how** before you commit or merge.

---

