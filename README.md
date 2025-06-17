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
--------
