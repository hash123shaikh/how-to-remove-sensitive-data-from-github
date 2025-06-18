# 🔐 How to Remove `.env` Files or Sensitive Data from GitHub

Accidentally pushed `.env`, passwords, or other credentials to GitHub? Don’t worry — this repo explains how to remove sensitive files from your Git history **safely and properly**.

---

## 🚫 Step 1: Prevent Future Mistakes Using `.gitignore`

Before pushing any project:

1. Create a `.gitignore` file (if not already present).
2. Add the sensitive file(s) to it:

```bash
# .gitignore
.env
*.env
*.key
*.pem
*.crt
```

---

## 🧹 Step 2: Remove Already Committed `.env` File
If you’ve already committed a sensitive file, follow these steps:

### 🧼 A. Remove It from the Current Commit

```bash
git rm --cached .env
git commit -m "Remove .env file from repository"
git push
```

This removes the file from Git **tracking**, but not from the history.

---

### 🧨 B. Remove It from Entire Git History (Using BFG or Filter-Repo)

**Option 1: Using BFG Repo Cleaner (Easy)**

1. Download: https://rtyley.github.io/bfg-repo-cleaner
2. Run:

```bash
bfg --delete-files .env
```

Then clean and push:

```bash
git reflog expire --expire=now --all && git gc --prune=now --aggressive
git push --force
```

---

**Option 2: Using Git Filter-Repo (Advanced)**

```bash
git filter-repo --path .env --invert-paths
```

This permanently deletes `.env` from your entire repo history.

---

## 🧠 Best Practices

* ✅ Always use `.gitignore` before pushing

* ✅ Use `.env.example` to share structure of `.env` without exposing secrets

* ❌ Never share AWS keys, tokens, or credentials in code

---

## 📦 Sample `.env.example`

```
**env** file

AWS_ACCESS_KEY=your_key_here
AWS_SECRET_KEY=your_secret_here
DB_HOST=localhost
```

---

## 📚 References

- [BFG Repo Cleaner](https://rtyley.github.io/bfg-repo-cleaner/)
- [Git Filter-Repo](https://github.com/newren/git-filter-repo)
- [GitHub Docs – Removing Sensitive Data](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository)

---

## 🙌 Feel Free to Clone & Share

Created by [@hash123shaikh](https://github.com/hash123shaikh) to help others avoid this common mistake.
