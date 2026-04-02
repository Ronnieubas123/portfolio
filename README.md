# Alex Chen - Creative Portfolio (Vue 3)

A modern, responsive portfolio website built with Vue 3, Tailwind CSS v4, and VueUse Motion for smooth animations.

## Features

- ✨ Modern and professional design
- 🎨 Bold typography and asymmetrical layouts
- 🌓 Dark/Light mode with system preference detection
- 📱 Fully responsive across all devices
- ⚡ Smooth animations and transitions
- 🎯 Custom cursor effects
- 📊 Interactive scroll progress indicator
- ⌨️ Keyboard shortcuts for navigation
- 🚀 Loading screen with progress animation
- 💼 Comprehensive sections: Hero, About, Skills, Experience, Projects, Contact
- 🎭 Floating action button with quick actions

## Tech Stack

- **Framework**: Vue 3 (Composition API)
- **Styling**: Tailwind CSS v4
- **Animations**: @vueuse/motion
- **Router**: Vue Router 4
- **Build Tool**: Vite
- **Language**: JavaScript (ES6+)

## Installation

1. Navigate to the vue directory:
```bash
cd vue
```

2. Install dependencies:
```bash
npm install
```

## Development

Run the development server:
```bash
npm run dev
```

The application will be available at `http://localhost:5173`

## Build for Production

Create a production build:
```bash
npm run build
```

Preview the production build:
```bash
npm run preview
```

## Project Structure

```
vue/
├── public/              # Static assets
├── src/
│   ├── assets/
│   │   └── styles/
│   │       └── main.css       # Main CSS with Tailwind imports
│   ├── components/
│   │   ├── About.vue          # About section
│   │   ├── Contact.vue        # Contact form and info
│   │   ├── CustomCursor.vue   # Custom cursor component
│   │   ├── Experience.vue     # Work experience timeline
│   │   ├── FloatingActions.vue # FAB with quick actions
│   │   ├── Footer.vue         # Footer component
│   │   ├── Header.vue         # Navigation header
│   │   ├── Hero.vue           # Hero section
│   │   ├── KeyboardShortcuts.vue # Keyboard navigation
│   │   ├── LoadingScreen.vue  # Initial loading screen
│   │   ├── Projects.vue       # Projects showcase
│   │   ├── ScrollProgress.vue # Scroll indicator
│   │   ├── Skills.vue         # Skills showcase
│   │   └── ThemeToggle.vue    # Theme switcher
│   ├── router/
│   │   └── index.js           # Vue Router configuration
│   ├── views/
│   │   └── Home.vue           # Main home view
│   ├── App.vue                # Root component
│   └── main.js                # Application entry point
├── index.html                 # HTML entry point
├── package.json               # Dependencies and scripts
└── vite.config.js             # Vite configuration
```

## Keyboard Shortcuts

- `?` - Show keyboard shortcuts help
- `H` - Go to top
- `A` - Go to About section
- `S` - Go to Skills section
- `P` - Go to Projects section
- `C` - Go to Contact section
- `T` - Toggle theme
- `Esc` - Close modals

## Customization

### Colors

Edit the CSS variables in `src/assets/styles/main.css` to customize the color scheme:

```css
:root {
  --primary: #030213;
  --background: #ffffff;
  /* ... other color variables */
}
```

### Content

- Update personal information in each component
- Replace project images and data in `Projects.vue`
- Modify skills and experience in respective components
- Update social links throughout the components

### Images

Replace the Unsplash image URLs with your own images:
- Profile image in `About.vue`
- Project images in `Projects.vue`

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## License

This project is open source and available under the MIT License.

## Credits

- Icons: Inline SVG icons
- Images: Unsplash (for demo purposes)
- Animations: @vueuse/motion
- UI Components: Custom built with Tailwind CSS

## Contact

For questions or collaboration opportunities, reach out via the contact form on the website.
