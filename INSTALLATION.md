# Installation Instructions

## Prerequisites

Before you begin, ensure you have the following installed:
- **Node.js** (version 16 or higher)
- **npm** (comes with Node.js) or **yarn**

Check your versions:
```bash
node --version  # Should be 16.x or higher
npm --version   # Should be 7.x or higher
```

## Step-by-Step Installation

### 1. Navigate to Project Directory

```bash
cd vue
```

### 2. Install Dependencies

Using npm:
```bash
npm install
```

Or using yarn:
```bash
yarn install
```

This will install:
- Vue 3
- Vue Router
- VueUse (Core & Motion)
- Tailwind CSS v4
- Vite
- Other required dependencies

### 3. Start Development Server

Using npm:
```bash
npm run dev
```

Or using yarn:
```bash
yarn dev
```

The application will start at `http://localhost:5173`

### 4. Open in Browser

Open your browser and navigate to:
```
http://localhost:5173
```

You should see the portfolio website running!

## Verify Installation

Check that everything is working:
- ✅ Page loads without errors
- ✅ Navigation works (click on menu items)
- ✅ Theme toggle works (try switching between light/dark)
- ✅ Animations play smoothly
- ✅ All sections are visible
- ✅ Contact form displays correctly

## Common Installation Issues

### Issue: "npm: command not found"
**Solution**: Install Node.js from https://nodejs.org/

### Issue: "EACCES: permission denied"
**Solution**: Don't use `sudo`. Fix npm permissions:
```bash
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
export PATH=~/.npm-global/bin:$PATH
```

### Issue: "Cannot find module"
**Solution**: Clear cache and reinstall:
```bash
rm -rf node_modules package-lock.json
npm install
```

### Issue: Port 5173 already in use
**Solution**: Kill the process or use a different port:
```bash
npm run dev -- --port 3000
```

### Issue: Vite errors or blank screen
**Solution**: Clear Vite cache:
```bash
rm -rf node_modules/.vite
npm run dev
```

## Build for Production

When you're ready to deploy:

```bash
npm run build
```

This creates a `dist` folder with optimized files.

### Preview Production Build

Test the production build locally:
```bash
npm run preview
```

## Environment Setup (Optional)

1. Copy the example environment file:
```bash
cp .env.example .env
```

2. Edit `.env` with your values:
```bash
# Use your preferred editor
nano .env
# or
code .env
```

3. Restart the development server

## What's Next?

1. **Read the Documentation**
   - `README.md` - Quick overview
   - `SETUP_GUIDE.md` - Detailed customization
   - `FEATURES_CHECKLIST.md` - Deployment checklist

2. **Customize Your Portfolio**
   - Update personal information
   - Add your projects
   - Update skills and experience
   - Change colors and styling

3. **Test Everything**
   - Try all navigation
   - Test on mobile devices
   - Check all links
   - Test contact form

4. **Deploy**
   - Choose a hosting platform
   - Follow deployment guide
   - Test live site

## Recommended Development Setup

### VS Code Extensions
- Volar (Vue Language Features)
- ESLint
- Prettier
- Tailwind CSS IntelliSense
- Path Intellisense

### Browser Extensions
- Vue DevTools (Chrome/Firefox)
- React DevTools (if comparing with React version)

## Development Tips

### Hot Reload
Changes to `.vue` files automatically reload the page.

### Component Location
All components are in `src/components/`

### Styling
- Global styles: `src/assets/styles/main.css`
- Component styles: Inside `<style>` tags in `.vue` files

### Adding New Dependencies

Using npm:
```bash
npm install package-name
```

Using yarn:
```bash
yarn add package-name
```

## Getting Help

If you encounter issues:

1. Check the console for errors (F12 in browser)
2. Read the error message carefully
3. Check the documentation files
4. Clear cache and restart dev server
5. Search for the error online
6. Check Vue.js and Vite documentation

## System Requirements

### Minimum
- Node.js 16+
- 2GB RAM
- Modern browser (Chrome, Firefox, Safari, Edge)

### Recommended
- Node.js 18+ (LTS)
- 4GB RAM
- SSD for faster builds
- Good internet connection for installing dependencies

## Success! 🎉

If you can see the portfolio in your browser and navigate around, you're all set!

Now customize it with your information and make it your own.

**Happy coding!** ✨
