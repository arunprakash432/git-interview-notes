
---

# 🧠 What Are Branch Protection Rules?

**Branch Protection Rules** are **settings in GitHub** (or other Git platforms) that control **what can and can’t happen on specific branches** — usually your *main* or *production* branch.

They prevent unwanted changes, accidental deletions, or unreviewed code from being merged.

> 💡 Think of them as “safety locks” on important branches.

---

# 🧱 Example

Let’s say you have these branches:

```
main      ← production-ready code (protected)
develop   ← testing or staging
feature-x ← your new feature
```

You don’t want anyone to:

* Directly push code into `main`
* Merge unreviewed pull requests
* Force-push or delete the branch

So you add **branch protection rules** to `main`.

---

# ⚙️ Where to Set Them (in GitHub)

Go to:

```
GitHub → Your Repository → Settings → Branches → Branch Protection Rules → Add rule
```

You can apply rules to:

* A specific branch (e.g. `main`)
* A pattern (e.g. `release/*` or `develop`)

---

# 🧩 Common Branch Protection Options

Here are the most used protection settings you’ll see in GitHub:

| Option                                     | Description                                           |
| ------------------------------------------ | ----------------------------------------------------- |
| ✅ **Require pull request before merging**  | Prevents direct pushes — you must open a PR           |
| 👥 **Require approvals**                   | PR must be approved by one or more reviewers          |
| 🧪 **Require status checks to pass**       | CI/CD tests must succeed before merging               |
| 🕒 **Require branch to be up to date**     | Ensures the branch includes latest `main` commits     |
| 🚫 **Restrict who can push to the branch** | Only certain users or teams can push                  |
| 🔒 **Include administrators**              | Rules also apply to admins (optional)                 |
| ❌ **Disallow force pushes**                | Prevents rewriting commit history                     |
| ❌ **Disallow deletions**                   | Stops users from deleting the branch                  |
| 🧾 **Require signed commits**              | Enforces GPG-signed commits for identity verification |

---

# 🧭 Text-Based Visual: How It Works

```
                 +--------------------------+
                 |   Branch Protection Rule  |
                 +--------------------------+
                                |
                                ↓
Developers → [feature-branch] → Pull Request → ✅ Review → ✅ Tests → 🔀 Merge → main (protected)
                                ↑
                      (cannot push directly)
```

✅ You can still work on branches
❌ But you **can’t** push directly to `main` or merge without approval

---

# 💼 Example: Typical Team Workflow with Protection Rules

```
1. Create feature branch
   git checkout -b feature/login

2. Work and commit code

3. Push branch
   git push origin feature/login

4. Open Pull Request → target = main

5. CI tests run automatically

6. Reviewer approves PR ✅

7. Merge allowed (main updated)
```

If any rule fails (e.g., no review, failed tests) → merge is blocked 🚫

---

# 🧩 Example Rules Configuration (in GitHub)

| Rule                                         | Status |
| -------------------------------------------- | ------ |
| Require pull request reviews before merging  | ✅      |
| Require status checks to pass before merging | ✅      |
| Require branches to be up to date            | ✅      |
| Include administrators                       | ✅      |
| Allow force pushes                           | ❌      |
| Allow deletions                              | ❌      |

---

# 🔒 Visual Summary

```
Without Protection:
-------------------
feature → main   (anyone can push)
❌ Risk of mistakes, overwriting, or broken code


With Protection:
----------------
feature → Pull Request → review + checks → merge → main ✅
✅ Safer
✅ Reviewed
✅ Tested
```

---

# ⚠️ Why They Matter

Branch protection rules help teams:

* Maintain **code quality** ✅
* Avoid **accidental overwrites or force-pushes** 🔒
* Ensure **peer review and testing** before merging 👥
* Keep main branches **stable and production-ready** 🚀

---

# 🧠 In Summary

| Concept                     | Description                                              |
| --------------------------- | -------------------------------------------------------- |
| **Branch Protection Rules** | Restrictions that prevent unsafe actions on key branches |
| **Typical Target**          | `main`, `master`, or `release/*` branches                |
| **Purpose**                 | Enforce reviews, tests, and controlled merges            |
| **Set In**                  | GitHub → Repo Settings → Branches                        |
| **Helps With**              | Collaboration, CI/CD enforcement, code safety            |

---

✅ **In short:**

> **Branch Protection Rules** are GitHub’s guardrails —
> they make sure that *only tested, reviewed, and authorized* code makes it into important branches like `main`.

---

