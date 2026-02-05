---
name: style-extractor
description: Extrahiert Design-Styleguides aus Webseiten, Screenshots oder Dateien. Analysiert Farbpaletten, Typografie, Abstände, UI-Komponenten und Layout. Verwenden wenn der Benutzer "im Stil von", "Style extrahieren", "Design übernehmen", "Styleguide erstellen", "Farbschema analysieren" oder "Look and Feel" erwähnt.
---

# Style Extractor

Extrahiere komplette Design-Systeme aus bestehenden Webseiten, Screenshots oder Designdateien und erstelle wiederverwendbare Styleguides.

## Quick Start

1. **Quelle identifizieren** - Was soll analysiert werden?
2. **Extraktion durchführen** - Passende Methode wählen
3. **Styleguide generieren** - Im gewünschten Format ausgeben

## Unterstützte Quellen

| Quelle | Methode | Beste für |
|--------|---------|-----------|
| Live-Browser | `browser_snapshot` + CSS-Analyse | Interaktive Webseiten |
| URL | `WebFetch` + HTML/CSS-Parsing | Statische Seiten |
| Screenshot | Visuelle Analyse | Designs ohne Quellcode |
| Figma | API oder Export-Analyse | Design-Handoffs |
| Lokale Dateien | Direkte Datei-Analyse | Bestehende Projekte |

## Extraktions-Workflow

### Schritt 1: Analyse starten

```
Analyse-Checkliste:
- [ ] Quelle identifiziert
- [ ] Hauptseite/Komponenten erfasst
- [ ] Farbpalette extrahiert
- [ ] Typografie dokumentiert
- [ ] Abstände gemessen
- [ ] UI-Komponenten katalogisiert
- [ ] Effekte notiert
- [ ] Layout-Struktur erfasst
```

### Schritt 2: Design-Elemente extrahieren

#### Farbpalette
Extrahiere und kategorisiere:
- **Primary**: Hauptmarkenfarbe
- **Secondary**: Unterstützende Farben
- **Accent**: Hervorhebungen, CTAs
- **Neutral**: Grautöne, Hintergründe
- **Semantic**: Success, Warning, Error, Info

#### Typografie
Dokumentiere:
- Font-Families (Headings, Body, Code)
- Font-Sizes (Scale: xs, sm, base, lg, xl, 2xl...)
- Font-Weights (light, normal, medium, semibold, bold)
- Line-Heights
- Letter-Spacing

#### Abstände (Spacing)
Erfasse das Spacing-System:
- Base-Unit (oft 4px oder 8px)
- Scale (0, 1, 2, 3, 4, 5, 6, 8, 10, 12, 16...)
- Container-Widths
- Grid-Gaps

#### UI-Komponenten
Analysiere wiederkehrende Elemente:
- Buttons (Varianten, States)
- Cards (Struktur, Schatten)
- Forms (Inputs, Labels, Validation)
- Navigation (Header, Sidebar, Footer)

#### Effekte
Notiere:
- Border-Radius (none, sm, md, lg, full)
- Box-Shadows (sm, md, lg, xl)
- Transitions (duration, easing)
- Hover/Focus States

### Schritt 3: Output generieren

Wähle das passende Format:

| Ziel | Format | Siehe |
|------|--------|-------|
| Modernes CSS | CSS Custom Properties | [css-variables.md](output-templates/css-variables.md) |
| Tailwind-Projekt | Tailwind Config | [tailwind-config.md](output-templates/tailwind-config.md) |
| Maschinenlesbar | JSON Styleguide | [styleguide-json.md](output-templates/styleguide-json.md) |
| Dokumentation | Markdown | Inline generieren |
| SCSS-Projekt | SCSS Variables | Analog zu CSS Variables |

## Browser-Analyse (Live-Webseite)

Bei Verwendung des integrierten Browsers:

1. **Navigiere zur Seite**: `browser_navigate`
2. **Erfasse Snapshot**: `browser_snapshot`
3. **Analysiere CSS**: Über DevTools oder computed styles
4. **Extrahiere Werte**: Systematisch alle Elemente durchgehen

```javascript
// Nützliche Browser-Befehle zur Analyse
getComputedStyle(element).getPropertyValue('property')
document.querySelectorAll('[class*="btn"]')  // Alle Buttons
```

## Screenshot-Analyse

Bei Bildern ohne Quellcode:

1. Identifiziere dominante Farben visuell
2. Schätze Schriftarten (Google Fonts Matcher, WhatTheFont)
3. Miss Abstände relativ zur Bildgröße
4. Dokumentiere visuelle Hierarchie

## Qualitätskriterien

Ein guter Styleguide enthält:

- [ ] Alle Farben mit HEX, RGB und HSL
- [ ] Schriftarten mit Fallbacks
- [ ] Konsistentes Spacing-System
- [ ] Dokumentierte Komponenten-Varianten
- [ ] Responsive Breakpoints
- [ ] Barrierefreiheits-Hinweise (Kontraste)

## Beispiel-Anfragen

Der Skill wird automatisch aktiviert bei:

- "Erstelle mir eine Webseite im Stil von [URL]"
- "Extrahiere das Farbschema von dieser Seite"
- "Analysiere das Design und erstelle einen Styleguide"
- "Übernimm den Look and Feel von [Quelle]"
- "Welche Schriftarten verwendet diese Webseite?"

## Zusätzliche Ressourcen

- [Extraktions-Methoden im Detail](extraction-methods.md)
- [Output-Templates](output-templates/)
- [Beispiel-Output](examples/example-output.md)
