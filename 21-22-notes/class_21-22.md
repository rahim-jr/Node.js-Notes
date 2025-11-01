# 📌 Git & GitHub Workflow Guide

---

## 1. **Core Concepts**

- **Git** → a version control system that tracks changes in your code.
- **GitHub** → a cloud-based hosting platform for Git repositories.
- **Repository (repo)** → the project’s codebase stored locally (on your machine) and remotely (on
  GitHub).
- **.git folder** → hidden folder in your project that stores metadata and history for Git tracking.

---

## 2. **Initialize & Connect to GitHub**

```bash
git init                # Initialize Git in your project
ls -a                   # List files, including hidden ones (.git/)
git remote add origin <repo-url>   # Connect to GitHub repo
```

🔍 Check connection:

```bash
cd .git/                # Inspect Git folder
ls -a                   # Check contents
cat config              # Verify remote URL in config file
cd ..                   # Return to project root
git status              # Check current status of repository
```

---

## 3. **Ignore Unwanted Files**

- Create a `.gitignore` file to prevent tracking unwanted files (e.g. `node_modules`, `.env`).
  Example `.gitignore`:

```
node_modules/
.env
dist/
```

---

## 4. **Staging & Committing**

```bash
git add filename        # Add a single file
git add .               # Add all changes
git commit -m "message" # Save changes in local Git
```

---

## 5. **Branching**

```bash
git branch                  # List branches
git branch <branch-name>    # Create a new branch
git switch <branch-name>    # Switch to a branch (new way)
git checkout -b <branch>    # Create + switch to a new branch (old way)
```

✅ Best practice: Use **feature branches** (`feature/login-page`, `bugfix/cart-issue`) instead of
working directly on `main`/`develop`.

---

## 6. **Pushing Changes**

```bash
git push origin <branch-name>      # Push branch to remote
git push --force-with-lease origin <branch-name>  # Safe force push
```

---

## 7. **Merging & Rebasing**

### 🔹 Normal Merge

```bash
git fetch
git merge origin/develop
# OR single command
git pull origin develop
```

- Keeps history intact with a **merge commit**.

### 🔹 Rebase

```bash
git fetch
git rebase origin/develop
# OR single command
git pull --rebase origin develop
```

- Re-applies your commits **on top of the latest develop branch**.
- Cleaner history, avoids merge commits.

### 🔹 Squash Merge

- Combine multiple commits into **one commit** before merging.

```bash
git rebase -i HEAD~<n>   # Interactive squash
```

---

## 8. **Logs & History**

```bash
git log --oneline        # Compact commit history
git log --graph --oneline --decorate --all  # Visualize branch history
```

---

## 9. **Cleaning Up**

```bash
rm -rf .git                  # Remove Git tracking entirely
git push origin -d <branch>  # Delete remote branch
git branch -d <branch>       # Delete local branch
```

---

## 10. **Best Practices**

- Always pull/rebase from `develop` (or main branch) before pushing.
- Commit **small, meaningful changes** with clear messages.
- Never commit `node_modules`, `.env`, or secrets.
- Use **feature branches** instead of pushing directly to `develop` or `main`.
- Prefer `--force-with-lease` instead of `--force` to avoid overwriting teammates’ work.

---
