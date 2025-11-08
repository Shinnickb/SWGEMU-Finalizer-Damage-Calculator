# GitHub Pages Setup Instructions

Follow these steps to publish your SWGEMU Damage Calculator on GitHub Pages:

## Prerequisites

- A GitHub account
- Git installed on your computer (if not installed, download from [git-scm.com](https://git-scm.com/))

## Step 1: Create a GitHub Repository

1. Go to [GitHub.com](https://github.com) and sign in
2. Click the "+" icon in the top right corner
3. Select "New repository"
4. Name your repository (e.g., `swgemu-damage-calculator`)
5. Choose "Public" (required for free GitHub Pages)
6. **Do NOT** initialize with README, .gitignore, or license (we already have these)
7. Click "Create repository"

## Step 2: Initialize Git and Push Files

Open PowerShell or Command Prompt in your project folder ( ) and run:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: SWGEMU Damage Calculator"

# Add your GitHub repository as remote (replace YOUR_USERNAME and REPO_NAME)
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git

# Push to GitHub
git branch -M main
git push -u origin main
```

**Note:** You'll be prompted for your GitHub username and password (or personal access token).

**Troubleshooting `git add .` error:**
If you get an error like `'SWGEMU Damage Calculator_files/' does not have a commit checked out`:
- This means there's a nested Git repository in that folder
- Remove it with: `Remove-Item -Recurse -Force "SWGEMU Damage Calculator_files\.git"` (PowerShell) or `rm -rf "SWGEMU Damage Calculator_files/.git"` (Linux/Mac)
- Then try `git add .` again

## Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click on "Settings" (top menu)
3. Scroll down to "Pages" in the left sidebar
4. Under "Source", select "Deploy from a branch"
5. Choose "main" branch and "/ (root)" folder
6. Click "Save"
7. Wait a few minutes for GitHub to build your site

## Step 4: Access Your Site

Your site will be available at:
```
https://YOUR_USERNAME.github.io/REPO_NAME/
```

For example, if your username is `johndoe` and repository is `swgemu-calc`:
```
https://johndoe.github.io/swgemu-calc/
```

## Updating Your Site

Whenever you make changes:

```bash
git add .
git commit -m "Description of changes"
git push
```

GitHub Pages will automatically update within a few minutes.

## Troubleshooting

- **Files not loading?** Make sure the folder name `SWGEMU Damage Calculator_files` matches exactly (with spaces)
- **404 Error?** Wait 5-10 minutes after enabling Pages, or check that `index.html` is in the root directory
- **JavaScript errors?** Open browser console (F12) to see specific errors

## Cloudflare Pages Deployment (Alternative)

If you're using Cloudflare Pages instead of GitHub Pages:

### Step 1: Deploy to Cloudflare Pages

1. Go to [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. Navigate to "Workers & Pages" → "Pages"
3. Click "Create a project"
4. Connect your Git repository (GitHub, GitLab, or Bitbucket)
5. Configure build settings:
   - **Build command:** Leave empty (static site)
   - **Build output directory:** `/` (root)
6. Click "Save and Deploy"

### Step 2: Fix SSL/TLS Error

If you're getting "SSL_ERROR_NO_CYPHER_OVERLAP" or "Secure Connection Failed":

#### Option A: Using Default `.pages.dev` Domain

If you're using the default Cloudflare Pages domain (e.g., `your-project.pages.dev`):
- SSL/TLS is **automatically enabled** and should work
- The error is likely a **browser/client-side issue**

**Try these fixes:**
1. **Clear browser cache and cookies** for the site
2. **Try a different browser** (Chrome, Firefox, Edge)
3. **Try incognito/private mode**
4. **Check your system date/time** - incorrect date can cause SSL errors
5. **Disable browser extensions** temporarily (especially security/SSL-related ones)
6. **Wait 10-15 minutes** - sometimes SSL certificates need time to propagate

#### Option B: Using Custom Domain

If you're using a custom domain (e.g., `yourdomain.com`):

1. **First, add your domain to Cloudflare:**
   - Go to Cloudflare Dashboard home
   - Click **"Add a Site"**
   - Enter your domain and follow the setup wizard
   - Update your domain's nameservers as instructed

2. **Then configure SSL/TLS:**
   - Once your domain is added, click on it in the dashboard
   - Now you'll see **"SSL/TLS"** in the left sidebar
   - Set **SSL/TLS encryption mode** to **"Full"** or **"Full (strict)"**
   - Go to **"SSL/TLS"** → **"Edge Certificates"**
   - Enable **"Always Use HTTPS"**
   - Set **"Minimum TLS Version"** to **"1.2"** or **"1.3"**

3. **Link domain to Pages project:**
   - Go back to **"Workers & Pages"** → **"Pages"** → Your project
   - Click **"Custom domains"** tab
   - Add your custom domain
   - Cloudflare will automatically configure SSL

### Step 3: Verify Deployment

1. Go to your Pages project
2. Check the **"Deployments"** tab - make sure the latest deployment shows "Success"
3. Click on the deployment to see the live URL
4. Try accessing the site using the **`.pages.dev`** URL first to verify it works

## Need Help?

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Cloudflare Pages Documentation](https://developers.cloudflare.com/pages/)
- [Cloudflare SSL/TLS Troubleshooting](https://developers.cloudflare.com/ssl/troubleshooting/)
- [Git Documentation](https://git-scm.com/doc)


