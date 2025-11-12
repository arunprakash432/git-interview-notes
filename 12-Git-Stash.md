
---

# 🧠 What is `git stash`?

**`git stash`** temporarily shelves (or "stashes") your uncommitted changes —
so you can **switch branches, pull updates, or work on something else** —
then **bring them back later**.

Think of it like:

> 💼 “Put my unfinished work in a drawer for now — I’ll grab it later.”

---

# ⚙️ Common Scenario

You’re working on a feature and make changes to a few files:

```
(feature)
A --- B
     \
      (your uncommitted edits here)
```

Then you realize:

> “Oops! I need to switch to `main` to fix a bug or pull updates!”

But Git says:

```
error: Your local changes would be overwritten by checkout
```

You can’t switch branches while you have uncommitted changes.

---

# 💼 Use `git stash`

You run:

```bash
git stash
```

Git takes your current changes (both **staged** and **unstaged**) and saves them in a **special stack**, then restores your working directory to the **last committed state**.

---

# 📊 Visual Diagram

Before `git stash`:

```
(feature)
A --- B
  \
   (modified files)
```

After `git stash`:

```
(feature)
A --- B        ← working directory clean
     ↑
   stash@{0}   ← your changes are saved here
```

✅ Your changes are safe in the **stash**
✅ You can now safely switch branches

---

# 🔁 When You’re Ready to Get Back

After you finish what you needed to do, you can **reapply** the stashed changes.

```bash
git stash apply     # reapplies latest stash (keeps it saved)
```

or

```bash
git stash pop       # reapplies latest stash AND removes it from stash list
```

---

# 🔄 Visual: Applying Back

After `git stash pop`:

```
(feature)
A --- B
  \
   (your changes restored)
```

The stash entry (`stash@{0}`) is removed after popping.

---

# 📚 Managing Multiple Stashes

You can have **multiple stashes** saved — Git keeps them in a **stack**.

### Example Commands:

```bash
git stash list          # see all stashes
git stash show stash@{0}  # see what’s inside a stash
git stash apply stash@{2} # apply a specific one
git stash drop stash@{0}  # delete a stash
git stash clear          # remove all stashes
```

---

# 🧩 Example Workflow

Let’s simulate it step-by-step 👇

### 1️⃣ You have uncommitted work:

```
$ git status
modified: index.html
modified: app.js
```

### 2️⃣ Save it away:

```
$ git stash
Saved working directory and index state WIP on feature: e1a2b3 Update UI
```

### 3️⃣ Switch branches:

```
$ git checkout main
```

### 4️⃣ Later, come back:

```
$ git checkout feature
$ git stash pop
```

Now your changes are back in your working directory 🎉

---

# ⚠️ Important Notes

| Behavior                                     | Explanation                              |
| -------------------------------------------- | ---------------------------------------- |
| Only stashes **uncommitted** changes         | Committed work is not affected           |
| Works on both tracked & staged files         | Unless you specify otherwise             |
| Doesn’t stash **untracked** files by default | Use `git stash -u` to include them       |
| You can have multiple stashes                | Stored as `stash@{0}`, `stash@{1}`, etc. |

---

# 🧭 Text-Based Summary Diagram

```
Before:
(feature) A --- B
             \
            (local edits)

After git stash:
(feature) A --- B     ← working dir clean
           ↑
         stash@{0}     ← uncommitted changes saved

After git stash pop:
(feature) A --- B
             \
            (local edits restored)
```

---

# 🎯 Summary

| Command           | What It Does                     |
| ----------------- | -------------------------------- |
| `git stash`       | Save current uncommitted changes |
| `git stash list`  | Show all saved stashes           |
| `git stash apply` | Reapply changes (keep in stash)  |
| `git stash pop`   | Reapply and remove from stash    |
| `git stash drop`  | Delete a specific stash          |
| `git stash clear` | Remove all stashes               |
| `git stash -u`    | Include untracked files too      |

---

✅ **In short:**

> `git stash` = "Temporarily hide my changes so I can work elsewhere safely."

---

