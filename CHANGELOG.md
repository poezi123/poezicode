# Changelog

## v0.3.0 – layout, functions and a command line

**English**

- **Page breaks are automatic now.** Boxes, code blocks and quotes are never cut at the page
  edge, and a heading never stays alone at the bottom of a page – no more manual `@pagebreak`.
- **`@style` sets every spacing**, either with a preset (`compact`, `classic`, `modern`) or value
  by value: paragraph, heading, list, table, image, code, box, formula, drawing, plus `indent`
  for the classic first-line indent and `linespacing`.
- **`@block[fontsize=9]`** sets the font size for a whole block.
- **Automatic typography:** typographic quotes, en and em dashes, ellipsis, and a non-breaking
  space between a number and its unit. `@document[typography=no]` switches it off.
- **Computing inside the document:** `@set{a}{5}` fixes a value, `@function{f(x)}{x^2-2}` declares
  a function (also with several parameters), `@calc{2*a+1}` writes the result. Functions work in
  `@plot` and `@surface` as well.
- **Custom commands** may now have defaults: `#2?default?` fills in when an argument is missing.
- **Images in header and footer** – a logo with a fixed height, `width=`, `height=` or `auto`.
  `@image[height=2cm]` now works everywhere.
- **Numbered equations** with `@document[formulanumbers=yes]`.
- **Text in the 3D editor:** a text body stands in the model like any other shape and appears in
  the PDF. In the 2D editor the cursor jumps straight into the text field after placing text.
- **New command line `poezicode-cli`** – build, render, check and watch documents without a
  window: `build`, `render` (one PNG per page), `check --json` (errors with line and column),
  `watch`, `docs --json`, `prompt`. Made for scripts and AI tools.
- **Fixed:** zooming far into the 2D editor painted black tiles.

**Deutsch**

- **Der Seitenumbruch macht sich von selbst.** Kästen, Codeblöcke und Zitate werden nicht mehr an
  der Blattkante abgeschnitten, und eine Überschrift bleibt nicht allein unten stehen – `@pagebreak`
  von Hand ist nicht mehr nötig.
- **`@style` stellt alle Abstände ein**, wahlweise mit einer Vorlage (`compact`, `classic`,
  `modern`) oder einzeln: paragraph, heading, list, table, image, code, box, formula, drawing, dazu
  `indent` für den klassischen Absatzeinzug und `linespacing`.
- **`@block[fontsize=9]`** setzt die Schriftgröße für einen ganzen Block.
- **Automatische Typografie:** typografische Anführungszeichen, Gedankenstriche,
  Auslassungspunkte und ein geschütztes Leerzeichen zwischen Zahl und Einheit.
  `@document[typography=no]` schaltet es ab.
- **Rechnen im Dokument:** `@set{a}{5}` legt eine Größe fest, `@function{f(x)}{x^2-2}` eine
  Funktion (auch mit mehreren Parametern), `@calc{2*a+1}` schreibt das Ergebnis. Funktionen gelten
  auch in `@plot` und `@surface`.
- **Eigene Befehle** dürfen Vorgaben haben: `#2?Vorgabe?` springt ein, wenn ein Argument fehlt.
- **Bilder in Kopf- und Fußzeile** – ein Logo mit fester Höhe, `width=`, `height=` oder `auto`.
  `@image[height=2cm]` geht jetzt überall.
- **Nummerierte Gleichungen** mit `@document[formulanumbers=yes]`.
- **Text im 3D-Editor:** Ein Textkörper steht wie jeder andere Körper im Modell und erscheint im
  PDF. Im 2D-Editor springt der Schreibcursor nach dem Setzen sofort ins Textfeld.
- **Neue Befehlszeile `poezicode-cli`** – Dokumente bauen, ansehen, prüfen und beobachten, ganz
  ohne Fenster: `build`, `render` (je Seite ein PNG), `check --json` (Fehler mit Zeile und Spalte),
  `watch`, `docs --json`, `prompt`. Für Skripte und KI-Werkzeuge gedacht.
- **Behoben:** Beim starken Hineinzoomen im 2D-Editor erschienen schwarze Felder.

## v0.2.0 – first public release / erste öffentliche Version

**English**

- Editor with syntax highlighting, suggestions after `@`, error messages with hints and a
  live PDF preview.
- The PoeziCode language: document setup, headings with automatic numbering, table of
  contents, text formatting, lists, tables, boxes, quotes, code blocks, columns, images,
  links, header and footer, custom commands.
- Math typesetting: fractions, roots, sums, integrals, limits, matrices, case distinctions.
- Drawings (`@drawing`), function graphs, 3D models (STL, OBJ) and function surfaces.
- CAD editor for 3D models and 2D drawings.
- Layout helpers: `@block` for spacing and indentation, `@newln`, alignment.
- Locate: click in the PDF to jump to the source.
- Print preview in colour or black & white, PDF export.
- Docs window with every command, copyable AI prompt.
- German and English interface.
- Packages for Windows 10/11 (installer and ZIP), Arch Linux, Debian/Ubuntu and a universal tar.gz.

**Deutsch**

- Editor mit Syntaxhervorhebung, Vorschlägen nach `@`, Fehlermeldungen mit Hinweisen und
  Live-PDF-Vorschau.
- Die Sprache PoeziCode: Dokumenteinstellungen, automatisch nummerierte Überschriften,
  Inhaltsverzeichnis, Textformatierung, Listen, Tabellen, Kästen, Zitate, Codeblöcke,
  Spalten, Bilder, Links, Kopf- und Fußzeile, eigene Befehle.
- Formelsatz: Brüche, Wurzeln, Summen, Integrale, Grenzwerte, Matrizen, Fallunterscheidungen.
- Zeichnungen (`@drawing`), Funktionsgraphen, 3D-Modelle (STL, OBJ) und Funktionsflächen.
- CAD-Editor für 3D-Modelle und 2D-Zeichnungen.
- Layout-Helfer: `@block` für Abstände und Einrückung, `@newln`, Ausrichtung.
- Lupe: im PDF klicken, um zur Stelle im Quelltext zu springen.
- Druckansicht in Farbe oder Schwarz-weiß, PDF-Export.
- Docs-Fenster mit allen Befehlen, kopierbarer KI-Prompt.
- Oberfläche auf Deutsch und Englisch.
- Pakete für Windows 10/11 (Installer und ZIP), Arch Linux, Debian/Ubuntu und ein universelles tar.gz.
