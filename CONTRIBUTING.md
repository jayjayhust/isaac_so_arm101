
# Contributing Guidelines

Thank you for your interest in contributing!  
We welcome all kinds of contributions — bug reports, bug fixes, feature implementations, documentation improvements, and more.

Please follow these guidelines to ensure a smooth and productive collaboration.

---

## 🚀 Contribution Workflow

### 1. Fork the Repository

Click the **Fork** button at the top-right of the repository page to create your own copy.

### 2. Clone Your Fork


```bash
git clone git@github.com:<your-username>/IsaacLab-SO_100.git
cd IsaacLab-SO_100
```


### 3. Add the Original Repository as Upstream

To keep your fork up-to-date with the original project:

```bash
git remote add upstream https://github.com/MuammerBay/IsaacLab-SO_100.git
```

To fetch and merge changes from upstream later:

```bash
git fetch upstream
git merge upstream/main
```

### 4. Create a Feature Branch

Always create a new branch off `main` for your work.  
Use a **clear, kebab-case** name describing your contribution:

```bash
git checkout -b adds-contributing-guide
```

> ✅ Example: `fix-login-issue`, `add-dark-mode`

---

## ✅ Commit & Pull Request Guidelines

### Commit Messages

- Use **lowercase** messages  
- Start with a **third-person verb** (e.g., `adds`, `updates`, `fixes`)  
- Keep messages **short and descriptive**

**Examples:**

```
adds contributing guide  
fixes broken link in readme  
updates config for python 3.10
```

### Pull Request Titles

- Follow the same format as commit messages, except a upper case is expected for the first character
- Example: `Adds user authentication`, `Fixes login redirect bug`

---

## 📦 Push Your Changes

When your changes are ready:

```bash
git add .
git commit -m "adds contributing guide"
git push origin adds-contributing-guide
```

---

## 📬 Open a Pull Request (PR)

1. Go to your fork on GitHub.
2. Click **Compare & pull request**.
3. Set the **base repository** to `MuammerBay/IsaacLab-SO_100` and base branch to `main`.
4. Add a clear title and short description.
5. Submit the pull request!

---

## ℹ️ Best Practices

- ✅ Keep PRs focused and minimal — one feature or fix per PR  
- 🚫 Avoid unrelated changes  
- 📖 Update documentation if needed  
- 💬 Ask questions in the PR if anything is unclear

---

Thank you again for contributing! 💙  
Let’s build something great together.

