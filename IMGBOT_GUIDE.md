# ImgBot Troubleshooting Guide

## Quick Check: Is ImgBot Working?

If you're wondering "How do I know if ImgBot is working?", here's a step-by-step guide:

### ✅ Step 1: Verify ImgBot Installation

1. Go to your GitHub repository
2. Click **Settings** (repository settings, not your profile)
3. In the left sidebar, click **Integrations & services** or **GitHub Apps**
4. Look for "ImgBot" in the installed apps list

**If ImgBot is NOT listed:**
- Visit [imgbot.net](https://imgbot.net/)
- Click "Install on GitHub"
- Select your repository and complete installation

### ✅ Step 2: Check Your Images

ImgBot analyzes these file types:
- ✅ JPG/JPEG files (like your profile pictures)
- ✅ PNG files (like your logo)
- ✅ GIF files
- ✅ SVG files  
- ✅ WebP files
- ❌ AVIF files (excluded in this repo's config - already highly optimized)

**In this repository:**
- `profile-picture/*.jpg` files (~8-20KB each) - **Candidates for optimization**
- `resources/logo-removebg-preview.png` (~92KB) - **Good candidate for optimization**
- `Thumbnail/*.avif` files - **Excluded** (already optimized format)

### ✅ Step 3: Understanding ImgBot Behavior

**ImgBot will create a PR when:**
- It finds images that can be reduced by ≥10KB total (configured in `.imgbotconfig`)
- New unoptimized images are added to the repository
- It runs on its schedule (daily, as configured)

**ImgBot will NOT create a PR when:**
- Total savings are less than 10KB
- Images are already well-optimized
- File types are in the ignored list (like AVIF files here)

### ✅ Step 4: Force ImgBot to Run

If ImgBot is installed but you haven't seen activity:

1. **Add a new unoptimized image:**
   - Take a screenshot or photo
   - Save as PNG or JPG (make it larger than 50KB)
   - Commit and push to your repository

2. **Wait for ImgBot:**
   - ImgBot runs daily
   - May take 24-48 hours to process new images
   - Will create a PR if significant savings are found

### ✅ Step 5: Manual Testing

To test if your current images can be optimized:

1. Download `resources/logo-removebg-preview.png` (92KB)
2. Upload to [TinyPNG.com](https://tinypng.com/)
3. If it reduces the file by >10KB, ImgBot should eventually optimize it

### 🔧 Current Configuration

This repository's `.imgbotconfig` settings:
```json
{
    "schedule": "daily",           // Runs once per day
    "minKBReduced": 10,           // Only creates PR if ≥10KB saved
    "ignoredFiles": ["*.avif"],   // Skips AVIF files
    "aggressiveCompression": false // Uses standard compression
}
```

### 🚨 Common Issues

**"I installed ImgBot but no PRs appeared"**
- Your images might already be optimized
- Total potential savings might be <10KB
- Try adding a large, unoptimized image to test

**"ImgBot created a PR but images look worse"**
- Review the PR carefully
- ImgBot preserves visual quality while reducing file size
- You can always decline the PR if unsatisfied

**"ImgBot is optimizing files I don't want changed"**
- Add file patterns to `ignoredFiles` in `.imgbotconfig`
- Examples: `["docs/*", "*.gif", "logo.png"]`

### 📞 Need Help?

- [ImgBot Documentation](https://imgbot.net/docs)
- [ImgBot GitHub Repository](https://github.com/dabutvin/Imgbot)
- Create an issue in the ImgBot repository for technical problems