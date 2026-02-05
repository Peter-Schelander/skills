# Beispiel: Extrahierter Styleguide

Dieses Beispiel zeigt einen vollständig extrahierten Styleguide von einer fiktiven Webseite.

---

## Quelle

**URL**: https://example-modern-saas.com  
**Analysiert am**: 2024-01-15  
**Methode**: Browser-Analyse

---

## Farbpalette

### Primary (Blau)

| Stufe | HEX | RGB | Verwendung |
|-------|-----|-----|------------|
| 50 | `#eff6ff` | rgb(239, 246, 255) | Hintergrund hover |
| 100 | `#dbeafe` | rgb(219, 234, 254) | Badges, Tags |
| 200 | `#bfdbfe` | rgb(191, 219, 254) | Focus rings |
| 300 | `#93c5fd` | rgb(147, 197, 253) | - |
| 400 | `#60a5fa` | rgb(96, 165, 250) | Links hover |
| **500** | **`#3b82f6`** | rgb(59, 130, 246) | **Primary buttons, links** |
| 600 | `#2563eb` | rgb(37, 99, 235) | Buttons hover |
| 700 | `#1d4ed8` | rgb(29, 78, 216) | Active states |
| 800 | `#1e40af` | rgb(30, 64, 175) | - |
| 900 | `#1e3a8a` | rgb(30, 58, 138) | Dark text |

### Neutral (Grau)

| Stufe | HEX | Verwendung |
|-------|-----|------------|
| 50 | `#f9fafb` | Page background |
| 100 | `#f3f4f6` | Card background |
| 200 | `#e5e7eb` | Borders |
| 300 | `#d1d5db` | Disabled text |
| 400 | `#9ca3af` | Placeholder text |
| 500 | `#6b7280` | Secondary text |
| 600 | `#4b5563` | Body text |
| 700 | `#374151` | Headings |
| 800 | `#1f2937` | - |
| 900 | `#111827` | Primary text |

### Semantic

| Typ | HEX | Verwendung |
|-----|-----|------------|
| Success | `#10b981` | Erfolg, bestätigt |
| Warning | `#f59e0b` | Warnung, Achtung |
| Error | `#ef4444` | Fehler, Löschen |
| Info | `#3b82f6` | Information |

---

## Typografie

### Schriftarten

| Verwendung | Font | Fallbacks |
|------------|------|-----------|
| Headings | Inter | system-ui, sans-serif |
| Body | Inter | system-ui, sans-serif |
| Code | Fira Code | Consolas, monospace |

### Größen-Scale

| Name | Größe | Line-Height | Verwendung |
|------|-------|-------------|------------|
| xs | 12px / 0.75rem | 16px | Labels, Badges |
| sm | 14px / 0.875rem | 20px | Secondary text, Buttons |
| base | 16px / 1rem | 24px | Body text |
| lg | 18px / 1.125rem | 28px | Lead paragraphs |
| xl | 20px / 1.25rem | 28px | H4 |
| 2xl | 24px / 1.5rem | 32px | H3 |
| 3xl | 30px / 1.875rem | 36px | H2 |
| 4xl | 36px / 2.25rem | 40px | H1 |
| 5xl | 48px / 3rem | 1 | Hero headlines |

### Font Weights

| Name | Wert | Verwendung |
|------|------|------------|
| normal | 400 | Body text |
| medium | 500 | Buttons, Labels |
| semibold | 600 | Subheadings |
| bold | 700 | Headings |

---

## Spacing

**Base Unit**: 4px

| Token | Wert | Verwendung |
|-------|------|------------|
| space-1 | 4px | Inline-Abstände |
| space-2 | 8px | Icon gaps, tight padding |
| space-3 | 12px | Button padding (y) |
| space-4 | 16px | Standard padding |
| space-5 | 20px | Card padding |
| space-6 | 24px | Section gaps |
| space-8 | 32px | Component gaps |
| space-10 | 40px | Large gaps |
| space-12 | 48px | Section padding |
| space-16 | 64px | Page sections |

---

## Border Radius

| Token | Wert | Verwendung |
|-------|------|------------|
| none | 0 | - |
| sm | 4px | Badges, Tags |
| md | 6px | Buttons, Inputs |
| lg | 8px | Cards |
| xl | 12px | Modals, Dropdowns |
| full | 9999px | Pills, Avatare |

---

## Shadows

```css
/* Small - für Buttons */
--shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);

/* Medium - für Cards */
--shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 
             0 2px 4px -2px rgb(0 0 0 / 0.1);

/* Large - für Modals */
--shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 
             0 4px 6px -4px rgb(0 0 0 / 0.1);

/* XL - für Dropdowns */
--shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 
             0 8px 10px -6px rgb(0 0 0 / 0.1);
```

---

## Komponenten

### Button - Primary

```css
.btn-primary {
  background-color: #3b82f6;
  color: #ffffff;
  font-size: 14px;
  font-weight: 500;
  padding: 8px 16px;
  border-radius: 6px;
  box-shadow: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  transition: all 150ms ease;
}

.btn-primary:hover {
  background-color: #2563eb;
}

.btn-primary:focus {
  outline: none;
  box-shadow: 0 0 0 3px #bfdbfe;
}
```

### Card

```css
.card {
  background: #ffffff;
  border-radius: 8px;
  box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1);
  padding: 24px;
}
```

### Input

```css
.input {
  width: 100%;
  padding: 8px 12px;
  font-size: 14px;
  border: 1px solid #e5e7eb;
  border-radius: 6px;
  transition: border-color 150ms ease;
}

.input:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px #dbeafe;
}
```

---

## Layout

### Breakpoints

| Name | Wert |
|------|------|
| sm | 640px |
| md | 768px |
| lg | 1024px |
| xl | 1280px |
| 2xl | 1536px |

### Container

```css
.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 16px;
}

@media (min-width: 640px) {
  .container { padding: 0 24px; }
}

@media (min-width: 1024px) {
  .container { padding: 0 32px; }
}
```

---

## Generierte Outputs

Basierend auf dieser Analyse wurden folgende Dateien generiert:

- `variables.css` - CSS Custom Properties
- `tailwind.config.js` - Tailwind-Konfiguration
- `tokens.json` - Design Tokens im JSON-Format
