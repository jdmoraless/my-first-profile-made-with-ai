# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Hato is a minimal portfolio showcase template built with Nuxt 3, Nuxt UI, and TailwindCSS. It's designed as a single-page landing template for designers, agencies, or studios seeking simplicity and elegance.

## Commands

### Development
```bash
npm install              # Install dependencies
npm run dev             # Start dev server on http://localhost:3000
npm run build           # Build for production
npm run preview         # Preview production build locally
npm run generate        # Generate static site
```

## Architecture

### Single Page Application Structure
The entire application is rendered through `app.vue` which serves as the main entry point. There are no separate pages - all content is displayed on a single view.

### Component Composition in app.vue
Components are composed in a specific order in `app.vue:6-10`:
1. `SwitchMode` - Dark/light theme toggle
2. `PhotoProfile` - User avatar
3. `MyInfo` - Name, title, and bio
4. `SocialNetwork` - Social media links
5. `Gallery` - Image grid

All components use lazy loading with the `Lazy` prefix.

### Configuration-Driven Content
All user-facing content is managed through `app.config.ts` rather than hardcoded in components. Components retrieve data using `useAppConfig()` composable:

```typescript
const app = useAppConfig();
const { data: { name, title, bio } } = app
```

To customize the portfolio, edit `app.config.ts:11-41` where all personal information, social links, and gallery images are defined.

### Image Handling
- Uses Nuxt Image module with Unsplash provider configured in `nuxt.config.ts:5-23`
- Gallery images in `app.config.ts` are Unsplash photo IDs (the hash portion of the URL)
- Image quality defaults to 50 for optimization
- Custom Image component wraps the nuxt-image implementation

### Styling System
- Nuxt UI provides the base component library
- Primary color: emerald, Gray scale: zinc (configured in `app.config.ts:2-10`)
- Dark mode support is built-in through Nuxt UI
- Motion animations via VueUse/Motion with `v-motion-fade` and `v-motion-fade-visible` directives

### Modules
The project uses these Nuxt modules (`nuxt.config.ts:4`):
- `@nuxt/ui` - Component library
- `@vueuse/motion/nuxt` - Animation composables
- `@nuxt/image` - Image optimization
