To use Git (push/pull) with GitHub securely, GitHub now requires a **Personal Access Token (PAT)** instead of a password.
Here’s **exactly how to generate one step-by-step**:

---

# ✅ Step 1: Log in to GitHub

Go to **[https://github.com](https://github.com)** and sign in to your account.

---

# ✅ Step 2: Open Developer Settings

Top-right corner → **Profile Picture** → **Settings**
Scroll down the left sidebar → **Developer settings**

---

# ✅ Step 3: Go to Personal Access Tokens

Click **Personal access tokens**
Then choose:

* **Tokens (classic)** → common and simple
  *(or “Fine-grained tokens” if you need more control)*

---

# ✅ Step 4: Click “Generate new token”

If using classic:

* Click **Generate new token (classic)**

---

# ✅ Step 5: Give your token details

Fill in:
✅ **Note** → e.g. “Git CLI access”
✅ **Expiration** → Choose (e.g. 90 days or No expiration)
✅ **Scopes (Permissions)** → Check what you need:

* `repo` ✅ (required to push/pull code)
* `workflow` ✅ (if you use GitHub Actions)
* `read:org` ✅ (if in private org)

For basic Git use, **checking only `repo` is usually enough.**

---

# ✅ Step 6: Generate & COPY the token

Click **Generate token** at the bottom.

⚠️ IMPORTANT:
**COPY the token now!**
You will **not** see it again.

---

# ✅ Step 7: Use it instead of a password in Git

When Git asks for a **username and password**:

* Username → your GitHub username
* Password → **paste the token**

Example when pushing:

```bash
git push origin main
Username: your-username
Password: <paste token here>
```

---

# ✅ (Optional but Recommended) Save it permanently

Run this to let Git store the token securely:

```bash
git config --global credential.helper store
```

(or on Mac:

```bash
git config --global credential.helper osxkeychain
```

on Windows:

```bash
git config --global credential.helper manager
```

)

After one push, Git will remember the token.

---

# ✅ Done!

You can now push, pull, and clone from GitHub using your token.

---

