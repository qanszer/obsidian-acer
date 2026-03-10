
2026-02-24  09:49 am

Tags: [[Guide]] [[Git]] [[Github]]

---
# Git HTTP and SSH Guide

## **Solution 1: GitHub CLI**

This handles authentication automatically:

```bash
# Install GitHub CLI
sudo apt update
sudo apt install gh

# Authenticate
gh auth login

# Follow the prompts:
# - Choose: GitHub.com
# - Choose: HTTPS
# - Authenticate: Login with a web browser (easiest)
# - Follow the browser prompts

# Now push will work automatically
git push origin fix-spelling-adv-dbms
```

---

## **Solution 2: SSH (Best Long-Term)**

SSH is more secure and doesn't require tokens:

### **Step 1: Generate SSH Key (if you don't have one)**

```bash
# Check if you have an SSH key
ls -la ~/.ssh/id_*.pub

# If nothing shows up, generate one:
ssh-keygen -t ed25519 -C "your_email@example.com"

# Press Enter for all prompts (default location, no passphrase is fine)

# Copy your public key
cat ~/.ssh/id_ed25519.pub
# Copy the entire output
```

### **Step 2: Add SSH Key to GitHub**

1. Go to GitHub.com → Settings
2. Click **SSH and GPG keys** (left sidebar)
3. Click **New SSH key**
4. Title: `Ubuntu Laptop` or whatever you want
5. Paste your public key (from the `cat` command above)
6. Click **Add SSH key**

### **Step 3: Change Your Remote to SSH**

```bash
# Change from HTTPS to SSH
git remote set-url origin git@github.com:qanszer/mkdocs_dknotes.git

# Verify
git remote -v
```


---

## References

Claude AI