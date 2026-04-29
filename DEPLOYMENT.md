# GitHub Pages Deployment Guide

## 🚀 Quick Deploy

### Option 1: Automatic GitHub Actions (Recommended)

Our repository includes an automated GitHub Actions workflow. When you push to `main`:

1. Code is automatically built
2. Tests run
3. Deployed to GitHub Pages
4. Available at: https://LCDR-WOMBAT.github.io/mapbox-gl-styles/

**No manual action needed!** Just commit and push.

```bash
git add .
git commit -m "Update defense mission app"
git push origin main
```

### Option 2: Manual Deployment

```bash
# Install dependencies
npm install

# Build for production
npm run build

# Deploy to GitHub Pages
npm run deploy
```

This uses `gh-pages` package to automatically push `dist/` to `gh-pages` branch.

## ✅ Verify Deployment

1. Go to: https://LCDR-WOMBAT.github.io/mapbox-gl-styles/
2. Open browser console (F12)
3. Check for errors
4. Test map interactions

## 🔧 Repository Settings

Ensure these GitHub settings are correct:

1. **Settings > Pages**
   - Source: Deploy from branch
   - Branch: `gh-pages`
   - Folder: `/ (root)`

2. **Settings > Actions**
   - Allow all actions and reusable workflows

3. **Actions > General**
   - Workflow permissions: Read and write

## 📊 CI/CD Pipeline Status

Check workflow status at:
```
https://github.com/LCDR-WOMBAT/mapbox-gl-styles/actions
```

## 🛠️ Troubleshooting

### Build fails
```bash
# Clear cache and rebuild
rm -rf node_modules dist
npm install
npm run build
```

### Page not updating
- Clear browser cache (Ctrl+Shift+Delete)
- Wait 5-10 minutes for GitHub Pages to refresh
- Check Actions tab for build errors

### Deployment not triggering
```bash
# Check workflow file exists
ls -la .github/workflows/deploy.yml

# Push an empty commit to trigger
git commit --allow-empty -m "Trigger deployment"
git push
```

## 🌍 Custom Domain

To use a custom domain:

1. Update `homepage` in `package.json`:
```json
"homepage": "https://yourdomain.com/"
```

2. Create `CNAME` file:
```
yourdomain.com
```

3. Add to repository root and commit

4. Configure DNS records to point to GitHub Pages

## 📦 Alternative Hosting

### Netlify
```bash
npm run build
netlify deploy --prod --dir=dist
```

### Vercel
```bash
npm run build
vercel --prod
```

### AWS S3
```bash
npm run build
aws s3 sync dist/ s3://your-bucket-name/
```

## 🔐 Environment Variables

For Mapbox token:

1. Generate token at: https://account.mapbox.com/tokens/
2. In app settings modal, paste token
3. Token stored locally in browser

**Never commit tokens to GitHub!**

## 📝 Files Deployed

When you push, these files go to production:

```
dist/
├── index.html          # Main page
├── js/
│   └── app.*.js       # Bundled JavaScript
├── css/
│   └── main.*.css     # Bundled CSS
├── sw.js              # Service Worker
└── manifest.json      # PWA Manifest
```

Filenames include content hashes for cache busting.

## 🎯 Next Steps

1. ✅ Repository forked/cloned
2. ✅ GitHub Actions configured
3. ✅ Deployed to GitHub Pages
4. ✅ Update Mapbox token in settings
5. ✅ Start using!

## 💬 Need Help?

- Check GitHub Actions logs
- Review `.github/workflows/deploy.yml`
- Open an issue on GitHub

---

**Your app is live!** 🎉
