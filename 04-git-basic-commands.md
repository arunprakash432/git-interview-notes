
---

# ✅ 1. `git status`

**What it does:**
Shows the current state of your working directory and staging area.

**Use it to see:**

* Which files changed
* Which files are staged (ready to commit)
* Which files are untracked

**Example:**

```bash
git status
```

---

# ✅ 2. `git add`

**What it does:**
Stages changes so they are ready to commit.

**Examples:**

```bash
git add file.txt     # stage one file
git add .            # stage all changes in current folder
```

Think: “I want to include this in my next commit.”

---

# ✅ 3. `git commit`

**What it does:**
Creates a snapshot of staged changes with a message.

**Example:**

```bash
git commit -m "Add feature X"
```

Think: “Save this version with a message.”

---

# ✅ 4. `git log`

**What it does:**
Shows the history of commits.

**Example:**

```bash
git log
```

Tip: Press `q` to quit.

**Short version:**

```bash
git log --oneline
```

---

# ✅ 5. `git reset`

**What it does:**
Moves the HEAD (current position) to a previous commit.
Used to **undo** commits or unstage files.

### Common uses:

**Unstage a file:**

```bash
git reset file.txt
```

**Undo last commit but keep changes:**

```bash
git reset --soft HEAD~1
```

**Undo commit and delete changes permanently:**

```bash
git reset --hard HEAD~1
```

⚠️ Be careful with `--hard`!

---

# ✅ 6. `git push`

**What it does:**
Sends local commits to a **remote repository** (e.g., GitHub).

**Example:**

```bash
git push origin main
```

Think: “Upload my changes.”

---

# ✅ 7. `git remote add`

**What it does:**
Connects your local repo to a **remote server**.

**Example:**

```bash
git remote add origin https://github.com/user/repo.git
```

After this, you can push/pull using `origin`.

---

# ✅ 8. `git branch`

**What it does:**
Manages branches (parallel versions of your code).

**Examples:**

```bash
git branch       # list branches
git branch new-feature   # create a branch
```

Branches let you work on features without breaking `main`.

---

# ✅ 9. `git checkout`

**What it does:**

* Switch between branches or
* Restore files

**Examples:**

```bash
git checkout new-feature    # switch to branch
git checkout -b new-feature # create AND switch
git checkout file.txt       # undo changes in file
```

---

# 🎯 10-Second Summary Table

| Command      | Purpose                         |
| ------------ | ------------------------------- |
| `status`     | See changes and staging         |
| `add`        | Stage changes                   |
| `commit`     | Save a snapshot                 |
| `log`        | View commit history             |
| `reset`      | Undo/unstage/move HEAD          |
| `push`       | Send commits to remote          |
| `remote add` | Link to GitHub or server        |
| `branch`     | Manage branches                 |
| `checkout`   | Switch branches / restore files |

---

# ✅ Typical Workflow Example

```bash
git status          # see changes
git add .           # stage changes
git commit -m "Fix bug"   # commit
git branch feature   # create a branch
git checkout feature # switch to it
git push origin feature   # upload branch
```

---


