# GitHub Pages Troubleshooting Guide

## Issues Found in Your Current Setup

### 🚨 Critical Issue #1: Wrong URL Configuration
**Problem**: Your `_config.yml` still points to the old Webflow URL:
```yaml
url: "https://diwu.webflow.io"
baseurl: ""
```

**Solution**: Update to your GitHub Pages URL. Replace `yourusername` with your actual GitHub username:
```yaml
url: "https://yourusername.github.io"
baseurl: "/XDLAB"  # Assuming your repo name is XDLAB
```

### 🚨 Critical Issue #2: Hard-coded Image Paths
**Problem**: Several images in `index.html` don't use relative URLs:
- `src="ERAU.jpg"`
- `src="diwu.jpeg"`
- `src="Rahi.jpeg"`
- `src="sriram.jpg"`

**Solution**: All images should use the `relative_url` filter.

### 🚨 Issue #3: Hard-coded Navigation Links
**Problem**: Some links use absolute paths that won't work with a baseurl:
- `href="/team"`
- `href="/research"`

## Step-by-Step Fix

### 1. Check GitHub Pages Build Status
1. Go to your GitHub repository
2. Click on **Actions** tab
3. Look for any failed builds (red X icons)
4. Click on a failed build to see error details

### 2. Check Your Live Site URL
Your GitHub Pages site should be at:
- `https://yourusername.github.io/XDLAB/` (if repo name is XDLAB)
- Replace `yourusername` with your actual GitHub username

### 3. Test Different URLs
If the main page doesn't load, try:
- `https://yourusername.github.io/XDLAB/` (with trailing slash)
- `https://yourusername.github.io/XDLAB/index.html`

### 4. Check Browser Developer Tools
1. Open your GitHub Pages site
2. Press F12 to open developer tools
3. Look at the **Console** tab for errors
4. Look at the **Network** tab to see failed requests (404 errors)

## Common Error Patterns

### CSS/JS Not Loading
**Symptoms**: Plain HTML with no styling
**Cause**: Wrong asset paths
**Check**: Look for 404 errors in Network tab for `/assets/css/main.css`

### Images Not Loading
**Symptoms**: Broken image icons
**Cause**: Wrong image paths
**Check**: Look for 404 errors in Network tab for image files

### Navigation Not Working
**Symptoms**: 404 errors when clicking links
**Cause**: Wrong baseurl configuration
**Check**: URLs in address bar when clicking links

### Blank Page
**Symptoms**: Completely blank page
**Cause**: JavaScript errors or missing layout
**Check**: Console tab for JavaScript errors

## Quick Diagnostic Commands

Run these locally to test your configuration:

```bash
# Test with GitHub Pages configuration
JEKYLL_ENV=production bundle exec jekyll serve --baseurl="/XDLAB"
```

Then visit: `http://localhost:4000/XDLAB/`

This simulates the GitHub Pages environment locally.

## Environmental Differences

### Local vs GitHub Pages
| Aspect | Local | GitHub Pages |
|--------|--------|--------------|
| baseurl | Usually empty `""` | Repository name `/XDLAB` |
| URL | `http://localhost:4000` | `https://user.github.io` |
| Plugins | All plugins work | Limited plugin support |
| Build | Immediate | Takes 1-2 minutes |

### Plugin Compatibility
GitHub Pages only supports [these plugins](https://pages.github.com/versions/). Your current plugins should work:
- ✅ `jekyll-feed` - Supported
- ❌ Any custom plugins - Not supported

## Next Steps

1. **First Priority**: Fix the URL configuration in `_config.yml`
2. **Second Priority**: Fix image paths in `index.html` 
3. **Third Priority**: Test the fixes locally with the production command above
4. **Fourth Priority**: Push changes and wait for GitHub Pages to rebuild

## Testing Checklist

After making changes, verify:
- [ ] Site loads at GitHub Pages URL
- [ ] CSS styling appears correctly
- [ ] Images load properly
- [ ] Navigation links work
- [ ] No 404 errors in browser console
- [ ] Mobile version works

## Still Having Issues?

If problems persist:
1. Check the GitHub Pages build logs in the Actions tab
2. Compare your local site (with baseurl) to the live site
3. Verify your repository name matches the baseurl
4. Check that all file names match exactly (case-sensitive on GitHub)