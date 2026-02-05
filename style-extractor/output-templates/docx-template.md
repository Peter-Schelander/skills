# DOCX Styleguide Template

Template für die Erstellung von Word-Dokumenten mit python-docx basierend auf extrahierten Styles.

## Voraussetzungen

```bash
pip install python-docx
```

## Basis-Struktur

```python
from docx import Document
from docx.shared import Pt, Inches, Cm, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH
from docx.enum.table import WD_TABLE_ALIGNMENT, WD_CELL_VERTICAL_ALIGNMENT
from docx.oxml.ns import qn
from docx.oxml import OxmlElement
```

## Farbkonstanten Template

Ersetze die Platzhalter mit den extrahierten Werten:

```python
# === FARBEN (aus Style-Extraktion) ===

# Primärfarbe - für Header, Überschriften, Banner
PRIMARY = RGBColor(0x##, 0x##, 0x##)      # z.B. 0x0D, 0x73, 0x77 für Teal

# Sekundär/Akzent - für Linien, Highlights
ACCENT = RGBColor(0x##, 0x##, 0x##)       # z.B. 0xC4, 0xA9, 0x62 für Gold

# Textfarben
TEXT_PRIMARY = RGBColor(0x33, 0x33, 0x33)  # Dunkelgrau für Fließtext
TEXT_BLACK = RGBColor(0x00, 0x00, 0x00)    # Schwarz für fette Teile
WHITE = RGBColor(0xFF, 0xFF, 0xFF)         # Weiß für Text auf Farbe
```

## Schriftgrößen Template

```python
# === SCHRIFTGRÖSSEN (aus Style-Extraktion) ===

FONT_FAMILY = "Calibri"  # oder Arial, Helvetica, etc.

# Header-Bereich
HEADER_SLOGAN_SIZE = Pt(9)     # Kleine Texte im Header
HEADER_BRAND_SIZE = Pt(8)      # Markenname/Slogan

# Hauptinhalt
MAIN_TITLE_SIZE = Pt(28)       # Große Hauptüberschrift
SUBTITLE_SIZE = Pt(12)         # Untertitel
SECTION_TITLE_SIZE = Pt(11)    # Abschnittstitel (im Banner)
BODY_SIZE = Pt(10)             # Fließtext

# Footer
FOOTER_SIZE = Pt(8)            # Footer-Text
```

## Helper-Funktionen

### Zellen-Hintergrundfarbe setzen

```python
def set_cell_shading(cell, color_hex):
    """Setzt die Hintergrundfarbe einer Tabellenzelle.
    
    Args:
        cell: Die Zelle
        color_hex: Farbe als String ohne # (z.B. '0D7377')
    """
    tc = cell._tc
    tcPr = tc.get_or_add_tcPr()
    shading = OxmlElement('w:shd')
    shading.set(qn('w:val'), 'clear')
    shading.set(qn('w:fill'), color_hex)
    tcPr.append(shading)
```

### Tabellen-Rahmen entfernen

```python
def remove_table_borders(table):
    """Entfernt alle Rahmen einer Tabelle."""
    tbl = table._tbl
    tblPr = tbl.tblPr if tbl.tblPr is not None else OxmlElement('w:tblPr')
    tblBorders = OxmlElement('w:tblBorders')
    for border_name in ['top', 'left', 'bottom', 'right', 'insideH', 'insideV']:
        border = OxmlElement(f'w:{border_name}')
        border.set(qn('w:val'), 'nil')
        tblBorders.append(border)
    tblPr.append(tblBorders)
```

### Formatierter Text-Run

```python
def create_run(paragraph, text, font_size=BODY_SIZE, bold=False, 
               italic=False, color=TEXT_PRIMARY, all_caps=False):
    """Erstellt einen formatierten Text-Run.
    
    Args:
        paragraph: Der Paragraph
        text: Der Text
        font_size: Schriftgröße (Pt)
        bold: Fett?
        italic: Kursiv?
        color: RGBColor
        all_caps: Großbuchstaben?
    """
    run = paragraph.add_run(text)
    run.font.name = FONT_FAMILY
    run.font.size = font_size
    run.bold = bold
    run.italic = italic
    run.font.color.rgb = color
    if all_caps:
        run.font.all_caps = True
    return run
```

## Dokument-Komponenten

### Header (klein, oben links)

```python
def add_header(doc):
    """Header mit Slogan links und Platzhalter für Logo rechts."""
    table = doc.add_table(rows=1, cols=2)
    table.autofit = False
    remove_table_borders(table)
    
    # Linke Spalte: Text
    cell_left = table.rows[0].cells[0]
    cell_left.width = Inches(4)
    
    p1 = cell_left.paragraphs[0]
    create_run(p1, "SLOGAN TEXT", font_size=HEADER_SLOGAN_SIZE, 
               bold=True, color=PRIMARY, all_caps=True)
    
    p2 = cell_left.add_paragraph()
    create_run(p2, "Markenname", font_size=HEADER_BRAND_SIZE, color=PRIMARY)
    
    # Rechte Spalte: Logo-Platzhalter
    cell_right = table.rows[0].cells[1]
    cell_right.width = Inches(2)
    # Hier Logo einfügen falls vorhanden:
    # cell_right.paragraphs[0].add_run().add_picture('logo.png', width=Inches(1))
```

### Hauptüberschrift

```python
def add_main_title(doc, title, subtitle=None):
    """Große Hauptüberschrift mit optionalem Untertitel."""
    p_title = doc.add_paragraph()
    create_run(p_title, title.upper(), font_size=MAIN_TITLE_SIZE, 
               bold=True, color=PRIMARY)
    p_title.paragraph_format.space_after = Pt(4)
    
    if subtitle:
        p_sub = doc.add_paragraph()
        create_run(p_sub, subtitle.upper(), font_size=SUBTITLE_SIZE, 
                   bold=True, color=PRIMARY)
        p_sub.paragraph_format.space_after = Pt(16)
```

### Abschnitts-Banner mit Akzentlinie

```python
def add_section_banner(doc, title):
    """Farbiger Banner mit Akzentlinie links."""
    doc.add_paragraph()  # Abstand
    
    # Tabelle: Schmale Akzentlinie | Hauptbanner
    table = doc.add_table(rows=1, cols=2)
    table.autofit = False
    remove_table_borders(table)
    
    # Akzentlinie (schmal, andere Farbe)
    cell_accent = table.rows[0].cells[0]
    cell_accent.width = Inches(0.08)
    set_cell_shading(cell_accent, 'C4A962')  # Gold/Akzent
    
    # Hauptbanner
    cell_main = table.rows[0].cells[1]
    cell_main.width = Inches(6.2)
    set_cell_shading(cell_main, '0D7377')  # Primärfarbe
    
    p = cell_main.paragraphs[0]
    create_run(p, title.upper(), font_size=SECTION_TITLE_SIZE, 
               bold=True, color=WHITE)
    
    doc.add_paragraph()  # Abstand
```

### Bullet-Point mit fettem Anfang

```python
def add_bullet_point(doc, bold_part, normal_part):
    """Bullet-Point mit fettem Einleitungstext."""
    p = doc.add_paragraph()
    p.paragraph_format.left_indent = Inches(0.2)
    p.paragraph_format.first_line_indent = Inches(-0.15)
    p.paragraph_format.space_after = Pt(6)
    
    # Bullet-Symbol
    create_run(p, "• ", font_size=BODY_SIZE, color=TEXT_PRIMARY)
    
    # Fetter Teil
    if bold_part:
        create_run(p, bold_part, font_size=BODY_SIZE, bold=True, color=TEXT_BLACK)
    
    # Normaler Teil
    create_run(p, normal_part, font_size=BODY_SIZE, color=TEXT_PRIMARY)
```

### Footer (mehrspaltig)

```python
def add_footer(doc):
    """Footer mit Logo, Standorten und URL."""
    doc.add_paragraph()
    
    table = doc.add_table(rows=1, cols=3)
    table.autofit = False
    remove_table_borders(table)
    
    # Alle Zellen einfärben
    for cell in table.rows[0].cells:
        set_cell_shading(cell, '0D7377')  # Primärfarbe
    
    # Links: Logo/Marke
    cell_left = table.rows[0].cells[0]
    cell_left.width = Inches(1.5)
    p_left = cell_left.paragraphs[0]
    create_run(p_left, "MARKENNAME", font_size=Pt(14), bold=True, color=WHITE)
    
    # Mitte: Standorte
    cell_mid = table.rows[0].cells[1]
    cell_mid.width = Inches(3.5)
    p_mid = cell_mid.paragraphs[0]
    create_run(p_mid, "STANDORT 1 | STANDORT 2 | STANDORT 3", 
               font_size=FOOTER_SIZE, color=WHITE)
    
    # Rechts: URL
    cell_right = table.rows[0].cells[2]
    cell_right.width = Inches(1.3)
    p_right = cell_right.paragraphs[0]
    p_right.alignment = WD_ALIGN_PARAGRAPH.RIGHT
    create_run(p_right, "WEBSITE.AT", font_size=Pt(10), bold=True, color=WHITE)
```

## Vollständiges Beispiel

```python
def create_document():
    doc = Document()
    
    # Seiteneinrichtung
    section = doc.sections[0]
    section.page_width = Cm(21)
    section.page_height = Cm(29.7)
    section.top_margin = Cm(1.5)
    section.bottom_margin = Cm(1.5)
    section.left_margin = Cm(2)
    section.right_margin = Cm(2)
    
    # Seite 1
    add_header(doc)
    add_main_title(doc, "Hauptüberschrift", "Untertitel hier")
    add_body_text(doc, "Einleitungstext...")
    add_section_banner(doc, "Abschnittstitel")
    add_bullet_point(doc, "Fetter Anfang: ", "Normaler Text...")
    add_footer(doc)
    
    # Speichern
    doc.save("output.docx")

if __name__ == "__main__":
    create_document()
```

## Checkliste vor der Implementierung

```
Vor dem Erstellen des Dokuments prüfen:
- [ ] Alle Farben als HEX-Codes vorhanden?
- [ ] Schriftart festgelegt (mit Fallback)?
- [ ] Schriftgrößen für alle Elemente definiert?
- [ ] Logo-Datei vorhanden oder Platzhalter?
- [ ] Layout-Struktur verstanden (Header, Banner, Footer)?
- [ ] Seitenränder und -größe bekannt?
```
