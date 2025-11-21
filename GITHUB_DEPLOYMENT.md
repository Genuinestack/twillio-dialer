# GitHub Deployment Guide

This guide will help you deploy your Twilio Dialer application to GitHub and set up continuous deployment.

## 📋 Prerequisites

- Git installed on your computer
- A GitHub account
- Your Twilio Dialer project ready to deploy

## 🚀 Step 1: Initialize Git Repository (if not already done)

If you haven't initialized a git repository yet, run these commands in your project directory:

```bash
cd twillio-dialer/lightning-dialer
git init
```

## 📝 Step 2: Add All Files to Git

```bash
# Add all files to staging
git add .

# Create your first commit
git commit -m "Initial commit: Twilio Dialer application"
```

## 🔗 Step 3: Create a GitHub Repository

1. **Go to GitHub**: Visit [https://github.com](https://github.com)
2. **Sign in** to your account
3. **Create a new repository**:
   - Click the "+" icon in the top right corner
   - Select "New repository"
   - Choose a repository name (e.g., `twilio-dialer`)
   - Add a description (optional)
   - Choose **Public** or **Private** (Private recommended for production apps)
   - **DO NOT** initialize with README, .gitignore, or license (we already have these)
   - Click "Create repository"

## 🔄 Step 4: Connect Local Repository to GitHub

After creating the repository, GitHub will show you commands. Use these commands in your terminal:

```bash
# Add the remote repository (replace YOUR_USERNAME and YOUR_REPO_NAME)
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git

# Rename the default branch to main (if needed)
git branch -M main

# Push your code to GitHub
git push -u origin main
```

**Example:**
```bash
git remote add origin https://github.com/johndoe/twilio-dialer.git
git branch -M main
git push -u origin main
```

## 🔐 Step 5: Set Up GitHub Secrets (For CI/CD)

If you plan to use GitHub Actions for deployment, you'll need to store sensitive information as GitHub Secrets:

1. Go to your repository on GitHub
2. Click **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret**
4. Add the following secrets (one at a time):

   - `TWILIO_ACCOUNT_SID` - Your Twilio Account SID
   - `TWILIO_ACCOUNT_TOKEN` - Your Twilio Auth Token
   - `TWILIO_APP_ID` - Your Twilio App ID
   - `TWILIO_CALLER_ID` - Your Twilio phone number
   - `TWILIO_QUEUE_NAME` - Your queue name (e.g., "CustomerService")
   - `TWILIO_DQUEUE_URL` - Your deployment URL
   - `MONGODB_URI` - Your MongoDB connection string
   - `RACK_ENV` - Set to "production"
   - `PORT` - Set to "10000" (or your preferred port)

## 🤖 Step 6: Set Up GitHub Actions (Optional - For Automated Deployment)

Create a GitHub Actions workflow file for automated deployment to platforms like Render, Heroku, or AWS.

### Create the workflow directory:

```bash
mkdir -p .github/workflows
```

### Create deployment workflow file:

Create `.github/workflows/deploy.yml` (see the example below in the file structure section)

## 📦 Step 7: Update README with GitHub Repository Link

Update your README.md to reflect your new GitHub repository URL:

```markdown
## 🚀 Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
   cd YOUR_REPO_NAME
   ```
```

## 🔄 Step 8: Future Updates

Whenever you make changes to your code:

```bash
# Check what files have changed
git status

# Add changed files
git add .

# Commit changes with a descriptive message
git commit -m "Description of your changes"

# Push to GitHub
git push
```

## 🌐 Step 9: Deploy from GitHub

### Option A: Deploy to Render (Recommended)

1. Go to [Render Dashboard](https://dashboard.render.com)
2. Click **New +** → **Web Service**
3. Connect your GitHub repository
4. Render will automatically detect your Ruby app
5. Set environment variables in Render dashboard
6. Deploy!

### Option B: Deploy to Heroku

1. Install Heroku CLI
2. Run:
   ```bash
   heroku create your-app-name
   git push heroku main
   ```

### Option C: Deploy to Railway

1. Go to [Railway](https://railway.app)
2. Click **New Project** → **Deploy from GitHub repo**
3. Select your repository
4. Railway will auto-detect and deploy

## 🔍 Verification

After pushing to GitHub:

1. Visit your repository URL: `https://github.com/YOUR_USERNAME/YOUR_REPO_NAME`
2. Verify all files are present
3. Check that sensitive files (`.env`) are NOT visible (they should be in `.gitignore`)

## ⚠️ Important Security Notes

- **Never commit** `.env` files or any files containing secrets
- Use GitHub Secrets for sensitive data in CI/CD
- Review your `.gitignore` file before committing
- If you accidentally committed secrets, rotate them immediately

## 🆘 Troubleshooting

### "Repository not found" error
- Check that you're using the correct repository URL
- Verify you have access to the repository
- Make sure you're authenticated with GitHub

### "Permission denied" error
- Set up SSH keys or use HTTPS with a personal access token
- For HTTPS, use: `https://YOUR_TOKEN@github.com/USERNAME/REPO.git`

### Files not showing up on GitHub
- Make sure you've run `git add .` and `git commit`
- Verify you've run `git push`

## 📚 Additional Resources

- [GitHub Documentation](https://docs.github.com)
- [Git Basics](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

---

**Need help?** Open an issue on your GitHub repository or check the main [README.md](README.md) for more information.


