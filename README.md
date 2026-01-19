# Matti Hicks Portfolio Website

A clean, custom-built portfolio website to replace your Squarespace site. Built with semantic HTML and vanilla CSS for fast performance and easy maintenance.

## 🎨 Design Specifications

- **Background Color**: `#F2EFED` (beige)
- **Font**: GT-Walsheim (system font fallback currently active)
- **Max Width**: 1200px (overall layout), 800px (text content)
- **Aesthetic**: Minimal, clean, professional

## 📁 File Structure

```
/
├── index.html                    # Homepage
├── case-study-template.html      # Reusable template for projects
├── CNAME                         # Domain configuration for GitHub Pages
├── css/
│   └── styles.css               # All styles (organized with comments)
├── images/                       # Your portfolio images
├── fonts/                        # GT-Walsheim font files (when added)
└── case-studies/                # Individual case study pages
```

## 🚀 Quick Start

### 1. Add Your Content

**Homepage (`index.html`):**
- Update the hero title and intro paragraph
- Replace placeholder case study content (titles, descriptions, images)
- Update the About section text and photo
- Update social links in the footer

**Case Studies:**
- Duplicate `case-study-template.html` into the `case-studies/` folder
- Rename each file (e.g., `banking-redesign.html`)
- Update the content sections with your project details
- Add your images to the `images/` folder

### 2. Add Your Images

Place images in the `images/` folder:
- `profile-photo.jpg` - Your headshot for the About section
- `case-study-1.jpg` through `case-study-5.jpg` - Homepage thumbnails
- Project-specific images for each case study

**Image Optimization Tips:**
- Use WebP format when possible for smaller file sizes
- Compress images before uploading (try [TinyPNG](https://tinypng.com/) or [Squoosh](https://squoosh.app/))
- Recommended sizes:
  - Case study thumbnails: 800x600px
  - Profile photo: 400x400px
  - Content images: 1200px max width
  - Full-width images: 1600px max width

### 3. Add GT-Walsheim Font

1. Add your GT-Walsheim font files to the `fonts/` folder:
   - `GT-Walsheim-Regular.woff2`
   - `GT-Walsheim-Regular.woff`
   - `GT-Walsheim-Medium.woff2`
   - `GT-Walsheim-Medium.woff`
   - `GT-Walsheim-Bold.woff2`
   - `GT-Walsheim-Bold.woff`

2. Uncomment the `@font-face` declarations at the top of `css/styles.css` (lines 8-31)

## 🎨 Customizing Styles

All visual customization can be done via CSS custom properties in `css/styles.css` (lines 34-71):

```css
:root {
  /* Colors */
  --color-background: #F2EFED;
  --color-text-primary: #1a1a1a;
  /* ... and more */

  /* Spacing */
  --spacing-xs: 8px;
  --spacing-sm: 16px;
  /* ... and more */
}
```

Change these values to customize colors, spacing, fonts, etc. across the entire site.

## 📱 Responsive Design

The site is fully responsive with breakpoints at:
- **Desktop**: 1024px+
- **Tablet**: 768px - 1023px
- **Mobile**: < 768px

Test your site at different screen sizes to ensure it looks good everywhere.

## 🎨 Case Study Sections with Alternating Backgrounds

Case study pages feature alternating background colors for visual separation:
- **Odd sections** (1st, 3rd, 5th...): Beige background (`#F2EFED`)
- **Even sections** (2nd, 4th, 6th...): White background

Each `.content-section` automatically gets the appropriate background. The content inside each section is constrained to a readable width (800px max) while the background spans full-width.

## 🖼️ Image Layout Options

The case study template includes three image layout patterns:

### 1. Regular Content Image
```html
<figure class="content-image">
  <img src="../images/your-image.jpg" alt="Description">
  <figcaption class="image-caption">Optional caption text</figcaption>
</figure>
```

### 2. Full-Width Image (breaks out of text column)
```html
<figure class="content-image-full">
  <img src="../images/your-image.jpg" alt="Description">
</figure>
```

### 3. Side-by-Side Comparison
```html
<div class="image-comparison">
  <figure class="content-image">
    <img src="../images/before.jpg" alt="Before">
    <figcaption class="image-caption">Before</figcaption>
  </figure>
  <figure class="content-image">
    <img src="../images/after.jpg" alt="After">
    <figcaption class="image-caption">After</figcaption>
  </figure>
</div>
```

## 🌐 Deploying to GitHub Pages

### Initial Setup

1. **Create a GitHub repository:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Custom portfolio site"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
   git push -u origin main
   ```

2. **Enable GitHub Pages:**
   - Go to your repository on GitHub
   - Click **Settings** → **Pages**
   - Under "Source", select **main** branch
   - Click **Save**

3. **Configure custom domain:**
   - In the same Pages settings, enter `mattihicks.com` in the "Custom domain" field
   - Click **Save** (this will verify the CNAME file)

4. **Update DNS settings with your domain registrar:**
   - Add an **A record** pointing to GitHub's IPs:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - Add a **CNAME record**: `www` pointing to `YOUR-USERNAME.github.io`

5. **Wait for DNS propagation** (can take up to 24 hours, usually much faster)

6. **Enable HTTPS:**
   - Return to Settings → Pages
   - Check "Enforce HTTPS" (may need to wait for DNS to propagate first)

### Updating Your Site

Whenever you make changes:

```bash
git add .
git commit -m "Description of changes"
git push
```

GitHub Pages will automatically rebuild and deploy your site within a few minutes.

## ♿ Accessibility Features

The site includes several accessibility considerations:

- Semantic HTML5 elements (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`)
- Proper heading hierarchy (h1 → h2 → h3)
- Alt text on all images
- ARIA labels on icon-only links
- Focus-visible styles for keyboard navigation
- Prefers-reduced-motion support
- Screen reader-only text with `.sr-only` class

**To test accessibility:**
- Use keyboard navigation (Tab key) to ensure all interactive elements are accessible
- Test with a screen reader (VoiceOver on Mac, NVDA on Windows)
- Run [axe DevTools](https://www.deque.com/axe/devtools/) or [WAVE](https://wave.webaim.org/) browser extensions

## 🎯 Overview Boxes Explained

The three overview boxes on case study pages are designed to be **full-width** (edge-to-edge on the page). This is achieved with the following CSS pattern in `styles.css` (lines 293-303):

```css
.overview-section {
  width: 100vw;
  position: relative;
  left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
}
```

This "breaks out" of the constrained content width to span the full viewport. The boxes inside remain constrained to the max-width for readability.

## 💡 Tips & Best Practices

1. **Keep it simple**: Don't add frameworks or libraries unless absolutely necessary
2. **Optimize images**: Large images slow down your site and hurt SEO
3. **Test on mobile**: Most visitors will view your site on mobile devices
4. **Update regularly**: Keep your portfolio current with recent work
5. **Monitor performance**: Use [Google PageSpeed Insights](https://pagespeed.web.dev/) to check site speed

## 🐛 Troubleshooting

**Site not loading on custom domain:**
- Check DNS settings with your registrar
- Verify CNAME file contains only `mattihicks.com` (no http://, no www.)
- Wait for DNS propagation (up to 24-48 hours)

**Images not showing:**
- Check file paths (case-sensitive on GitHub Pages)
- Verify images are committed to the repository
- Use relative paths (e.g., `../images/photo.jpg` from case studies)

**Fonts not loading:**
- Verify font files are in the `fonts/` folder
- Ensure `@font-face` declarations are uncommented in CSS
- Check file paths in `@font-face` declarations

**Layout looks broken on mobile:**
- Test in browser DevTools responsive mode
- Check for any custom CSS you added that might override responsive styles
- Verify viewport meta tag is present in HTML

## 📊 Annual Savings

**Squarespace**: $185/year
**This site**: $0/year (GitHub Pages is free)
**Savings**: $185/year 🎉

## 📝 License

This is your personal portfolio site. Feel free to modify it however you like!

---

**Questions?** If you need help customizing the site or run into issues, refer to the detailed comments in `css/styles.css` or check GitHub Pages documentation.
