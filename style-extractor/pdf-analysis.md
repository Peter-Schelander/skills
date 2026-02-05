# PDF-Analyse Workflow

PDF-Dokumente erfordern einen speziellen Analyse-Ansatz, da die Text-Extraktion KEINE visuellen Informationen liefert.

## KRITISCH: Screenshot ist PFLICHT

```
⚠️ WARNUNG: PDF-Text-Extraktion liefert NUR den Textinhalt!
   - KEINE Farben
   - KEINE Schriftarten
   - KEIN Layout
   - KEINE Abstände
   
   → Ohne Screenshot ist eine Style-Analyse UNMÖGLICH
```

## Schritt 1: Screenshot anfordern

**BEVOR du mit der Analyse beginnst**, fordere einen Screenshot an:

```
Beispiel-Anfrage an Benutzer:
"Bitte hänge einen Screenshot der PDF an deine nächste Nachricht.
Am besten:
1. Seite 1 vollständig - für Header, Farben, Schriften, Layout
2. Optional: Seite 2 - falls das Layout dort anders ist"
```

### Warum Screenshot statt PDF?

| PDF-Read | Screenshot |
|----------|------------|
| Nur Text | Farben sichtbar |
| Keine Formatierung | Schriftarten erkennbar |
| Keine Struktur | Layout messbar |
| Keine Bilder | Logos/Icons sichtbar |

## Schritt 2: Visuelle Analyse durchführen

Wenn der Screenshot vorliegt, extrahiere systematisch:

### Farben

```
Checkliste Farbanalyse:
- [ ] Primärfarbe identifizieren (Header, Überschriften, Banner)
- [ ] Sekundärfarbe/Akzentfarbe (Linien, Highlights)
- [ ] Textfarbe (Fließtext, meist Dunkelgrau)
- [ ] Hintergrundfarbe (weiß, grau, Muster?)
- [ ] Weitere Farben (Footer, CTAs, Badges)
```

**Farben schätzen aus Screenshot:**
- Teal/Petrol: #0D7377, #00837B, #008B8B
- Blau: #0066B3, #2563EB, #3B82F6
- Grün: #00A651, #10B981, #059669
- Gold/Gelb: #C4A962, #D4AF37, #F59E0B
- Grau (Text): #333333, #4B5563, #374151

### Typografie

```
Checkliste Typografie:
- [ ] Schriftart-Typ: Serif oder Sans-Serif?
- [ ] Besondere Merkmale (rund, eckig, modern, klassisch)
- [ ] Überschriften: Größe relativ zum Body-Text
- [ ] Body-Text: Geschätzte Größe (meist 10-12pt)
- [ ] Großbuchstaben verwendet? Wo?
```

**Schriftart-Hinweise:**
- Moderne Sans-Serif: Calibri, Arial, Helvetica, Open Sans
- Klassische Serif: Times, Georgia, Garamond
- Humanistische Sans: Frutiger, Myriad Pro, Segoe UI

### Layout-Struktur

```
Checkliste Layout:
- [ ] Header-Position und Inhalt
- [ ] Logo-Position (links, rechts, zentriert)
- [ ] Hauptüberschrift-Stil
- [ ] Abschnitts-Banner (Hintergrundfarbe, Akzentlinien?)
- [ ] Bullet-Point-Symbol (•, ·, -, ▪)
- [ ] Footer-Aufbau (Spalten, Inhalt)
- [ ] Seitenränder (schmal, normal, breit)
```

## Schritt 3: Benutzer-Validierung

Falls du bei einem Element unsicher bist, **FRAGE den Benutzer**:

### Fragen zu Farben

```
"Ich sehe die Primärfarbe als Teal/Grün. Kannst du bestätigen:
- Ist es eher #0D7377 (Teal) oder #00A651 (Grün)?
- Oder hast du den exakten HEX-Code?"
```

### Fragen zu Schriftarten

```
"Die Schriftart sieht aus wie eine moderne Sans-Serif.
- Weißt du, welche Schriftart verwendet wird?
- Falls nicht: Soll ich Calibri oder Arial als Fallback verwenden?"
```

### Fragen zu Logos/Assets

```
"Im Original sehe ich ein Logo/Icon.
- Hast du die Datei als PNG oder SVG?
- Falls nicht: Soll ich einen Platzhalter einfügen oder es weglassen?"
```

## Schritt 4: Styleguide dokumentieren

Nach der Analyse, dokumentiere die Ergebnisse strukturiert:

```markdown
## Extrahierter Styleguide: [Dokumentname]

### Farben
| Verwendung | HEX | Beschreibung |
|------------|-----|--------------|
| Primär | #0D7377 | Header, Überschriften, Banner |
| Akzent | #C4A962 | Linien, Highlights |
| Text | #333333 | Fließtext |
| Hintergrund | #FFFFFF | Seitenhintergrund |

### Typografie
| Element | Schrift | Größe | Gewicht |
|---------|---------|-------|---------|
| Header-Slogan | Calibri | 9pt | Bold |
| Hauptüberschrift | Calibri | 28pt | Bold |
| Untertitel | Calibri | 12pt | Bold |
| Body | Calibri | 10pt | Normal |
| Footer | Calibri | 8pt | Normal |

### Layout-Komponenten
- Header: Klein oben links, Logo rechts
- Banner: Grün mit goldener Akzentlinie links
- Bullets: Standard-Punkt (•)
- Footer: Dreispaltig (Logo | Standorte | URL)
```

## Schritt 5: Output generieren

Für Dokument-Reproduktion siehe:
- [docx-template.md](output-templates/docx-template.md) - Word/DOCX Ausgabe

## Häufige Fehler vermeiden

### Fehler 1: Farben raten ohne Screenshot
```
❌ FALSCH: "Ich nehme an, die Farbe ist Blau (#0066B3)"
✅ RICHTIG: "Bitte sende einen Screenshot, damit ich die Farben sehen kann"
```

### Fehler 2: Zu schnell analysieren
```
❌ FALSCH: Sofort mit der Implementierung beginnen
✅ RICHTIG: Erst alle Elemente dokumentieren, dann implementieren
```

### Fehler 3: Unsicherheiten nicht klären
```
❌ FALSCH: Bei Unsicherheit einfach schätzen
✅ RICHTIG: Den Benutzer fragen, bevor du falsche Werte verwendest
```

### Fehler 4: Logos selbst "erfinden"
```
❌ FALSCH: Ein Text-Logo als Ersatz erstellen
✅ RICHTIG: Nach der Original-Datei fragen oder explizit weglassen
```

## Zusammenfassung

```
PDF-ANALYSE IN 5 SCHRITTEN:

1. SCREENSHOT ANFORDERN → Ohne geht nichts!
2. VISUELL ANALYSIEREN  → Farben, Schriften, Layout
3. BENUTZER FRAGEN      → Bei Unsicherheit nachfragen
4. DOKUMENTIEREN        → Styleguide erstellen
5. IMPLEMENTIEREN       → Mit korrekten Werten
```
