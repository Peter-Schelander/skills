# Extraktions-Methoden im Detail

## Methode 1: Live-Browser (Cursor IDE Browser)

Die genaueste Methode für interaktive Webseiten.

### Vorgehen

```
1. browser_navigate → URL öffnen
2. browser_snapshot → Seitenstruktur erfassen
3. browser_evaluate → CSS-Werte auslesen
```

### CSS-Extraktion via JavaScript

```javascript
// Alle verwendeten Farben sammeln
function extractColors() {
  const colors = new Set();
  document.querySelectorAll('*').forEach(el => {
    const style = getComputedStyle(el);
    ['color', 'backgroundColor', 'borderColor'].forEach(prop => {
      const value = style.getPropertyValue(prop);
      if (value && value !== 'rgba(0, 0, 0, 0)') {
        colors.add(value);
      }
    });
  });
  return [...colors];
}

// Alle Schriftarten sammeln
function extractFonts() {
  const fonts = new Set();
  document.querySelectorAll('*').forEach(el => {
    fonts.add(getComputedStyle(el).fontFamily);
  });
  return [...fonts];
}

// Font-Sizes sammeln
function extractFontSizes() {
  const sizes = new Set();
  document.querySelectorAll('*').forEach(el => {
    sizes.add(getComputedStyle(el).fontSize);
  });
  return [...sizes].sort((a, b) => parseFloat(a) - parseFloat(b));
}
```

### Typische Selektoren für Komponenten

| Komponente | Selektoren |
|------------|------------|
| Buttons | `button`, `[class*="btn"]`, `[role="button"]` |
| Links | `a`, `[class*="link"]` |
| Cards | `[class*="card"]`, `article`, `.box` |
| Inputs | `input`, `textarea`, `select` |
| Headings | `h1, h2, h3, h4, h5, h6` |

---

## Methode 2: URL-Fetch (WebFetch)

Für statische Seiten ohne JavaScript-Rendering.

### Vorgehen

```
1. WebFetch → HTML abrufen
2. CSS-Links extrahieren
3. Inline-Styles parsen
4. Externe Stylesheets analysieren
```

### Was zu suchen ist

```css
/* In <style> Tags oder externen CSS-Dateien */
:root {
  --primary-color: #...;    /* CSS Variables */
  --font-family: ...;
}

/* Oder direkte Definitionen */
body { font-family: ...; }
.btn { background-color: ...; }
```

### Limitierungen

- Kein JavaScript-gerenderter Content
- Keine dynamischen Styles
- Keine Hover/Focus States sichtbar

---

## Methode 3: Screenshot-Analyse

Für Designs ohne Zugang zum Quellcode.

### Farbextraktion

1. **Dominante Farben identifizieren**
   - Hintergrundfarben (meist große Flächen)
   - Textfarben (häufigste dunkle Farben)
   - Akzentfarben (Buttons, Links, Highlights)

2. **Tools zur Unterstützung**
   - Color Picker im Bildbearbeitungsprogramm
   - Online: Coolors.co, Adobe Color
   - Browser-Extension: ColorZilla

### Schriftarten identifizieren

1. **Visuelle Merkmale analysieren**
   - Serif vs Sans-Serif
   - Strichstärke-Variationen
   - Besondere Buchstabenformen (a, g, e)

2. **Tools zur Identifikation**
   - WhatTheFont (myfonts.com)
   - Font Squirrel Matcherator
   - Google Fonts (visueller Vergleich)

### Abstände schätzen

```
Referenzgröße festlegen:
- Wenn Viewport-Breite bekannt: relative Berechnung
- Wenn Button-Höhe ~40px angenommen: davon ableiten
- Basis-Unit oft 4px oder 8px
```

---

## Methode 4: Figma-Analyse

Für Design-Handoffs und Prototypen.

### Via Figma API

```
1. File-Key aus URL extrahieren
2. GET /v1/files/{file_key}
3. Styles und Components parsen
```

### Via Export

1. **Design Tokens exportieren** (Plugin: Figma Tokens)
2. **CSS exportieren** (Plugin: CSS Export)
3. **Inspect-Panel** für einzelne Werte

### Zu extrahierende Figma-Eigenschaften

| Figma | CSS-Äquivalent |
|-------|----------------|
| Fill | background-color |
| Stroke | border |
| Effects → Drop Shadow | box-shadow |
| Text Properties | font-* |
| Auto Layout | flexbox/grid |
| Corner Radius | border-radius |

---

## Methode 5: Lokale Dateien

Für bestehende Projekte.

### HTML/CSS analysieren

```
1. Glob → CSS-Dateien finden (*.css, *.scss, *.less)
2. Read → Dateien einlesen
3. Grep → Patterns suchen
```

### Nützliche Grep-Patterns

```
# CSS Variables finden
--[a-z-]+:\s*[^;]+

# Hex-Farben
#[0-9a-fA-F]{3,6}

# RGB/RGBA
rgba?\([^)]+\)

# Font-Family Definitionen
font-family:\s*[^;]+
```

### Tailwind-Projekte

```
1. tailwind.config.js lesen
2. theme.extend extrahieren
3. Verwendete Klassen in HTML/JSX analysieren
```

---

## Priorisierung der Methoden

```
Entscheidungsbaum:

Ist es eine Live-Webseite?
├─ Ja → Brauchst du JavaScript-Content?
│       ├─ Ja → Browser-Methode
│       └─ Nein → WebFetch (schneller)
└─ Nein → Was hast du?
          ├─ Screenshot → Screenshot-Analyse
          ├─ Figma-Link → Figma-Analyse
          └─ Lokale Dateien → Datei-Analyse
```
