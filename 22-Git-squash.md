
---

# 🧠 What Is Git Squash?

**Git squash** means **combining multiple commits into a single commit**.

You use it to **tidy up your commit history** before merging a branch — especially when you have lots of small, messy commits like:

```
fix typo
add console.log
remove console.log
update README
final fix
```

You can **squash them into one clean commit**, for example:

```
feat: add login feature
```

> 💡 Think of it as:
> “Merging multiple small snapshots into one polished snapshot.”

---

# ⚙️ When to Use Git Squash

✅ Before merging a feature branch into `main`
✅ To simplify long commit histories
✅ To remove “noise” (e.g., temporary commits)
✅ During pull request cleanup

---

# 🧩 Example Scenario

You’re on a `feature/login` branch with these commits:

```
* 9d7c8e5 fix: handle login errors
* 1a2b3c4 feat: add login form
* 7e6f5d4 initial commit for login
```

You want to merge them into a **single clean commit** before merging to `main`.

---

# 🔧 Step 1: Start Interactive Rebase

You can squash commits using **interactive rebase**:

```bash
git rebase -i HEAD~3
```

Here:

* `HEAD~3` = look at the last 3 commits
* You’ll see something like this:

```
pick 7e6f5d4 initial commit for login
pick 1a2b3c4 feat: add login form
pick 9d7c8e5 fix: handle login errors
```

---

# 🔧 Step 2: Mark Commits to Squash

Keep the first one as `pick` and change the rest to `squash` (or just `s`):

```
pick 7e6f5d4 initial commit for login
squash 1a2b3c4 feat: add login form
squash 9d7c8e5 fix: handle login errors
```

Then save and close the editor.

---

# 🔧 Step 3: Edit Commit Message

Git will open another editor asking for the new message.
You can either:

* Combine all messages, or
* Write a new, cleaner message like:

```
feat: implement login feature
- added login form
- handled login errors
```

Save and close.

---

# ✅ Step 4: Done!

Now your 3 commits are **squashed into 1**:

```
* a4b3c2d feat: implement login feature
```

---

# 📊 Text-Based Diagram

Before squash:

```
main
 \
  feature/login
    ├── commit A (initial)
    ├── commit B (add form)
    └── commit C (fix error)
```

After squash:

```
main
 \
  feature/login
    └── commit D (clean single commit)
```

All three commits (`A`, `B`, `C`) are replaced with **one** commit (`D`).

---

# ⚙️ Squashing During Merge (GitHub Shortcut)

If you’re merging via GitHub Pull Request (PR), there’s a built-in **“Squash and merge”** option.

When you click it:

* All commits from the PR branch get combined into one.
* The resulting single commit gets added to the target branch.

✅ No command-line needed.
✅ Keeps `main` history clean.

---

# 🧩 Git Commands Summary

| Command                | Purpose                                     |
| ---------------------- | ------------------------------------------- |
| `git rebase -i HEAD~N` | Start interactive rebase for last N commits |
| `pick`                 | Keep commit as-is                           |
| `squash` (or `s`)      | Combine commit with the one above it        |
| `fixup` (or `f`)       | Squash + discard commit message             |
| `git log --oneline`    | Verify the result                           |

---

# ⚠️ Important Notes

* Only **squash local commits** (not yet pushed to shared branches)
  → Otherwise, history rewrite can confuse others.
* After squashing, commit hash changes → You may need to force push:

  ```bash
  git push --force
  ```

---

# 🧭 Example Workflow

```bash
# 1. Check recent commits
git log --oneline

# 2. Start interactive rebase for last 4 commits
git rebase -i HEAD~4

# 3. Mark which commits to squash
# (pick the first one, squash the rest)

# 4. Edit the message, save and exit

# 5. Verify
git log --oneline

# 6. Push changes
git push --force
```

---

# 🧾 Real-Life Example

Before:

```
* 8d2e3b1 fix: typo in login handler
* 7c1a9e3 feat: add login validation
* 5b4a8f7 feat: create login form
```

After squash:

```
* 1f2a3b4 feat: implement login feature
```

---

# ✅ In Summary

| Concept             | Description                                      |
| ------------------- | ------------------------------------------------ |
| **Git squash**      | Combines multiple commits into one               |
| **Command**         | `git rebase -i HEAD~N`                           |
| **Purpose**         | Clean, readable commit history                   |
| **Use case**        | Before merging branches                          |
| **GitHub Shortcut** | “Squash and merge” button on PRs                 |
| **Caution**         | Don’t squash shared commits without coordination |

---

# 💡 In Simple Terms

> 🧩 **Git squash** = “Compress my messy commit history into one beautiful, meaningful commit.”

---

