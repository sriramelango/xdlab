# GitHub Pages Setup Guide

## Current Status
✅ Your repository is already well-configured for GitHub Pages with:
- Jekyll site structure with `_config.yml`
- `github-pages` gem in Gemfile
- Proper layouts and content structure

## Steps to Publish on GitHub Pages

### 1. Repository Setup
1. **Push your code to GitHub** (if not already done):
   ```bash
   git add .
   git commit -m "Initial commit for GitHub Pages"
   git push origin main
   ```

### 2. Update Configuration for GitHub Pages

#### Update `_config.yml`
You need to update the `url` and potentially the `baseurl` in your `_config.yml`:

**If your repository name is `XDLAB`:**
```yaml
url: "https://yourusername.github.io"
baseurl: "/XDLAB"
```

**If your repository name is `yourusername.github.io`:**
```yaml
url: "https://yourusername.github.io"
baseurl: ""
```

Replace `yourusername` with your actual GitHub username.

### 3. Enable GitHub Pages

1. Go to your repository on GitHub
2. Click on **Settings** tab
3. Scroll down to **Pages** section in the left sidebar
4. Under **Source**, select:
   - **Deploy from a branch**
   - Choose **main** branch (or **master** if that's your default)
   - Choose **/ (root)** folder
5. Click **Save**

### 4. GitHub Actions Workflow (Recommended)

For better control and modern deployment, create a GitHub Actions workflow:

Create `.github/workflows/jekyll-gh-pages.yml`:
```yaml
name: Deploy Jekyll with GitHub Pages dependencies preinstalled

on:
  push:
    branches: [ "main" ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Pages
        uses: actions/configure-pages@v4
      - name: Build with Jekyll
        uses: actions/jekyll-build-pages@v1
        with:
          source: ./
          destination: ./_site
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

Then in GitHub Pages settings, change the source to **GitHub Actions**.

### 5. Verify Deployment

1. After enabling Pages, GitHub will provide a URL like:
   - `https://yourusername.github.io/XDLAB/` (for project pages)
   - `https://yourusername.github.io/` (for user/org pages)

2. It may take a few minutes for the site to build and deploy
3. Check the **Actions** tab to see the build status

### 6. Configuration Files to Update

#### Update navigation links (if using absolute URLs)
In your `_layouts/default.html`, ensure navigation links work with the baseurl:
```html
<a href="{{ '/' | relative_url }}">Home</a>
<a href="{{ '/team/' | relative_url }}">Team</a>
<a href="{{ '/publications/' | relative_url }}">Publications</a>
<a href="{{ '/research/' | relative_url }}">Research</a>
```

#### Update asset paths
Ensure CSS and JS files use relative URLs:
```html
<link rel="stylesheet" href="{{ '/assets/css/main.css' | relative_url }}">
<script src="{{ '/assets/js/main.js' | relative_url }}"></script>
```

### 7. Test Locally Before Deploying

Always test your changes locally:
```bash
bundle install
bundle exec jekyll serve
```

Visit `http://localhost:4000` to preview your site.

### 8. Common Issues and Solutions

#### Issue: Site shows 404 or doesn't load
- **Solution**: Check that `baseurl` in `_config.yml` matches your repository name
- **Solution**: Ensure all links use `| relative_url` filter

#### Issue: CSS/JS not loading
- **Solution**: Update asset paths to use `| relative_url` filter
- **Solution**: Check that files exist in the correct locations

#### Issue: Build fails
- **Solution**: Check the Actions tab for error details
- **Solution**: Ensure Gemfile has correct `github-pages` gem version
- **Solution**: Check Jekyll compatibility with GitHub Pages

### 9. Custom Domain (Optional)

If you want to use a custom domain:
1. Add a `CNAME` file to your repository root with your domain name
2. Configure DNS settings with your domain provider
3. Update the `url` in `_config.yml` to your custom domain

## Quick Checklist

- [ ] Repository pushed to GitHub
- [ ] `_config.yml` updated with correct URL and baseurl
- [ ] GitHub Pages enabled in repository settings
- [ ] Site builds successfully (check Actions tab)
- [ ] Site loads correctly at the GitHub Pages URL
- [ ] All links and assets work properly

## Next Steps

1. Update your `_config.yml` with the correct URL and baseurl
2. Push changes to GitHub
3. Enable GitHub Pages in repository settings
4. Wait for deployment and test your live site

Your site should be live within a few minutes of enabling GitHub Pages!