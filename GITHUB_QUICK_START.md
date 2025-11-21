# 🚀 Quick Start: Deploy to GitHub

Follow these simple steps to push your Twilio Dialer to GitHub:

## Step 1: Initialize Git (if needed)

```bash
cd twillio-dialer/lightning-dialer
git init
```

## Step 2: Add and Commit Files

```bash
git add .
git commit -m "Initial commit: Twilio Dialer application"
```

## Step 3: Create GitHub Repository

1. Go to https://github.com/new
2. Enter repository name (e.g., `twilio-dialer`)
3. Choose **Private** (recommended) or **Public**
4. **DO NOT** check "Initialize with README"
5. Click **Create repository**

## Step 4: Connect and Push

Replace `YOUR_USERNAME` and `YOUR_REPO_NAME` with your actual values:

```bash
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git branch -M main
git push -u origin main
```

**Example:**
```bash
git remote add origin https://github.com/johndoe/twilio-dialer.git
git branch -M main
git push -u origin main
```

## ✅ Done!

Your code is now on GitHub! Visit `https://github.com/YOUR_USERNAME/YOUR_REPO_NAME` to see it.

## 🔄 Next Steps

- **Deploy to Render**: Connect your GitHub repo in Render dashboard
- **Set up CI/CD**: See [GITHUB_DEPLOYMENT.md](GITHUB_DEPLOYMENT.md) for GitHub Actions
- **Add collaborators**: Go to Settings → Collaborators

## ⚠️ Important

- Never commit `.env` files (already in `.gitignore`)
- Use GitHub Secrets for sensitive data in CI/CD
- Keep your repository private if it contains business logic

---

For detailed instructions, see [GITHUB_DEPLOYMENT.md](GITHUB_DEPLOYMENT.md)


