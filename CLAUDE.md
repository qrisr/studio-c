# CLAUDE.md - AI Assistant Guide for studio-c

## Project Overview

**studio-c** is a modern, single-page landing website for AI/KI workshops and consulting services. The site is designed to showcase AI workshop offerings and collect leads through a contact form.

### Key Information
- **Project Type**: Static HTML landing page
- **Language**: German (de)
- **Target Audience**: Businesses interested in AI workshops and consulting
- **Deployment**: GitHub Pages with automated GitHub Actions workflow
- **No Build Process**: Pure HTML/CSS/JS with no dependencies or build tools

---

## Repository Structure

```
studio-c/
├── index.html              # Main HTML file (contains all markup, CSS, and JS)
├── README.md               # Project documentation (German)
├── SETUP.md                # Web3Forms email setup guide (German)
├── CLAUDE.md               # This file - AI assistant guide
└── .github/
    └── workflows/
        ├── deploy.yml      # GitHub Pages deployment workflow
        └── static.yml      # Static content deployment workflow
```

### File Descriptions

#### index.html
- **Lines 1-792**: Complete HTML document with embedded CSS and JavaScript
- **Lines 10-791**: `<style>` section with all CSS (no external stylesheets)
- **Lines 1084-1182**: `<script>` section with vanilla JavaScript (no frameworks)
- **Self-contained**: All assets, styles, and scripts are embedded inline

#### README.md
- German-language project documentation
- Describes features, local testing, deployment setup, and customization

#### SETUP.md
- Step-by-step guide for configuring Web3Forms email integration
- Contains instructions for obtaining and adding the Web3Forms access key
- Target email: qris.riner@gmail.com

---

## Technology Stack

### Frontend
- **HTML5**: Semantic markup with accessibility features
- **CSS3**: Modern CSS with:
  - CSS custom properties (CSS variables) at `:root` (lines 17-34)
  - CSS Grid for layouts
  - Flexbox for component alignment
  - Gradient backgrounds and effects
  - Smooth animations and transitions
  - Mobile-first responsive design
- **JavaScript (ES6+)**: Vanilla JS for:
  - Scroll progress bar
  - Scroll reveal animations
  - 3D tilt effects on cards
  - Contact form submission (AJAX)
  - Smooth scrolling

### External Dependencies
- **Google Fonts**: Inter font family (loaded via CDN)
- **Web3Forms API**: Contact form submission service
  - Endpoint: `https://api.web3forms.com/submit`
  - Access key required (line 1032)

### No Build Tools
- No npm/package.json
- No webpack/vite/parcel
- No CSS preprocessors (Sass/Less)
- No JavaScript frameworks (React/Vue/Angular)
- No TypeScript

---

## Design System

### Color Palette (CSS Variables)
Located in `:root` (lines 17-34):

```css
--gradient-1: linear-gradient(135deg, #667eea 0%, #764ba2 100%); /* Purple */
--gradient-2: linear-gradient(135deg, #f093fb 0%, #f5576c 100%); /* Pink */
--gradient-3: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%); /* Blue */
--gradient-4: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%); /* Green */
--gradient-5: linear-gradient(135deg, #fa709a 0%, #fee140 100%); /* Orange */

--primary: #667eea;      /* Primary purple */
--secondary: #764ba2;    /* Secondary purple */
--accent: #43e97b;       /* Green accent */
--dark: #1a202c;         /* Dark background */
--light: #f7fafc;        /* Light background */
--white: #ffffff;        /* White */
--text: #2d3748;         /* Main text color */
--text-light: #718096;   /* Light text color */
```

### Typography
- **Font Family**: Inter (Google Fonts)
- **Font Weights**: 400, 500, 600, 700, 800, 900
- **Heading Sizes**: Responsive using `clamp()` for fluid typography
- **Body Line Height**: 1.7

### Component Patterns
1. **Hero Section** (lines 126-809): Full-screen intro with CTA
2. **Success Grid** (lines 811-861): 2×2 grid showing AI readiness phases
3. **Services Grid** (lines 863-980): 4 workshop cards
4. **Connection Table** (lines 982-1018): Relationship matrix
5. **Contact Form** (lines 1020-1075): Web3Forms integration
6. **Footer** (lines 1077-1082): Copyright info

---

## Key Features & Implementation

### 1. Scroll Progress Bar
- **Location**: Lines 48-60 (CSS), 1085-1091 (JS)
- **Purpose**: Visual indicator of scroll position at top of page
- **Implementation**: Transform scaleX based on scroll percentage

### 2. Floating Blob Background
- **Location**: Lines 68-124 (CSS)
- **Purpose**: Animated background decoration
- **Implementation**: Absolute-positioned gradients with blur filter
- **Animation**: 20-second infinite floating animation

### 3. Scroll Reveal Animations
- **Location**: Lines 756-766 (CSS), 1093-1109 (JS)
- **Purpose**: Fade-in elements as user scrolls
- **Class**: `.reveal` (applied to sections/cards)
- **Trigger**: Elements become visible 100px before viewport

### 4. 3D Card Tilt Effect
- **Location**: Lines 1122-1141 (JS)
- **Purpose**: Interactive card hover effect
- **Implementation**: Mouse position tracking with CSS transform
- **Applied to**: `.grid-card` and `.service-card` elements

### 5. Contact Form (Web3Forms)
- **Location**: Lines 1031-1073 (HTML), 1143-1181 (JS)
- **Method**: POST to `https://api.web3forms.com/submit`
- **AJAX**: Fetch API for async submission
- **Features**:
  - Loading state ("Wird gesendet...")
  - Success message display
  - Error handling
  - Form reset on success
  - Honeypot spam protection (botcheck field)

---

## Development Workflows

### Local Development
```bash
# Option 1: Python HTTP Server
python3 -m http.server 8000
# Then open: http://localhost:8000

# Option 2: Direct file opening
# Simply open index.html in a browser
```

### Making Changes
1. **Edit index.html directly** - no build step required
2. **Test locally** using a local server or by opening the file
3. **Commit changes** with descriptive message
4. **Push to designated branch** (see Git Workflow section)

### Testing Checklist
- [ ] Test on multiple browsers (Chrome, Firefox, Safari, Edge)
- [ ] Test responsive design (mobile, tablet, desktop)
- [ ] Verify all animations work smoothly
- [ ] Test contact form submission (requires valid Web3Forms key)
- [ ] Check scroll behavior and smooth scrolling
- [ ] Verify all internal links work (#contact, #services, etc.)

---

## Git Workflow & Branching

### Branch Naming Convention
- **Claude branches**: Must start with `claude/` and end with session ID
- **Current branch**: `claude/claude-md-mithg6ituzk9oapy-01E3teqmwWdRQn6Mn7nvucqw`
- **Format**: `claude/<descriptive-name>-<session-id>`

### Git Commands
```bash
# Check current branch
git branch --show-current

# Create and checkout new branch
git checkout -b claude/<name>-<session-id>

# Stage all changes
git add .

# Commit with message
git commit -m "Description of changes"

# Push to remote (use -u for first push)
git push -u origin <branch-name>
```

### Deployment Workflow
- **Trigger**: Push to specific branch (configured in workflows)
- **Action**: GitHub Actions automatically deploys to GitHub Pages
- **Workflows**:
  - `deploy.yml`: Branch-specific deployment
  - `static.yml`: Static content deployment with manual trigger option
- **URL Pattern**: `https://<username>.github.io/studio-c/`

### Important Git Notes
- **Never force push** to main/master
- **Always use descriptive commit messages** in German or English
- **Test locally before pushing** to avoid breaking production
- **Push with retry logic** if network errors occur (up to 4 retries with exponential backoff)

---

## Content Structure

### Page Sections (in order)
1. **Hero** (#hero): Main headline and CTA button
2. **Success Grid** (#grid): 2×2 matrix of AI readiness phases
3. **Services** (#services): 4 workshop offerings
4. **Connection Table**: Maps workshops to success framework
5. **Contact Form** (#contact): Lead capture with Web3Forms
6. **Footer**: Copyright and legal

### Workshop Offerings
1. **Workshop A**: KI im digitalen Marketing (AI in Digital Marketing)
2. **Workshop B**: Web-/Front-Coding mit KI (Web/Frontend Coding with AI)
3. **Workshop C**: Chatbots & Automatisierung (Chatbots & Automation)
4. **Workshop D**: Context Engineering & Custom GPTs

### Success Grid Phases
1. **Phase 1** (Bottom-left): Experimentierphase - Neither tech nor people ready
2. **Phase 2** (Top-left): Motivation ohne Mittel - People ready, tech not ready
3. **Phase 3** (Bottom-right): Technologie-Push - Tech ready, people not ready
4. **Phase 4** (Top-right): ✓ Skalierbares Wachstum - Both ready (goal state)

---

## Code Conventions & Best Practices

### HTML
- Use semantic HTML5 elements (`<section>`, `<header>`, `<footer>`)
- Include ARIA labels where appropriate
- Keep all markup in single index.html file
- Use kebab-case for IDs and classes
- Maintain proper indentation (4 spaces)

### CSS
- **Organization**: Follow existing order:
  1. Reset/base styles
  2. CSS variables
  3. Layout components
  4. UI components
  5. Animations
  6. Media queries
- **Naming**: Use descriptive class names (e.g., `.service-card`, `.grid-icon`)
- **Responsive**: Mobile-first approach with min-width media queries
- **Performance**: Use `will-change` sparingly, prefer transform/opacity for animations

### JavaScript
- Use modern ES6+ syntax (const/let, arrow functions, async/await)
- No jQuery or frameworks - vanilla JS only
- Keep all scripts at bottom of body
- Use event delegation where appropriate
- Comment complex logic
- Avoid global namespace pollution

### Performance Considerations
- **Images**: Currently no images; if adding, use modern formats (WebP, AVIF)
- **Fonts**: Preconnect to Google Fonts for faster loading
- **CSS**: Consider critical CSS for above-the-fold content
- **JS**: Scripts at bottom; use defer/async if needed
- **Animations**: Use transform/opacity for GPU acceleration

---

## Common Tasks & How-To Guide

### Change Colors/Branding
1. Locate `:root` CSS variables (lines 17-34)
2. Update gradient and color values
3. Changes propagate automatically throughout site

### Add New Workshop/Service
1. Locate `.service-grid` (line 871)
2. Copy existing `.service-card` structure
3. Update content, icon, and gradient
4. Ensure card has `.reveal` class for scroll animation
5. Update connection table if needed

### Modify Contact Form
1. Form markup: lines 1031-1073
2. Form handler: lines 1143-1181
3. To add field:
   - Add form-group in HTML
   - Web3Forms automatically includes all fields in email
4. To change recipient: Update email in Web3Forms dashboard

### Update Web3Forms Access Key
1. Get key from https://web3forms.com
2. Replace `YOUR_ACCESS_KEY_HERE` at line 1032
3. Key should be kept private (but not a security risk if exposed)

### Add New Section
1. Create `<section>` with unique ID
2. Add `.reveal` class for scroll animation
3. Include `.container` for max-width constraint
4. Follow existing section pattern:
   ```html
   <section id="new-section">
     <div class="container">
       <div class="section-header reveal">
         <h2 class="section-title">Title</h2>
         <p class="section-subtitle">Subtitle</p>
       </div>
       <!-- Content here -->
     </div>
   </section>
   ```

### Adjust Responsive Breakpoints
1. Main breakpoint at 768px (line 769)
2. Uses mobile-first approach
3. Add additional breakpoints as needed:
   ```css
   @media (max-width: 1024px) { /* Tablet */ }
   @media (max-width: 768px) { /* Mobile */ }
   @media (max-width: 480px) { /* Small mobile */ }
   ```

---

## Important Constraints & Limitations

### What NOT to Do
1. ❌ **Don't add build tools** - Keep project dependency-free
2. ❌ **Don't split into multiple HTML files** - Maintain single-page structure
3. ❌ **Don't add external JS/CSS files** - Keep everything inline
4. ❌ **Don't use frameworks** - Pure vanilla JS only
5. ❌ **Don't commit sensitive data** - Web3Forms key is in HTML but not a secret
6. ❌ **Don't force push to main** - Protected branch
7. ❌ **Don't remove accessibility features** - Maintain semantic HTML

### Technical Limitations
- No server-side code (static hosting)
- No database (form submissions via Web3Forms)
- No user authentication/sessions
- No dynamic routing (single page)
- Limited to 250 form submissions/month (Web3Forms free tier)

---

## Troubleshooting

### Contact Form Not Working
1. **Check access key**: Verify Web3Forms key at line 1032
2. **Check console**: Open browser DevTools for errors
3. **Test API**: Form submission logs to console
4. **Verify email**: Ensure Web3Forms account is confirmed
5. **Check CORS**: Web3Forms API allows cross-origin requests

### Animations Not Smooth
1. **Check GPU acceleration**: Ensure using transform/opacity
2. **Reduce blur**: Lower blur values on blobs for better performance
3. **Disable on mobile**: Add media query to disable heavy animations
4. **Check browser**: Test in different browsers

### Layout Broken on Mobile
1. **Check viewport meta tag**: Ensure present in `<head>` (line 5)
2. **Test responsive breakpoint**: Verify @media query at line 769
3. **Check overflow**: Ensure `overflow-x: hidden` on body
4. **Test on real device**: Emulators may not match real behavior

### Deployment Not Working
1. **Check workflow file**: Verify correct branch name in `.github/workflows/`
2. **Check Pages settings**: GitHub repo → Settings → Pages
3. **Verify permissions**: Ensure workflow has pages write permission
4. **Check Actions tab**: View deployment logs in GitHub Actions

---

## AI Assistant Guidelines

### When Working on This Project

#### Do:
- ✅ **Read context first**: Review relevant sections of this file before making changes
- ✅ **Test locally**: Verify changes work before committing
- ✅ **Maintain patterns**: Follow existing code structure and conventions
- ✅ **Preserve inline style**: Keep CSS and JS embedded in HTML
- ✅ **Use descriptive commits**: Write clear commit messages
- ✅ **Consider responsiveness**: Test changes on multiple screen sizes
- ✅ **Respect German content**: Keep existing German text unless instructed otherwise
- ✅ **Document changes**: Update this CLAUDE.md if adding new patterns

#### Don't:
- ❌ **Don't refactor unnecessarily**: Avoid over-engineering simple changes
- ❌ **Don't add dependencies**: Keep project dependency-free
- ❌ **Don't split files**: Maintain single-file structure
- ❌ **Don't remove features**: Preserve existing animations and interactions
- ❌ **Don't change architecture**: No frameworks or build tools
- ❌ **Don't assume context**: Read the code before suggesting changes

### Communication Style
- **Be concise**: User sees output on CLI
- **Avoid emojis**: Unless explicitly requested
- **Be direct**: No unnecessary validation or praise
- **Prioritize accuracy**: Facts over assumptions
- **Ask when unclear**: Don't guess requirements

### Before Making Changes
1. Read the relevant section of index.html
2. Understand the existing implementation
3. Consider responsive impact
4. Test locally if possible
5. Document reasoning for significant changes

### Code Review Checklist
- [ ] Follows existing code style
- [ ] Maintains inline CSS/JS pattern
- [ ] Works on mobile and desktop
- [ ] No console errors
- [ ] Animations perform well
- [ ] Semantic HTML maintained
- [ ] Accessibility not degraded

---

## Recent Changes & History

### Commit History (Most Recent First)
1. **6816a2c** - Ultra-Premium Design: Die fanciest Version
2. **db29b9e** - Add Web3Forms E-Mail Integration
3. **9408b0c** - Premium UX/UI Design Update
4. **768d7dc** - Add GitHub Actions workflow for static site deployment
5. **66162ac** - GitHub Pages Deployment Setup
6. **694e234** - Erstelle AI/KI Workshop Landing Page

### Evolution
- Started as basic landing page
- Enhanced with premium UI/UX design
- Added Web3Forms integration for contact form
- Implemented GitHub Pages deployment
- Refined to "ultra-premium" design with advanced animations

---

## Contact & Support

### Project Owner
- **Email**: qris.riner@gmail.com (as specified in SETUP.md)
- **Use Case**: AI/KI Workshop landing page and lead generation

### For AI Assistants
- **Reference this file**: When uncertain about project structure or conventions
- **Update this file**: When adding new patterns or significant features
- **Ask questions**: If requirements are unclear or ambiguous

---

## Quick Reference

### File Locations
- Main HTML: `/index.html` (lines 1-1185)
- CSS Variables: `/index.html` (lines 17-34)
- Hero Section: `/index.html` (lines 126-809)
- Services Grid: `/index.html` (lines 863-980)
- Contact Form: `/index.html` (lines 1031-1073)
- JavaScript: `/index.html` (lines 1084-1182)

### External URLs
- Web3Forms API: `https://api.web3forms.com/submit`
- Google Fonts: `https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900`
- Web3Forms Setup: `https://web3forms.com`

### Color Shortcuts
- Primary Purple: `#667eea` / `var(--primary)`
- Accent Green: `#43e97b` / `var(--accent)`
- Dark Background: `#1a202c` / `var(--dark)`
- White: `#ffffff` / `var(--white)`

---

**Last Updated**: 2025-12-05
**Version**: 1.0
**Maintained By**: AI Assistants working on studio-c
