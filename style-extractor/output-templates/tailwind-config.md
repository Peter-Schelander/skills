# Tailwind Config Template

Verwende dieses Template für Tailwind CSS v3+ Projekte.

## Basis-Template

```javascript
// tailwind.config.js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    './src/**/*.{js,ts,jsx,tsx,html}',
    // Weitere Pfade nach Bedarf
  ],
  
  theme: {
    extend: {
      // ==================== 
      // COLORS
      // ====================
      colors: {
        primary: {
          50: '#[lightest]',
          100: '#[lighter]',
          200: '#[light]',
          300: '#[light-medium]',
          400: '#[medium]',
          500: '#[base]',        // Hauptfarbe
          600: '#[medium-dark]',
          700: '#[dark]',
          800: '#[darker]',
          900: '#[darkest]',
          950: '#[near-black]',
        },
        secondary: {
          // ... gleiche Struktur
          500: '#[base]',
        },
        accent: '#[value]',
        
        // Semantic Colors
        success: {
          light: '#[light]',
          DEFAULT: '#[base]',
          dark: '#[dark]',
        },
        warning: {
          light: '#[light]',
          DEFAULT: '#[base]',
          dark: '#[dark]',
        },
        error: {
          light: '#[light]',
          DEFAULT: '#[base]',
          dark: '#[dark]',
        },
        info: {
          light: '#[light]',
          DEFAULT: '#[base]',
          dark: '#[dark]',
        },
      },
      
      // ==================== 
      // TYPOGRAPHY
      // ====================
      fontFamily: {
        sans: ['[Primary Font]', 'system-ui', '-apple-system', 'sans-serif'],
        serif: ['[Serif Font]', 'Georgia', 'serif'],
        mono: ['[Mono Font]', 'Fira Code', 'monospace'],
        // Custom display font
        display: ['[Display Font]', 'sans-serif'],
      },
      
      fontSize: {
        // Überschreibe oder erweitere Standard-Größen
        // Format: ['size', { lineHeight: 'value', letterSpacing: 'value' }]
        'xs': ['0.75rem', { lineHeight: '1rem' }],
        'sm': ['0.875rem', { lineHeight: '1.25rem' }],
        'base': ['1rem', { lineHeight: '1.5rem' }],
        'lg': ['1.125rem', { lineHeight: '1.75rem' }],
        'xl': ['1.25rem', { lineHeight: '1.75rem' }],
        '2xl': ['1.5rem', { lineHeight: '2rem' }],
        '3xl': ['1.875rem', { lineHeight: '2.25rem' }],
        '4xl': ['2.25rem', { lineHeight: '2.5rem' }],
        '5xl': ['3rem', { lineHeight: '1.16' }],
        '6xl': ['3.75rem', { lineHeight: '1.1' }],
      },
      
      // ==================== 
      // SPACING
      // ====================
      spacing: {
        // Ergänze Standard-Spacing
        '4.5': '1.125rem',  // 18px
        '13': '3.25rem',    // 52px
        '15': '3.75rem',    // 60px
        '18': '4.5rem',     // 72px
        '22': '5.5rem',     // 88px
        '26': '6.5rem',     // 104px
        '30': '7.5rem',     // 120px
      },
      
      // ==================== 
      // BORDERS & EFFECTS
      // ====================
      borderRadius: {
        // Standard: none, sm, DEFAULT, md, lg, xl, 2xl, 3xl, full
        '4xl': '2rem',
      },
      
      boxShadow: {
        // Überschreibe oder erweitere
        'sm': '0 1px 2px 0 rgb(0 0 0 / 0.05)',
        'DEFAULT': '0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1)',
        'md': '0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)',
        'lg': '0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1)',
        'xl': '0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1)',
        // Custom shadows
        'soft': '0 2px 15px -3px rgb(0 0 0 / 0.07), 0 10px 20px -2px rgb(0 0 0 / 0.04)',
        'card': '0 0 0 1px rgb(0 0 0 / 0.05), 0 2px 4px rgb(0 0 0 / 0.05)',
      },
      
      // ==================== 
      // TRANSITIONS
      // ====================
      transitionDuration: {
        '400': '400ms',
      },
      
      transitionTimingFunction: {
        'bounce-in': 'cubic-bezier(0.68, -0.55, 0.265, 1.55)',
      },
      
      // ==================== 
      // LAYOUT
      // ====================
      maxWidth: {
        '8xl': '88rem',   // 1408px
        '9xl': '96rem',   // 1536px
      },
      
      screens: {
        // Standard: sm:640, md:768, lg:1024, xl:1280, 2xl:1536
        'xs': '475px',
        '3xl': '1920px',
      },
      
      // ==================== 
      // ANIMATIONS
      // ====================
      animation: {
        'fade-in': 'fadeIn 0.3s ease-out',
        'slide-up': 'slideUp 0.3s ease-out',
      },
      
      keyframes: {
        fadeIn: {
          '0%': { opacity: '0' },
          '100%': { opacity: '1' },
        },
        slideUp: {
          '0%': { transform: 'translateY(10px)', opacity: '0' },
          '100%': { transform: 'translateY(0)', opacity: '1' },
        },
      },
    },
  },
  
  plugins: [
    // Offizielle Plugins
    // require('@tailwindcss/forms'),
    // require('@tailwindcss/typography'),
    // require('@tailwindcss/aspect-ratio'),
  ],
}
```

## Verwendung

```html
<button class="
  bg-primary-500 
  hover:bg-primary-600 
  text-white 
  px-4 py-2 
  rounded-md 
  font-medium 
  text-sm 
  transition-colors 
  duration-150
">
  Button
</button>
```

## Farbpalette generieren

Tools zur Generierung von Farbabstufungen:
- [Tailwind CSS Color Generator](https://uicolors.app/create)
- [Tailwind Shades](https://www.tailwindshades.com/)
- [Coolors](https://coolors.co/)
