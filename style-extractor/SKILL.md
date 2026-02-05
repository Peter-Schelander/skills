---
name: style-extractor
description: Extrahiert Design-Styleguides aus Webseiten, Screenshots, PDFs oder Dateien. Analysiert Farbpaletten, Typografie, Abstände, UI-Komponenten und Layout. Verwenden wenn der Benutzer "im Stil von", "Style extrahieren", "Design übernehmen", "Styleguide erstellen", "Farbschema analysieren", "Look and Feel", "PDF im Stil von", "Word-Dokument wie", "Newsletter im Design von" oder "Dokument reproduzieren" erwähnt.
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
| **PDF** | **Screenshot + Benutzer-Abfrage** | **Dokument-Reproduktion** |
| Figma | API oder Export-Analyse | Design-Handoffs |
| Lokale Dateien | Direkte Datei-Analyse | Bestehende Projekte |

---

## PDF-Analyse (WICHTIG)

```
⚠️ KRITISCH: PDF-Text-Extraktion liefert KEINE visuellen Daten!
```

Bei PDFs gilt ein spezieller Workflow:

1. **SCREENSHOT PFLICHT** - Ohne Screenshot: KEINE Farben, KEINE Schriften, KEIN Layout
2. **BENUTZER FRAGEN** - Bei Unsicherheit nachfragen statt raten
3. **LOGOS SEPARAT** - Nach Original-Dateien fragen (PNG/SVG)
4. **DOCX OUTPUT** - Für Word-Dokumente eigenes Template verwenden

**Workflow:**
```
1. Screenshot anfordern → "Bitte hänge einen Screenshot der PDF an"
2. Visuelle Analyse    → Farben, Schriften, Layout aus Screenshot
3. Validierung         → Bei Unsicherheit den Benutzer fragen
4. Dokumentieren       → Styleguide erstellen
5. Implementieren      → Mit python-docx für Word-Output
```

**Siehe:** [pdf-analysis.md](pdf-analysis.md) für den vollständigen Workflow

---

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
| **Word/DOCX** | **python-docx** | [docx-template.md](output-templates/docx-template.md) |
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

## PDF-Analyse

Bei PDFs als Vorlage (Newsletter, Flyer, Dokumente):

### Strukturelle Analyse
Analysiere die **Dokumentstruktur** genau:

```
Checkliste PDF-Layout:
- [ ] Gibt es eine Überschrift ÜBER dem Header-Banner?
- [ ] Wie ist der Header aufgebaut (URL, Regionen, Slogan)?
- [ ] Welches Bullet-Symbol wird verwendet (•, ·, -, ▪)?
- [ ] Wiederholt sich der Header auf Folgeseiten?
- [ ] Wie ist der Footer aufgebaut?
- [ ] Erscheint der Footer auf jeder Seite?
- [ ] Ein- oder mehrspaltig?
```

### Typische Dokumenten-Komponenten

| Komponente | Zu prüfen |
|------------|-----------|
| **Kategorie-Titel** | Über dem Banner, zentriert, Schriftgröße/Farbe |
| **Header-Banner** | Hintergrundfarbe, Textfarben, Schriftgrößen |
| **Hauptslogan** | Größe, Gewicht, Ausrichtung |
| **Abschnittstitel** | Größe, Farbe, Abstände davor/danach |
| **Bullet-Points** | Symbol (·, •, -), Einrückung, Fett-Markierungen |
| **Footer-Banner** | Inhalt, Hintergrund, Position |

### Beispiel: IoT-Wizard / COMM-UNITY Newsletter

Analysiertes Layout aus Original-PDF (Screenshot-Analyse):

**FARBEN:**
- Primärfarbe: GRÜN/TEAL #0D7377 (NICHT Blau!)
- Akzentfarbe: GOLD #C4A962 (Linie am Banner)
- Text: Dunkelgrau #333333
- Hintergrund: Weiß mit subtilen Wellenlinien

```
SEITE 1:
┌────────────────────────────────────────┐
│ ENERGIE INTELLIGENT MANAGEN  [LOGO]    │  ← Header: 9pt grün links, Wizard-Icon rechts
│ IoT-Wizard                             │  ← 8pt grün
├────────────────────────────────────────┤
│                                        │
│ ENERGIE INTELLIGENT MANAGEN            │  ← 28pt, GRÜN, Großbuchstaben
│ WIE DER IOT-WIZARD IHR HOTEL...        │  ← 12pt, grün, Großbuchstaben
│                                        │
│ Einleitungstext in dunkelgrau...       │  ← 10pt, Blocksatz
│                                        │
│ ▌▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ │  ← Grüner Banner mit GOLDENER Linie links
│ ▌  ABSCHNITTSTITEL IN WEISS           │  ← 11pt, weiß, Großbuchstaben
│ ▌▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ │
│                                        │
│ • Fetter Anfang: Normaler Text...      │  ← Bullet-Point
│ • Weiterer Punkt: Text...              │
│                                        │
├────────────────────────────────────────┤
│ ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ │  ← Grüner Footer
│ COMM-UNITY  📍Standorte  IOT-WIZARD.AT │  ← Logo links, Standorte mitte, URL rechts
│ ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ │
└────────────────────────────────────────┘

SEITE 2+:
- Header wiederholt (gleich wie Seite 1)
- Weitere Abschnitts-Banner mit goldener Linie
- Footer wiederholt
```

**WICHTIGE ERKENNTNISSE:**
1. Farbe ist GRÜN/TEAL, nicht Blau!
2. Abschnitts-Banner haben GOLDENE Akzentlinie links
3. Footer enthält COMM-UNITY Logo (nicht nur "IoT-Wizard")
4. Header ist klein oben links, nicht als großes Banner

### Wichtige Details bei PDFs

1. **Bullet-Symbole**: Standard-Bullets (•) vs. Middle-Dot (·) - großer visueller Unterschied!
2. **Wiederholende Elemente**: Header/Footer müssen auf jeder Seite erscheinen
3. **Hierarchie über Banner**: Manche Dokumente haben Titel ÜBER dem farbigen Banner
4. **Seitenumbrüche**: Content-Aufteilung auf Seiten beachten

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

**Web-Design:**
- "Erstelle mir eine Webseite im Stil von [URL]"
- "Extrahiere das Farbschema von dieser Seite"
- "Analysiere das Design und erstelle einen Styleguide"
- "Übernimm den Look and Feel von [Quelle]"
- "Welche Schriftarten verwendet diese Webseite?"

**Dokument-Reproduktion (PDF → Word):**
- "Erstelle ein Word-Dokument im Stil dieser PDF"
- "Newsletter im Design von [PDF] erstellen"
- "Dokument reproduzieren wie das Original"
- "PDF-Stil auf neuen Text anwenden"

## Zusätzliche Ressourcen

- [PDF-Analyse Workflow](pdf-analysis.md) - **Wichtig für Dokument-Reproduktion**
- [Extraktions-Methoden im Detail](extraction-methods.md)
- [Output-Templates](output-templates/)
- [Beispiel-Output](examples/example-output.md)
