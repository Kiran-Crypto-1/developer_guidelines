# GitHub Publishing Guide

## Quick Start: Publishing to GitHub Pages

### Step 1: Create GitHub Repository

1. Go to GitHub and create a new repository
2. Name it `guidelines` (or your preferred name)
3. Make it public (for GitHub Pages) or private (if you have GitHub Pro)
4. **Do NOT** initialize with README, .gitignore, or license (we already have these)

### Step 2: Initialize Git and Push

Open terminal in the `guidelines` directory and run:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: EchorTech Developer Guidelines v1.0"

# Add remote (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/guidelines.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages** (in the left sidebar)
3. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)`
4. Click **Save**
5. GitHub will provide a URL like: `https://YOUR_USERNAME.github.io/guidelines/`

### Step 4: Access Your Published Site

- Your guidelines will be available at: `https://YOUR_USERNAME.github.io/guidelines/`
- It may take a few minutes for the first deployment
- Future commits to `main` will automatically update the site

## Alternative: Using GitHub Actions (Optional)

If you want more control over the deployment process, you can use GitHub Actions:

1. Create `.github/workflows/pages.yml`:
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

permissions:
  contents: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./
```

## File Structure for GitHub

Your repository should have this structure:

```
guidelines/
├── .gitignore
├── README.md
├── index.html          # Main webpage
├── GITHUB_SETUP.md     # This file
├── REVIEW_AND_RECOMMENDATIONS.md
└── EchorTech_Developer_Guidelines_Onboarding_v1 (1).pdf
```

## Custom Domain (Optional)

If you want to use a custom domain:

1. Add a `CNAME` file to the root with your domain:
   ```
   guidelines.echortech.com
   ```

2. Configure DNS:
   - Add a CNAME record pointing to `YOUR_USERNAME.github.io`

3. Update GitHub Pages settings:
   - Settings → Pages → Custom domain

## Updating the Guidelines

To update the guidelines:

```bash
# Make your changes to index.html
git add index.html
git commit -m "Update: [describe your changes]"
git push origin main
```

GitHub Pages will automatically rebuild and deploy within a few minutes.

## Troubleshooting

### Page Not Loading
- Check that GitHub Pages is enabled in Settings
- Verify the branch is set to `main`
- Wait 5-10 minutes for initial deployment

### 404 Errors
- Ensure `index.html` is in the root directory
- Check that the file is committed and pushed
- Verify the URL path is correct

### Styling Issues
- Clear browser cache
- Check browser console for errors
- Verify all external resources (Font Awesome) are loading

## Security Considerations

Since this is an internal document:
- Consider making the repository private
- Use GitHub's access controls
- Don't include sensitive information in the HTML
- Review the PDF file - ensure it doesn't contain confidential data

## Analytics (Optional)

To track page views, you can add:

1. Google Analytics
2. GitHub's built-in traffic insights (Settings → Insights → Traffic)
3. Plausible Analytics (privacy-friendly)

## Backup Strategy

- Keep a local copy of the repository
- Consider backing up to another Git hosting service
- Export the HTML periodically as a backup

---

**Need Help?** Check GitHub's official documentation: https://docs.github.com/en/pages

