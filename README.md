# BioInterpreter AI - Landing Page

A modern, animated landing page showcasing BioInterpreter AI with dynamic cellular visualization and knowledge extraction effects.

## 🎯 Project Overview

This is a single-file HTML landing page featuring a 3D biological cell that gets progressively illuminated by a scanning light beam, symbolizing the AI-powered decoding of biological information into actionable knowledge.

## 🏗️ Architecture

### Single-File Design
The entire project is contained in a **single `index.html` file** with no external dependencies. This architecture provides:

- **Simplicity**: No build process, bundlers, or package managers required
- **Portability**: Easy to deploy anywhere (static hosting, CDN, local file system)
- **Performance**: Zero HTTP requests for external resources
- **Maintainability**: All code in one place for easy updates

### File Structure

```
/Users/davidjm/temp/bia/
├── index.html          # Complete landing page (HTML + CSS + JavaScript)
└── README.md           # This file
```

### `index.html` Components

The file is organized into three main sections:

#### 1. **HTML Structure** (`<body>`)
```
├── Stars background (animated)
├── Main content (3-column grid)
│   ├── Left: Title section
│   │   ├── "BioInterpreter AI" (animated gradient)
│   │   └── Tagline
│   ├── Center: Cell visualization
│   │   ├── Dark silhouette cell (SVG)
│   │   ├── Illuminated cell (SVG with organelles)
│   │   └── Light beam (animated)
│   └── Right: Knowledge text boxes
│       └── Dynamic biological descriptions
└── Footer
    ├── Brand name
    ├── Tagline
    └── Copyright
```

#### 2. **CSS Styles** (`<style>`)

**Layout System:**
- CSS Grid for 3-column responsive layout
- Flexbox for component alignment
- `clamp()` for responsive typography

**Animations:**
- `gradientShift`: Animated gold-to-cyan gradient on title (3s loop)
- `fadeInUp`: Title entrance animation (1.5s on load)
- `twinkle`: Star background twinkling (3s loop, randomized)
- `revealCell`: Cell illumination synchronized with light beam (9.5s loop)
- `sweepLightVertical`: Light beam scanning motion (9.5s loop)
- `appearBox`: Knowledge text box fade-in/out (1.5s per box)

**Visual Effects:**
- SVG gradients for cellular components
- Drop shadows and glows
- Blur filters for light beam
- Clip-path for progressive cell reveal

#### 3. **JavaScript** (`<script>`)

**Dynamic Content Generation:**

1. **`createStars()`**
   - Generates 150 randomized stars
   - Random size (1-3px), position, animation delay, and duration
   - Creates depth and atmosphere

2. **`createKnowledgeText()`**
   - Creates 6 fixed-position text boxes (80px spacing, 70px height)
   - Manages two animation sequences:
     - **Down scan**: Boxes 1→6 appear sequentially (0.6s start, 200ms intervals)
     - **Up scan**: Boxes 6→1 appear sequentially (3.8s start, 200ms intervals)
   - Rotates through 10 biological process descriptions
   - Repeats every 9.5 seconds

3. **Mouse parallax effect**
   - Subtle cell movement following cursor (±10px)
   - Only active on desktop (>1200px width)

## ⏱️ Animation Timeline (9.5 second cycle)

```
0.0s - 0.3s:  Ready state (everything hidden)
0.3s - 1.8s:  DOWN SCAN
              - Light beam scans top→bottom
              - Cell progressively illuminates from top
              - Text boxes appear sequentially (top→bottom)
1.8s - 3.3s:  PAUSE (1.5 seconds)
              - Cell stays fully illuminated
              - Light beam off-screen
3.3s - 3.6s:  Transition (cell returns to dark)
3.6s - 3.8s:  Repositioning
3.8s - 5.0s:  UP SCAN
              - Light beam scans bottom→top
              - Cell progressively illuminates from bottom
              - Text boxes appear sequentially (bottom→top)
5.0s - 5.3s:  Fade out (cell returns to dark)
5.3s - 9.5s:  REST (2 seconds)
              - Everything dark before next cycle
```

## 🎨 Design System

### Color Palette
- **Background**: `#0a0e27` (dark space blue)
- **Cell silhouette**: `#000000` (pure black for contrast)
- **Primary accent**: `#FFD700` (gold) → `#00FFFF` (cyan) gradient
- **Text**: `#64c8ff` (cyan blue) with glow effects
- **Secondary text**: `#b8c5d6` (light blue-gray)

### Typography
- **System fonts**: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto
- **Title**: 2-3.5rem, animated gradient
- **Tagline**: 0.9-1.1rem
- **Knowledge boxes**: 0.75rem monospace (Courier New)

### Responsive Breakpoints
- **Desktop**: 3-column layout (>1200px)
- **Tablet/Mobile**: Stacked layout (<1200px)
- **Small screens**: Reduced font sizes via `clamp()`

## 🚀 Deployment

### Local Development
Simply open `index.html` in any modern browser:
```bash
open index.html
# or
python -m http.server 8000  # Then visit http://localhost:8000
```

### Production Deployment

**Option 1: Static Hosting**
Upload `index.html` to any static host:
- GitHub Pages
- Netlify
- Vercel
- AWS S3 + CloudFront
- Cloudflare Pages

**Option 2: CDN**
```bash
# Example: Deploy to Netlify
netlify deploy --prod --dir=.
```

**Option 3: Docker**
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/
```

## 🔧 Customization

### Modify Animation Speed
Change the animation duration in CSS:
```css
animation: revealCell 9.5s ease-in-out infinite;  /* Change 9.5s */
animation: sweepLightVertical 9.5s ease-in-out infinite;  /* Match above */
```

And in JavaScript:
```javascript
setInterval(() => { /* ... */ }, 9500);  /* Match duration in ms */
```

### Add More Knowledge Items
Edit the `knowledgeItems` array in JavaScript:
```javascript
const knowledgeItems = [
    'Your new biological process description here',
    // ... add more
];
```

### Adjust Pause Duration
Modify the timeline percentages in `@keyframes revealCell` and `@keyframes sweepLightVertical`.

### Change Colors
Update color values in the CSS:
- Title gradient: `linear-gradient(45deg, #FFD700, #00FFFF, #FFD700)`
- Knowledge box color: `color: #64c8ff`
- Background: `background: #0a0e27`

## 📱 Browser Compatibility

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

**Features used:**
- CSS Grid
- CSS clip-path
- CSS custom properties
- SVG with gradients
- ES6 JavaScript (arrow functions, template literals)

## ♿ Accessibility

- **Reduced motion**: Animation disabled when user prefers reduced motion
- **Semantic HTML**: Proper header, main, footer structure
- **Alt text**: SVG elements are decorative (presentation role implicit)
- **Keyboard navigation**: No interactive elements requiring focus management

## 📄 License

© biodavidjm

---

**Built with vanilla HTML, CSS, and JavaScript - no frameworks, no dependencies, no build step.**
