
---

# 🧠 What Is Forking?

**Forking** means **creating your own copy** of someone else’s GitHub repository under your own account.
It’s like cloning — but on GitHub’s servers — giving you full control to experiment **without affecting the original project**.

> 💡 Think of a fork as:
> “My own sandbox copy of your repo.”

---

# ⚙️ Forking Workflow (Typical in Open Source)

```
Original Repository:
github.com/original-author/project

Your Fork:
github.com/your-username/project
```

Now you have your own copy! 🎉
You can make changes freely — commit, branch, test, etc.

---

# 🧩 Step-by-Step Fork Workflow

### 1️⃣ Fork the repository

On GitHub → click **Fork** (top right corner of the repo page)

GitHub creates:

```
original-author/project  →  your-username/project (your fork)
```

---

### 2️⃣ Clone your fork locally

```bash
git clone git@github.com:your-username/project.git
```

Now you’re working with your **own** repo.

---

### 3️⃣ Add the original repo as an upstream remote

To keep your fork updated:

```bash
git remote add upstream https://github.com/original-author/project.git
```

Now you have two remotes:

| Name       | URL           | Purpose                     |
| ---------- | ------------- | --------------------------- |
| `origin`   | your fork     | where you push your changes |
| `upstream` | original repo | where you pull updates from |

---

### 4️⃣ Create a feature branch

```bash
git checkout -b feature/add-login
```

Make your code changes, commit, and push:

```bash
git push origin feature/add-login
```

---

### 5️⃣ Open a **Pull Request (PR)**

On GitHub, go to your fork → click **Compare & pull request**.

Target:

* **Base repository:** `original-author/project`
* **Base branch:** `main`
* **Head repository:** `your-username/project`
* **Head branch:** `feature/add-login`

This requests the maintainers to **review** and **merge** your changes.

---

# 🧭 Text-Based Diagram: Fork + PR Flow

```
            +----------------------------+
            |   Original Repo (upstream) |
            |   github.com/original/...  |
            +-------------^--------------+
                          |
                      Pull Request
                          |
       +------------------+------------------+
       |                                     |
Your Fork (origin)                    Other Contributors
github.com/you/...                    (their own forks)
```

---

# 🧩 What Happens in a Pull Request (PR)

A **Pull Request** is a formal way to say:

> “Hey, please pull (merge) my changes into your repository.”

It triggers a **code review process** and **automated checks** before merging.

---

# ✅ Pull Request Approval Process

When you open a PR, here’s what typically happens:

1️⃣ **CI/CD Checks Run**

* Automated tests (GitHub Actions, Jenkins, etc.)
* Linting, code style, build verification

2️⃣ **Code Review by Team or Maintainers**

* Reviewers inspect the code
* They may request changes or approve

3️⃣ **Approvals**

* Required reviewers must approve before merging
  (configured in *branch protection rules*)

4️⃣ **Merge**

* Once approved and all checks pass → you or the maintainer clicks **Merge pull request**

5️⃣ **Delete the branch (optional)**

* The feature branch is cleaned up after merging.

---

# 🧱 Text Diagram: Pull Request & Approval

```
[Your Fork]
feature/add-login
      |
      v
   Pull Request →   [Original Repo: main]
        \
         +---> Reviewer checks code
               |
               +--> ✅ Approve → Merge into main
               |
               +--> ❌ Request changes → fix & update branch
```

---

# 💡 Pull Request States

| State                | Meaning                                |
| -------------------- | -------------------------------------- |
| 🟡 Open              | Waiting for review or checks           |
| 🟢 Approved          | Reviewers approved, ready to merge     |
| 🔴 Changes Requested | Needs updates before approval          |
| ⚪️ Closed            | PR closed without merging              |
| 🔵 Merged            | Successfully merged into target branch |

---

# 🧭 Example Git Commands Summary

```bash
# Fork is on GitHub (no command needed)
git clone git@github.com:your-username/repo.git
cd repo

# Add original repo as upstream
git remote add upstream https://github.com/original/repo.git

# Create feature branch
git checkout -b feature/my-update
# make changes, commit
git add .
git commit -m "Add new login feature"

# Push to your fork
git push origin feature/my-update

# On GitHub → Open Pull Request
```

---

# 🧾 Real-World Example

```
Original Repo:  github.com/microsoft/vscode
Your Fork:      github.com/you/vscode
Branch:         feature/improve-search
PR Target:      microsoft/vscode → main
```

Reviewers approve, CI passes → merged 🎉

---

# ⚙️ Forking vs. Cloning

| Concept   | Fork                           | Clone                                 |
| --------- | ------------------------------ | ------------------------------------- |
| Done on   | GitHub (server)                | Local machine                         |
| Ownership | You own your fork              | Original repo owner still owns source |
| Purpose   | Contribute to others’ projects | Work locally                          |
| Command   | Done via GitHub UI             | `git clone` in terminal               |

---

# ✅ Summary

| Concept                     | Description                                              |
| --------------------------- | -------------------------------------------------------- |
| **Forking**                 | Creating your own copy of a GitHub repo (your sandbox)   |
| **Pull Request (PR)**       | Asking to merge your changes into another repo           |
| **PR Approval**             | Reviewers approve after reviewing & testing your code    |
| **Branch Protection Rules** | Can enforce approvals and passing checks                 |
| **Merging**                 | Combines your branch into the main branch after approval |

---

# 🧠 In Simple Terms

> Fork = your personal copy of a repo.
> Pull Request = your formal request to merge changes.
> Approval = reviewers say “yes, this is safe and ready.”

---

