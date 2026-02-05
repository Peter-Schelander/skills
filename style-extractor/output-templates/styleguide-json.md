# JSON Styleguide Template

Maschinenlesbares Format für Design Tokens und automatisierte Verarbeitung.

## Basis-Template

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "name": "[Project Name] Design System",
  "version": "1.0.0",
  "description": "Extracted from [Source]",
  "extractedAt": "[ISO Date]",
  
  "colors": {
    "primary": {
      "50": { "value": "#...", "type": "color" },
      "100": { "value": "#...", "type": "color" },
      "200": { "value": "#...", "type": "color" },
      "300": { "value": "#...", "type": "color" },
      "400": { "value": "#...", "type": "color" },
      "500": { "value": "#...", "type": "color", "description": "Base primary color" },
      "600": { "value": "#...", "type": "color" },
      "700": { "value": "#...", "type": "color" },
      "800": { "value": "#...", "type": "color" },
      "900": { "value": "#...", "type": "color" }
    },
    "secondary": {
      "500": { "value": "#...", "type": "color" }
    },
    "accent": {
      "value": "#...",
      "type": "color"
    },
    "neutral": {
      "50": { "value": "#...", "type": "color" },
      "100": { "value": "#...", "type": "color" },
      "200": { "value": "#...", "type": "color" },
      "300": { "value": "#...", "type": "color" },
      "400": { "value": "#...", "type": "color" },
      "500": { "value": "#...", "type": "color" },
      "600": { "value": "#...", "type": "color" },
      "700": { "value": "#...", "type": "color" },
      "800": { "value": "#...", "type": "color" },
      "900": { "value": "#...", "type": "color" }
    },
    "semantic": {
      "success": { "value": "#...", "type": "color" },
      "warning": { "value": "#...", "type": "color" },
      "error": { "value": "#...", "type": "color" },
      "info": { "value": "#...", "type": "color" }
    },
    "background": {
      "primary": { "value": "{colors.neutral.50}", "type": "color" },
      "secondary": { "value": "{colors.neutral.100}", "type": "color" }
    },
    "text": {
      "primary": { "value": "{colors.neutral.900}", "type": "color" },
      "secondary": { "value": "{colors.neutral.600}", "type": "color" },
      "muted": { "value": "{colors.neutral.400}", "type": "color" }
    }
  },
  
  "typography": {
    "fontFamilies": {
      "sans": {
        "value": "[Font], system-ui, sans-serif",
        "type": "fontFamily"
      },
      "serif": {
        "value": "[Font], Georgia, serif",
        "type": "fontFamily"
      },
      "mono": {
        "value": "[Font], monospace",
        "type": "fontFamily"
      }
    },
    "fontSizes": {
      "xs": { "value": "0.75rem", "type": "fontSize", "px": 12 },
      "sm": { "value": "0.875rem", "type": "fontSize", "px": 14 },
      "base": { "value": "1rem", "type": "fontSize", "px": 16 },
      "lg": { "value": "1.125rem", "type": "fontSize", "px": 18 },
      "xl": { "value": "1.25rem", "type": "fontSize", "px": 20 },
      "2xl": { "value": "1.5rem", "type": "fontSize", "px": 24 },
      "3xl": { "value": "1.875rem", "type": "fontSize", "px": 30 },
      "4xl": { "value": "2.25rem", "type": "fontSize", "px": 36 },
      "5xl": { "value": "3rem", "type": "fontSize", "px": 48 }
    },
    "fontWeights": {
      "light": { "value": 300, "type": "fontWeight" },
      "normal": { "value": 400, "type": "fontWeight" },
      "medium": { "value": 500, "type": "fontWeight" },
      "semibold": { "value": 600, "type": "fontWeight" },
      "bold": { "value": 700, "type": "fontWeight" }
    },
    "lineHeights": {
      "tight": { "value": 1.25, "type": "lineHeight" },
      "normal": { "value": 1.5, "type": "lineHeight" },
      "relaxed": { "value": 1.75, "type": "lineHeight" }
    },
    "letterSpacing": {
      "tight": { "value": "-0.025em", "type": "letterSpacing" },
      "normal": { "value": "0", "type": "letterSpacing" },
      "wide": { "value": "0.025em", "type": "letterSpacing" }
    }
  },
  
  "spacing": {
    "baseUnit": { "value": "4px", "type": "spacing" },
    "scale": {
      "0": { "value": "0", "type": "spacing" },
      "1": { "value": "0.25rem", "type": "spacing", "px": 4 },
      "2": { "value": "0.5rem", "type": "spacing", "px": 8 },
      "3": { "value": "0.75rem", "type": "spacing", "px": 12 },
      "4": { "value": "1rem", "type": "spacing", "px": 16 },
      "5": { "value": "1.25rem", "type": "spacing", "px": 20 },
      "6": { "value": "1.5rem", "type": "spacing", "px": 24 },
      "8": { "value": "2rem", "type": "spacing", "px": 32 },
      "10": { "value": "2.5rem", "type": "spacing", "px": 40 },
      "12": { "value": "3rem", "type": "spacing", "px": 48 },
      "16": { "value": "4rem", "type": "spacing", "px": 64 },
      "20": { "value": "5rem", "type": "spacing", "px": 80 },
      "24": { "value": "6rem", "type": "spacing", "px": 96 }
    }
  },
  
  "borders": {
    "radius": {
      "none": { "value": "0", "type": "borderRadius" },
      "sm": { "value": "0.125rem", "type": "borderRadius", "px": 2 },
      "md": { "value": "0.375rem", "type": "borderRadius", "px": 6 },
      "lg": { "value": "0.5rem", "type": "borderRadius", "px": 8 },
      "xl": { "value": "0.75rem", "type": "borderRadius", "px": 12 },
      "2xl": { "value": "1rem", "type": "borderRadius", "px": 16 },
      "full": { "value": "9999px", "type": "borderRadius" }
    },
    "width": {
      "default": { "value": "1px", "type": "borderWidth" },
      "2": { "value": "2px", "type": "borderWidth" }
    }
  },
  
  "effects": {
    "shadows": {
      "sm": {
        "value": "0 1px 2px 0 rgb(0 0 0 / 0.05)",
        "type": "boxShadow"
      },
      "md": {
        "value": "0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)",
        "type": "boxShadow"
      },
      "lg": {
        "value": "0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1)",
        "type": "boxShadow"
      },
      "xl": {
        "value": "0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1)",
        "type": "boxShadow"
      }
    },
    "transitions": {
      "fast": { "value": "150ms ease", "type": "transition" },
      "normal": { "value": "300ms ease", "type": "transition" },
      "slow": { "value": "500ms ease", "type": "transition" }
    }
  },
  
  "layout": {
    "breakpoints": {
      "sm": { "value": "640px", "type": "dimension" },
      "md": { "value": "768px", "type": "dimension" },
      "lg": { "value": "1024px", "type": "dimension" },
      "xl": { "value": "1280px", "type": "dimension" },
      "2xl": { "value": "1536px", "type": "dimension" }
    },
    "containers": {
      "sm": { "value": "640px", "type": "dimension" },
      "md": { "value": "768px", "type": "dimension" },
      "lg": { "value": "1024px", "type": "dimension" },
      "xl": { "value": "1280px", "type": "dimension" }
    },
    "zIndex": {
      "dropdown": { "value": 100, "type": "number" },
      "sticky": { "value": 200, "type": "number" },
      "modal": { "value": 300, "type": "number" },
      "tooltip": { "value": 400, "type": "number" }
    }
  },
  
  "components": {
    "button": {
      "primary": {
        "background": "{colors.primary.500}",
        "color": "#ffffff",
        "borderRadius": "{borders.radius.md}",
        "padding": "{spacing.scale.2} {spacing.scale.4}",
        "fontSize": "{typography.fontSizes.sm}",
        "fontWeight": "{typography.fontWeights.medium}",
        "hover": {
          "background": "{colors.primary.600}"
        }
      }
    },
    "card": {
      "background": "#ffffff",
      "borderRadius": "{borders.radius.lg}",
      "shadow": "{effects.shadows.md}",
      "padding": "{spacing.scale.6}"
    },
    "input": {
      "background": "#ffffff",
      "borderColor": "{colors.neutral.300}",
      "borderRadius": "{borders.radius.md}",
      "padding": "{spacing.scale.2} {spacing.scale.3}",
      "focus": {
        "borderColor": "{colors.primary.500}",
        "shadow": "0 0 0 3px {colors.primary.100}"
      }
    }
  }
}
```

## Verwendung

Dieses JSON-Format ist kompatibel mit:
- **Style Dictionary** (Amazon)
- **Tokens Studio** (Figma Plugin)
- **Design Token Transformers**

### Beispiel: Style Dictionary Config

```javascript
// config.js
module.exports = {
  source: ['styleguide.json'],
  platforms: {
    css: {
      transformGroup: 'css',
      buildPath: 'build/css/',
      files: [{
        destination: 'variables.css',
        format: 'css/variables'
      }]
    },
    js: {
      transformGroup: 'js',
      buildPath: 'build/js/',
      files: [{
        destination: 'tokens.js',
        format: 'javascript/es6'
      }]
    }
  }
};
```
