# Git Commit Amend

## Introduction

`git commit --amend` Git ka ek bahut useful command hai jo **last commit ko modify (edit)** karne ke liye use hota hai.

Is command ki help se aap:

* Last commit ka message change kar sakte hain.
* Last commit me bhooli hui files add kar sakte hain.
* Last commit ke content ko update kar sakte hain.

> Note: `git commit --amend` sirf **most recent (last) commit** par kaam karta hai.

---

# Why Use Git Amend?

Maan lo aapne commit kiya:

```bash
git commit -m "frist commit"
```

Baad me pata chala ki spelling mistake hai.

Ya phir commit karne ke baad yaad aaya ki ek file add karna bhool gaye.

Aise cases me naya commit banane ke bajay `git commit --amend` use kar sakte hain.

---

# Syntax

```bash
git commit --amend
```

Ya commit message directly change karne ke liye:

```bash
git commit --amend -m "new commit message"
```

---

# Example 1: Change Last Commit Message

### Current Commit

```bash
git log --oneline
```

Output:

```text
a1b2c3d frist commit
```

Message galat hai.

### Correct It

```bash
git commit --amend -m "first commit"
```

### Result

```bash
git log --oneline
```

Output:

```text
e4f5g6h first commit
```

Notice:

* Commit message update ho gaya.
* Commit hash bhi change ho gaya.

---

# Example 2: Add Forgotten File to Last Commit

Maan lo:

```bash
git add index.js
git commit -m "Add login page"
```

Baad me pata chala ki `style.css` add karna bhool gaye.

### Stage the Missing File

```bash
git add style.css
```

### Amend the Commit

```bash
git commit --amend
```

Git editor open hoga.

Commit message same rakh sakte hain.

Save and close.

### Result

Ab `style.css` bhi usi commit ka part ban jayegi.

Naya commit create nahi hoga.

---

# Example Workflow

```bash
git add .
git commit -m "Initial Commit"

# Forgot a file
git add style.css

git commit --amend
```

Final result:

```text
Initial Commit
```

Aur us commit me `style.css` bhi include ho jayegi.

---

# Checking Commit History

```bash
git log --oneline
```

Example Output:

```text
9f8e7d6 Add login page
```

Amend ke baad commit hash change ho sakta hai kyunki Git ek naya updated commit create karta hai.

---

# Amend After Push

Agar commit already GitHub par push ho chuka hai:

```bash
git commit --amend -m "Updated Message"
```

To normal push fail ho sakta hai.

Aise case me:

```bash
git push --force origin main
```

use karna pad sakta hai.

### Warning

Force push shared/team repositories me carefully use karein kyunki ye remote history ko rewrite karta hai.

---

# Git Amend vs New Commit

| Feature                     | git commit --amend | New Commit |
| --------------------------- | ------------------ | ---------- |
| Last commit edit karta hai  | Yes                | No         |
| New commit create karta hai | No                 | Yes        |
| Commit hash change hota hai | Yes                | No         |
| Small fixes ke liye useful  | Yes                | No         |

---

# Best Use Cases

* Commit message correction
* Forgot to add a file
* Small changes immediately after commit
* Clean commit history maintain karna

---

# Summary

`git commit --amend` ek powerful Git command hai jo last commit ko edit karne ke liye use hota hai. Iski madad se commit message change kar sakte hain, missing files add kar sakte hain aur commit ko update kar sakte hain bina extra commit create kiye.

### Important Commands

```bash
# Change last commit message
git commit --amend -m "New Message"

# Add forgotten file to last commit
git add .
git commit --amend

# Push amended commit
git push --force origin main
```
