# Setup Guide - Vue 3 Portfolio

This guide will help you set up and customize your Vue 3 portfolio website.

## Quick Start

1. **Navigate to the project directory:**
   ```bash
   cd vue
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start development server:**
   ```bash
   npm run dev
   ```

4. **Open your browser:**
   Navigate to `http://localhost:5173`

## Understanding Tailwind CSS v4

This project uses Tailwind CSS v4, which has some differences from v3:

### Key Changes in Tailwind v4:

1. **No more tailwind.config.js** - Configuration is now done in CSS using `@theme` directive
2. **CSS-first configuration** - Theme tokens are defined directly in your CSS file
3. **Import syntax** - Use `@import "tailwindcss"` instead of separate directives

### Color System

The project uses CSS custom properties for theming. Colors are defined in `src/assets/styles/main.css`:

```css
:root {
  --primary: #030213;
  --background: #ffffff;
  /* ... more colors */
}

.dark {
  --primary: oklch(0.985 0 0);
  --background: oklch(0.145 0 0);
  /* ... more colors */
}
```

To use these colors in your components:
```html
<div class="bg-primary text-primary-foreground">Content</div>
```

## Customization Guide

### 1. Personal Information

Update the following components with your information:

**Hero.vue** - Line 47-67:
```vue
<h1>
  <span>YOUR</span>
  <span>NAME</span>
</h1>
```

**About.vue** - Update stats, bio, and values

**Contact.vue** - Update contact information and social links

### 2. Projects

Edit `Projects.vue` to add your projects:

```javascript
const projects = [
  {
    id: 1,
    title: "Your Project Name",
    description: "Project description",
    image: "https://your-image-url.com/image.jpg",
    technologies: ["Vue.js", "Node.js"],
    liveUrl: "https://your-live-site.com",
    githubUrl: "https://github.com/username/repo"
  }
]
```

### 3. Skills

Customize your skills in `Skills.vue`:

```javascript
const skillCategories = {
  frontend: {
    title: "Frontend Development",
    skills: [
      { name: "Vue.js", experience: "4+ years", level: "Expert", icon: "💚" }
    ]
  }
}
```

### 4. Experience

Update your work history in `Experience.vue`:

```javascript
const experiences = [
  {
    title: "Your Job Title",
    company: "Company Name",
    period: "2020 - Present",
    description: "What you did...",
    technologies: ["Tech1", "Tech2"]
  }
]
```

### 5. Theme Colors

To change the color scheme, edit `src/assets/styles/main.css`:

```css
:root {
  --primary: #your-color;        /* Main brand color */
  --secondary: #your-color;      /* Secondary color */
  --accent: #your-color;         /* Accent color */
  /* Add more custom colors */
}
```

Available color utilities:
- `bg-primary` - Primary background
- `text-primary` - Primary text color
- `border-primary` - Primary border
- Similar for: secondary, accent, muted, card, etc.

### 6. Fonts

To change fonts, update the CSS in `main.css`:

```css
body {
  font-family: 'Your Font', -apple-system, BlinkMacSystemFont, sans-serif;
}
```

Don't forget to import the font in `index.html`:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Your+Font&display=swap" rel="stylesheet">
```

## Component Guide

### Theme System

The theme is managed in `App.vue` using VueUse's `useStorage`:

```javascript
const theme = useStorage('portfolio-theme', 'system')
```

Theme options:
- `light` - Light mode
- `dark` - Dark mode
- `system` - Follow system preference

### Animations

Animations are powered by `@vueuse/motion`:

```vue
<div
  v-motion
  :initial="{ opacity: 0, y: 50 }"
  :visible-once="{ opacity: 1, y: 0, transition: { duration: 800 } }"
>
  Content
</div>
```

Animation presets:
- `initial` - Starting state
- `enter` - On mount
- `visible-once` - When element enters viewport (once)
- `hovered` - On hover

### Custom Cursor

The custom cursor automatically detects interactive elements:
- Buttons and links - Larger cursor
- Input fields - Medium cursor
- Headings - Extra large cursor

Disable on mobile automatically (< 768px width)

### Keyboard Shortcuts

Users can press `?` to see all available shortcuts. Add new shortcuts in `KeyboardShortcuts.vue`:

```javascript
switch (e.key.toLowerCase()) {
  case 'x':
    e.preventDefault()
    // Your action
    break
}
```

## Deployment

### Build for Production

```bash
npm run build
```

This creates a `dist` folder with optimized files.

### Deploy to Netlify

1. Connect your GitHub repository to Netlify
2. Set build command: `npm run build`
3. Set publish directory: `dist`
4. Deploy!

### Deploy to Vercel

```bash
npm install -g vercel
vercel
```

### Deploy to GitHub Pages

1. Install gh-pages:
```bash
npm install --save-dev gh-pages
```

2. Add to package.json:
```json
{
  "scripts": {
    "deploy": "npm run build && gh-pages -d dist"
  }
}
```

3. Run:
```bash
npm run deploy
```

## Performance Tips

1. **Optimize Images**
   - Use WebP format
   - Compress images before uploading
   - Use lazy loading for below-fold images

2. **Code Splitting**
   - Vue Router automatically code-splits routes
   - Use dynamic imports for large components

3. **Lighthouse Score**
   - Run `npm run build` and test with Lighthouse
   - Aim for 90+ in all categories

## Troubleshooting

### Tailwind styles not working

Make sure `@import "tailwindcss"` is at the top of your `main.css`

### Dark mode not working

Check that your root element has the theme class:
```vue
<div :class="{ 'dark': isDark }">
```

### Animations not showing

Ensure `@vueuse/motion` is installed:
```bash
npm install @vueuse/motion
```

And plugin is registered in `main.js`:
```javascript
import { MotionPlugin } from '@vueuse/motion'
app.use(MotionPlugin)
```

## Advanced Customization

### Add a New Section

1. Create a new component in `src/components/`
2. Import it in `src/views/Home.vue`
3. Add it to the template
4. Add navigation link in `Header.vue`

Example:
```vue
<!-- src/components/NewSection.vue -->
<template>
  <section id="new-section" class="py-32 px-4">
    <div class="max-w-7xl mx-auto">
      <h2>New Section</h2>
    </div>
  </section>
</template>
```

### Custom Utilities

Add custom Tailwind utilities in `main.css`:

```css
@layer utilities {
  .text-gradient {
    @apply bg-clip-text text-transparent bg-gradient-to-r from-primary to-chart-1;
  }
}
```

Use in components:
```html
<h1 class="text-gradient">Gradient Text</h1>
```

## Resources

- [Vue 3 Documentation](https://vuejs.org/)
- [Tailwind CSS v4 Docs](https://tailwindcss.com/)
- [VueUse Motion](https://motion.vueuse.org/)
- [Vue Router](https://router.vuejs.org/)

## Support

If you need help:
1. Check the Vue 3 and Tailwind documentation
2. Review the component source code
3. Search for similar issues online

Happy coding! 🚀
