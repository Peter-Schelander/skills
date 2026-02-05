# CSS Custom Properties Template

Verwende dieses Template für modernes CSS mit nativen Variables.

## Basis-Template

```css
:root {
  /* ==================== */
  /* COLORS               */
  /* ==================== */
  
  /* Primary */
  --color-primary-50: #[lightest];
  --color-primary-100: #[lighter];
  --color-primary-200: #[light];
  --color-primary-300: #[light-medium];
  --color-primary-400: #[medium];
  --color-primary-500: #[base];
  --color-primary-600: #[medium-dark];
  --color-primary-700: #[dark];
  --color-primary-800: #[darker];
  --color-primary-900: #[darkest];
  
  /* Secondary */
  --color-secondary-500: #[base];
  /* ... weitere Abstufungen nach Bedarf */
  
  /* Accent */
  --color-accent: #[value];
  
  /* Neutral / Grays */
  --color-gray-50: #[near-white];
  --color-gray-100: #[lighter];
  --color-gray-200: #[light];
  --color-gray-300: #[light-medium];
  --color-gray-400: #[medium];
  --color-gray-500: #[base];
  --color-gray-600: #[medium-dark];
  --color-gray-700: #[dark];
  --color-gray-800: #[darker];
  --color-gray-900: #[near-black];
  
  /* Semantic */
  --color-success: #[green];
  --color-warning: #[yellow/orange];
  --color-error: #[red];
  --color-info: #[blue];
  
  /* Backgrounds */
  --color-bg-primary: var(--color-gray-50);
  --color-bg-secondary: var(--color-gray-100);
  --color-bg-tertiary: var(--color-gray-200);
  
  /* Text */
  --color-text-primary: var(--color-gray-900);
  --color-text-secondary: var(--color-gray-600);
  --color-text-muted: var(--color-gray-400);
  --color-text-inverse: #ffffff;
  
  /* Borders */
  --color-border: var(--color-gray-200);
  --color-border-focus: var(--color-primary-500);
  
  /* ==================== */
  /* TYPOGRAPHY           */
  /* ==================== */
  
  /* Font Families */
  --font-family-sans: '[Primary Font]', system-ui, -apple-system, sans-serif;
  --font-family-serif: '[Serif Font]', Georgia, serif;
  --font-family-mono: '[Mono Font]', 'Fira Code', monospace;
  
  /* Font Sizes */
  --font-size-xs: 0.75rem;    /* 12px */
  --font-size-sm: 0.875rem;   /* 14px */
  --font-size-base: 1rem;     /* 16px */
  --font-size-lg: 1.125rem;   /* 18px */
  --font-size-xl: 1.25rem;    /* 20px */
  --font-size-2xl: 1.5rem;    /* 24px */
  --font-size-3xl: 1.875rem;  /* 30px */
  --font-size-4xl: 2.25rem;   /* 36px */
  --font-size-5xl: 3rem;      /* 48px */
  
  /* Font Weights */
  --font-weight-light: 300;
  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;
  
  /* Line Heights */
  --line-height-tight: 1.25;
  --line-height-normal: 1.5;
  --line-height-relaxed: 1.75;
  
  /* Letter Spacing */
  --letter-spacing-tight: -0.025em;
  --letter-spacing-normal: 0;
  --letter-spacing-wide: 0.025em;
  
  /* ==================== */
  /* SPACING              */
  /* ==================== */
  
  --space-0: 0;
  --space-1: 0.25rem;   /* 4px */
  --space-2: 0.5rem;    /* 8px */
  --space-3: 0.75rem;   /* 12px */
  --space-4: 1rem;      /* 16px */
  --space-5: 1.25rem;   /* 20px */
  --space-6: 1.5rem;    /* 24px */
  --space-8: 2rem;      /* 32px */
  --space-10: 2.5rem;   /* 40px */
  --space-12: 3rem;     /* 48px */
  --space-16: 4rem;     /* 64px */
  --space-20: 5rem;     /* 80px */
  --space-24: 6rem;     /* 96px */
  
  /* ==================== */
  /* BORDERS & EFFECTS    */
  /* ==================== */
  
  /* Border Radius */
  --radius-none: 0;
  --radius-sm: 0.125rem;   /* 2px */
  --radius-md: 0.375rem;   /* 6px */
  --radius-lg: 0.5rem;     /* 8px */
  --radius-xl: 0.75rem;    /* 12px */
  --radius-2xl: 1rem;      /* 16px */
  --radius-full: 9999px;
  
  /* Box Shadows */
  --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
  --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
  
  /* Border Widths */
  --border-width: 1px;
  --border-width-2: 2px;
  
  /* ==================== */
  /* TRANSITIONS          */
  /* ==================== */
  
  --transition-fast: 150ms ease;
  --transition-normal: 300ms ease;
  --transition-slow: 500ms ease;
  
  /* ==================== */
  /* LAYOUT               */
  /* ==================== */
  
  /* Container */
  --container-sm: 640px;
  --container-md: 768px;
  --container-lg: 1024px;
  --container-xl: 1280px;
  --container-2xl: 1536px;
  
  /* Z-Index */
  --z-dropdown: 100;
  --z-sticky: 200;
  --z-modal: 300;
  --z-tooltip: 400;
}

/* ==================== */
/* DARK MODE            */
/* ==================== */

@media (prefers-color-scheme: dark) {
  :root {
    --color-bg-primary: var(--color-gray-900);
    --color-bg-secondary: var(--color-gray-800);
    --color-text-primary: var(--color-gray-50);
    --color-text-secondary: var(--color-gray-300);
    --color-border: var(--color-gray-700);
  }
}

/* Oder mit Klasse */
.dark {
  --color-bg-primary: var(--color-gray-900);
  /* ... */
}
```

## Verwendung

```css
.button {
  background-color: var(--color-primary-500);
  color: var(--color-text-inverse);
  padding: var(--space-2) var(--space-4);
  border-radius: var(--radius-md);
  font-family: var(--font-family-sans);
  font-size: var(--font-size-sm);
  font-weight: var(--font-weight-medium);
  transition: background-color var(--transition-fast);
}

.button:hover {
  background-color: var(--color-primary-600);
}
```
