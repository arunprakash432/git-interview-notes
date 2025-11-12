Here’s a clear explanation of the **`git config`** command, what it does, and how to use it.

---

# ✅ What is `git config`?

`git config` is used to **view and set Git configuration settings** such as your username, email, editor, aliases, and more.

These settings control how Git behaves.

---

# 📍 Levels of Configuration

| Level      | Scope                      | Where stored     |
| ---------- | -------------------------- | ---------------- |
| `--system` | All users on the system    | `/etc/gitconfig` |
| `--global` | Current user (most common) | `~/.gitconfig`   |
| `--local`  | Current repository only    | `.git/config`    |

If no level is specified, Git uses **local** by default.

---

# ✅ Common Uses

### 1️⃣ Set Username & Email (Required for commits)

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### 2️⃣ View Configuration

```bash
git config --list             # show all config values
git config user.name          # show a specific value
```

### 3️⃣ Set Default Editor

```bash
git config --global core.editor "code --wait"   # VS Code
git config --global core.editor "nano"
git config --global core.editor "vim"
```

### 4️⃣ Set Default Branch Name

```bash
git config --global init.defaultBranch main
```

### 5️⃣ Create Aliases (shortcuts)

```bash
git config --global alias.st status       # git st --> git status
git config --global alias.co checkout     # git co --> git checkout
git config --global alias.br branch       # git br --> git branch
git config --global alias.cm "commit -m"  # git cm "msg"
```

### 6️⃣ Color Output (for readability)

```bash
git config --global color.ui auto
```

---

# 🔍 How Configuration is Applied

When Git needs a setting (like user.name), it checks in this order:

1️⃣ Local
2️⃣ Global
3️⃣ System

First match wins.

---

# 🛠 Edit the Config File Directly

```bash
git config --global --edit
git config --system --edit
git config --local --edit
```

This opens the config file in your default editor.

---

# ✅ Example: Full Setup for a New Machine

```bash
git config --global user.name "Alice Smith"
git config --global user.email "alice@example.com"
git config --global core.editor "code --wait"
git config --global init.defaultBranch main
git config --global color.ui auto
```

---

# 🎯 In Summary:

`git config` lets you **set preferences, identity, behavior, and shortcuts** in Git.

---
