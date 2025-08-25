# YouTube Clone - HTML & CSS

A simple YouTube clone built with HTML and CSS, featuring a responsive design and clean layout.

## 🖼️ Image Optimization with ImgBot

This repository is configured to work with [ImgBot](https://imgbot.net/) for automatic image optimization.

### How to Know if ImgBot is Working

ImgBot will automatically optimize images in your repository when:

1. **ImgBot is installed**: Go to [imgbot.net](https://imgbot.net/) and install the GitHub App on your repository
2. **New images are added**: ImgBot scans for unoptimized images after installation
3. **Images can be optimized**: ImgBot will only create PRs if it can reduce file sizes significantly

### Expected Behavior

- **Pull Requests**: ImgBot creates PRs with optimized images when it finds savings ≥ 10KB (configured in `.imgbotconfig`)
- **Schedule**: ImgBot runs daily to check for new images (configured in `.imgbotconfig`)
- **File Types**: Optimizes JPG, PNG, GIF, SVG, and WebP files (AVIF files are excluded as they're already highly optimized)

### Why You Might Not See a Pull Request

1. **ImgBot not installed**: Check if the ImgBot app is installed in your repository settings
2. **Images already optimized**: Your images may already be well-optimized
3. **Savings too small**: ImgBot only creates PRs when savings ≥ 10KB
4. **Recent installation**: ImgBot may take time to scan existing images

### ImgBot Configuration

This repository includes a `.imgbotconfig` file with the following settings:

```json
{
    "schedule": "daily",
    "compressWiki": false,
    "minKBReduced": 10,
    "ignoredFiles": ["*.avif"],
    "aggressiveCompression": false
}
```

### Verifying ImgBot Installation

1. Go to your repository on GitHub
2. Click **Settings** → **Integrations & services** → **GitHub Apps**
3. Look for "ImgBot" in the list of installed apps
4. If not present, install ImgBot from [imgbot.net](https://imgbot.net/)

### Manual Verification

To check if your images can be optimized:

1. Use online tools like [TinyPNG](https://tinypng.com/) or [ImageOptim](https://imageoptim.com/)
2. Upload a few of your JPG/PNG files to see potential savings
3. If significant savings are possible, ImgBot should create a PR

## 📁 Project Structure

```
├── index.html                 # Main HTML file
├── css_for_youtube/          # CSS files
│   ├── general.css           # General styles
│   ├── header.css            # Header styles
│   └── video.css             # Video grid styles
├── Thumbnail/                # Video thumbnail images
├── profile-picture/          # Channel profile pictures
├── resources/                # Other assets (logos, etc.)
└── .imgbotconfig            # ImgBot configuration
```

## 🚀 Getting Started

1. Clone the repository
2. Open `index.html` in your browser
3. The page should display a YouTube-like interface

## 🔧 Development

This is a static HTML/CSS project with no build process required. Simply edit the files and refresh your browser to see changes.

## 📝 Notes

- The project uses modern CSS Grid and Flexbox for layout
- Images are optimized for web display
- AVIF format is used for thumbnails (modern, highly compressed format)
- JPG format is used for profile pictures (good balance of quality and size)