Ah! The error:

```
fatal: not in a git directory
```

means **Git doesn’t see your current folder as a Git repository**.
Before setting config or pushing, you need to initialize Git in your project.

Let’s do it step by step 👇

---

## 🧩 Step 1 — Go to your project folder

```bash
cd "C:\Users\anjal\Desktop\workspace\Learning\node js\portfolio\anjali-portfolio"
```

---

## 🧩 Step 2 — Initialize Git

```bash
git init
```

✅ This creates a `.git` folder in your project and makes it a Git repo.

---

## 🧩 Step 3 — Configure your Git user

Now you can safely set your user info:

```bash
git config user.name "Anjali Rajwar"
git config user.email "anjalirajwar101@gmail.com"
```

> Optional: Add `--global` if you want this config for all repos:

```bash
git config --global user.name "Anjali Rajwar"
git config --global user.email "anjalirajwar101@gmail.com"
```

---

## 🧩 Step 4 — Add files and commit

```bash
git add .
git commit -m "Initial commit"
```

---

## 🧩 Step 5 — Connect to GitHub

1. Create a new repository on GitHub (e.g., `anjali-portfolio`)
2. Copy the GitHub remote URL, then run:

```bash
git remote add origin https://github.com/your-username/anjali-portfolio.git
```

---

## 🧩 Step 6 — Push to GitHub

```bash
git branch -M main   # Rename branch to main if not already
git push -u origin main
```

---

✅ After this, your project will be live on GitHub.

---

If you want, I can give you a **single set of commands** that will take your project from zero to **pushed on GitHub** in one go.
Do you want me to do that?
