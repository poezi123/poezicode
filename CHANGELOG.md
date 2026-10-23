# Changelog

## v0.4.4 – formulas on parts, and what a full test run turned up

**English**

- **A part may be named with a formula:** `@part[coil, rot=270, name=$X_L$]{0,0}` prints X with a
  small L, `value=$1@text{ kΩ}$` sets the unit properly, `name=@bold{M1}` makes it bold – in
  `@circuit`, in `@drawing` and for `@footprint` on a board. A plain `name=R1` stays plain text.
- **The unit behind the `=` reaches the document:** `I := U/R = mA` stands in milliamperes on the
  sheet – and now in the typeset document as well, matrices included. Until now the document fell
  back to the base unit.
- **`@calc` may stand inside a formula:** `$$ R = @calc{U/I} @text{ Ω} $$` sets the computed number
  in the middle of the typeset formula. Until now every sheet from PoeziMath that ended a line
  without a unit in `=` produced an error here.
- **A formula in the document is an equation again.** `$f = 1/T$` kept only the `f`: the right-hand
  side was read as a request for a result in tesla, the way PoeziMath does it. A document never asks
  for results, so the whole equation is set – this hit every formula whose right side began with a
  number and a unit name.
- **PoeziMath writes `@set` and `@calc` only where the document can follow.** A calculation that
  builds on a quantity with a unit now goes into the document as a formula instead of referring to a
  name the document does not know (`@set{Q}{XL/R}` → *unknown name*).
- **The footprints have clear names** – `electrolytic_large`, `resistor_power`, `inductor_radial`,
  `relay_power`, `testpoint`. The names used so far keep working.

**Deutsch**

- **Ein Bauteil darf mit einer Formel benannt werden:** `@part[coil, rot=270, name=$X_L$]{0,0}`
  schreibt X mit kleinem L, `value=$1@text{ kΩ}$` setzt die Einheit richtig, `name=@bold{M1}` macht
  es fett – in `@circuit`, in `@drawing` und bei `@footprint` auf der Platine. Ein einfaches
  `name=R1` bleibt einfacher Text.
- **Die Einheit hinter dem `=` gilt auch im Dokument:** `I := U/R = mA` steht im Blatt in
  Milliampere – und jetzt auch im gesetzten Dokument, Matrizen eingeschlossen. Bisher fiel das
  Dokument auf die Basiseinheit zurück.
- **`@calc` darf in einer Formel stehen:** `$$ R = @calc{U/I} @text{ Ω} $$` setzt die gerechnete Zahl
  mitten in die Formel. Bisher gab jedes Blatt aus PoeziMath, das eine Zeile ohne Einheit mit `=`
  abschloss, hier eine Fehlermeldung.
- **Eine Formel im Dokument ist wieder eine Gleichung.** Von `$f = 1/T$` blieb nur das `f` übrig: Die
  rechte Seite wurde als Wunsch nach einem Ergebnis in Tesla gelesen, so wie es PoeziMath macht. Ein
  Dokument fragt nie nach Ergebnissen, also steht die ganze Gleichung da – das betraf jede Formel,
  deren rechte Seite mit einer Zahl und einem Einheitennamen begann.
- **PoeziMath schreibt `@set` und `@calc` nur, wo das Dokument mitkommt.** Eine Rechnung, die auf
  einer Größe mit Einheit aufbaut, steht jetzt als Formel im Dokument, statt sich auf einen Namen zu
  berufen, den das Dokument nicht kennt (`@set{Q}{XL/R}` → *Unbekannter Name*).
- **Die Bauformen heißen klar** – `electrolytic_large`, `resistor_power`, `inductor_radial`,
  `relay_power`, `testpoint`. Die bisherigen Namen gelten weiter.

## v0.4.3 – PoeziMath for electrical engineering, formulas as you type them, and large files

**English**

- **Formulas the way you type them:** if there is no `@` command in `$…$`, the formula is set –
  `$n = U/sqrt(2*pi*c_r*M) - sum(R_a)/c_r$` becomes a fraction with a root, a sum sign and
  subscripted names. The same everywhere: in a sentence, displayed, in `@block`, in `@columns` and
  in drawing labels. With `@` commands everything stays exactly as written.
- **PoeziMath trimmed for electrical engineering:** roots of units (`sqrt(L*C)` is a time), composite
  units after the `=` (`= V/m`, `= ohm*mm^2/m`), constants with their unit (c0, eps0, mu0, q0, g),
  angles always in the setting of the sheet, and more than 30 new units from `Ah` to `rpm`.
- **`solve` rearranges:** write the formula, a comma and the variable you want –
  `solve(f_R = 1/(2*pi*sqrt(L*C)), L)`. Roots and powers are rearranged, and where the unknown
  appears more than once it is searched for with the right unit. While you type, the preview below
  shows what the document will look like.
- **A formulary at a click (Ctrl+F):** 101 formulas by subject – electrical engineering from the
  basic laws through Kirchhoff, power, capacitor and coil, alternating current, three-phase current
  and the magnetic field to electronics, plus physics: mechanics, energy, heat, oscillations, optics.
  With a search.
- **Help for PoeziMath**, with a search of its own: every key combination, the units, the solve
  blocks and the way into the document.
- **Large files:** from 60 kB on, only a window of 400 lines (adjustable in the settings) is really a
  text field, and it follows the caret. Nothing of this can be seen – same colours, same background,
  suggestions and the magnifier from the preview work as usual. A 200 kB document types about five
  times more smoothly than in a single text field.
- **Automatic formatting that earns its name:** it wraps long lines of prose (without ever splitting
  a formula or a brace), gives closing braces a line of their own, throws out empty blocks, columns
  and pages and brings figures to the same width. The typeset document stays identical, page for
  page.
- **Figures no longer run out of the type area:** in `@columns` and in indented blocks a drawing, a
  circuit or a 3D model is scaled down to the width available instead of being cut off.

**Deutsch**

- **Formeln so, wie man sie tippt:** Steht in `$…$` kein `@`-Befehl, wird die Formel gesetzt –
  `$n = U/sqrt(2*pi*c_r*M) - sum(R_a)/c_r$` ergibt Bruch, Wurzel, Summenzeichen und tiefgestellte
  Namen. Überall gleich: im Satz, abgesetzt, in `@block`, in `@columns` und in
  Zeichnungsbeschriftungen. Mit `@`-Befehlen bleibt alles, wie es geschrieben steht.
- **PoeziMath auf die Elektrotechnik getrimmt:** Wurzeln aus Einheiten (`sqrt(L*C)` ist eine Zeit),
  zusammengesetzte Einheiten hinter dem `=` (`= V/m`, `= ohm*mm^2/m`), Konstanten mit Einheit (c0,
  eps0, mu0, q0, g), Winkel immer in der Einstellung des Blattes und über 30 neue Einheiten von `Ah`
  bis `rpm`.
- **`solve` stellt um:** einfach die Formel, ein Komma und die gesuchte Größe –
  `solve(f_R = 1/(2*pi*sqrt(L*C)), L)`. Wurzeln und Potenzen werden umgestellt, und kommt die
  Unbekannte mehrfach vor, wird mit der richtigen Einheit gesucht. Beim Tippen zeigt die Vorschau
  darunter, wie es im Dokument aussehen wird.
- **Formelsammlung auf Knopfdruck (Strg+F):** 101 Formeln nach Gebieten – Elektrotechnik von den
  Grundgesetzen über Kirchhoff, Leistung, Kondensator und Spule, Wechselstrom, Drehstrom und
  Magnetfeld bis zur Elektronik, dazu Physik: Mechanik, Energie, Wärme, Schwingungen, Optik. Mit
  Suche.
- **Hilfe für PoeziMath**, mit eigener Suche: alle Tastenkombinationen, die Einheiten, die
  Lösungsblöcke und der Weg ins Dokument.
- **Große Dateien:** Ab 60 kB ist nur noch ein Fenster von 400 Zeilen (in den Einstellungen
  änderbar) wirklich ein Textfeld, und es wandert mit dem Cursor mit. Zu sehen ist davon nichts –
  gleiche Farben, gleicher Hintergrund, Vorschläge und die Lupe aus der Vorschau arbeiten wie
  gewohnt. Eine 200-kB-Datei tippt sich damit rund fünfmal flüssiger als in einem einzigen Textfeld.
- **Automatisch formatieren, das den Namen verdient:** Es bricht lange Textzeilen um (ohne je eine
  Formel oder eine Klammer zu trennen), gibt schließenden Klammern eine eigene Zeile, wirft leere
  Blöcke, Spalten und Seiten hinaus und bringt Abbildungen auf dieselbe Breite. Das gesetzte Dokument
  bleibt dabei Seite für Seite identisch.
- **Zeichnungen laufen nicht mehr aus dem Satzspiegel:** In `@columns` und in eingerückten Blöcken
  werden Zeichnung, Schaltung und 3D-Modell auf die verfügbare Breite verkleinert statt
  abgeschnitten.

## v0.4.2 – phasors, subscripts and the way back from the document

**English**

- **The equals sign decides:** a result stands only where a `=` was typed in PoeziMath, a definition
  included (`I := U/R =`). Without it the document shows exactly the formula you wrote and nothing
  else.
- **Phasors for electrical engineering:** `100 + 50∠90°` – the angle sign is typed as `/_` or
  fetched with Ctrl+W. A result you click can be switched on the right between `a + bj` and
  `r ∠ φ`, and for the whole sheet in its settings. In the document: `@angle`, `@degree`.
- **Subscripts with Ctrl+−:** `I_2` stands as I₂, `v_max` as v with a small “max”. Digits at the end
  of a name drop down by themselves – `R1` becomes R₁, on the sheet as in the document.
- **Several names for the same value:** `Z_1 := Z_2 := Z_3 := 50∠0°`, `Z_1 := 50∠0° := Z_2` and
  `R_a, R_b := 100*ohm` define every quantity named; the document then reads
  `Z_1 = Z_2 = Z_3 = 50∠0°`.
- **Back from the document into the worksheet:** select your formulas in the source and open
  PoeziMath – they are there again as a calculation, with definitions, fractions, units, matrices and
  headings. The sheet is not overwritten; the lines are added below it.
- **“Format automatically” means the document:** spacing is collected, empty blocks and empty pages
  go away, a page break behind a heading moves in front of it, and figures get the same width and
  alignment – the source is still tidied up as well.

**Deutsch**

- **Das Gleichheitszeichen entscheidet:** Ein Ergebnis steht nur dort, wo in PoeziMath ein `=`
  getippt wurde – auch hinter einer Festlegung (`I := U/R =`). Ohne `=` steht im Dokument genau die
  Formel, die du geschrieben hast, und sonst nichts.
- **Zeiger für die Elektrotechnik:** `100 + 50∠90°` – das Winkelzeichen tippt man als `/_` oder holt
  es mit Strg+W. Ein angeklicktes Ergebnis lässt sich rechts zwischen `a + bj` und `r ∠ φ`
  umschalten, fürs ganze Blatt auch in den Einstellungen. Im Dokument: `@angle`, `@degree`.
- **Tiefgestellt mit Strg+−:** `I_2` steht als I₂, `v_max` als v mit kleinem „max“. Ziffern am Ende
  eines Namens rutschen von selbst nach unten – `R1` wird R₁, im Blatt wie im Dokument.
- **Mehrere Namen auf denselben Wert:** `Z_1 := Z_2 := Z_3 := 50∠0°`, `Z_1 := 50∠0° := Z_2` und
  `R_a, R_b := 100*ohm` legen alle genannten Größen gemeinsam fest; im Dokument steht dann
  `Z_1 = Z_2 = Z_3 = 50∠0°`.
- **Aus dem Dokument zurück ins Rechenblatt:** Markier im Quelltext deine Formeln und öffne
  PoeziMath – sie stehen wieder als Rechnung da, samt Festlegungen, Brüchen, Einheiten, Matrizen und
  Überschriften. Das Blatt wird dabei nicht überschrieben, die Zeilen kommen darunter.
- **„Automatisch formatieren“ meint das Dokument:** Abstände werden zusammengefasst, leere Blöcke und
  leere Seiten entfernt, ein Seitenumbruch hinter einer Überschrift wandert davor, und Abbildungen
  bekommen dieselbe Breite und Ausrichtung – der Quelltext wird weiterhin mit aufgeräumt.

## v0.4.0 – circuits, automatic formatting and finer spacing

**English**

- **New circuit editor** – a third tab in the CAD editor next to 3D and 2D, with IEC/DIN symbols for
  electrical engineering (resistor, potentiometer, capacitor, electrolytic, coil, diode, LED, Zener
  diode, lamp, fuse, switch, push-button, voltage and current source, battery, ground, motor,
  voltmeter, ammeter) and for logic (AND, OR, XOR, NOT, NAND, NOR, inputs and outputs). Parts can be
  turned, mirrored, named and given a value; wires and junctions connect them.
- **Board mode** inside the same tab: footprints in millimetres (resistor, diode, LED, capacitor,
  electrolytic, TO-92, DIP-8/14/16, pin headers, screw terminal, mounting hole), copper tracks on
  both sides, vias and the board itself – written as `@pcb[board=50x30]{ @footprint[dip14]{25,15}
  @track[width=0.6]{…} @via{…} }`.
- **Frame rate display** in the drawing board, so you can see when a drawing gets heavy.
- **Connections are magnetic:** with the wire tool every pin, pad and wire end shows as a small ring,
  and the wire snaps onto it – no more aiming.
- **Wires run at right angles** and turn a corner by themselves; the space bar flips the corner.
  Where a wire ends on another wire, the junction dot appears on its own.
- **Truth tables:** `@circuit[truthtable]{…}` works out what a logic circuit does and prints the table
  under the drawing. The editor has a switch for it.
- **Circuit check:** open pins, duplicate designations, wires ending nowhere and two outputs on one
  wire are listed at a click.
- **From schematic to board:** one button puts the parts of the schematic onto the board, keeping
  their names; thin guide lines show which pads still need connecting. Tracks run at 45°, clearances
  can be checked, and `@pcb[ground]` fills the free areas with copper.
- **A worksheet in the CAD editor** – a fourth tab that works like a sheet of paper with a
  calculator: `a := 5` sets a value, `f(x) := x^2 - 3` a function, every other line is worked out and
  the result stands beside it. One click puts the whole sheet into the document as `@set`,
  `@function` and formulas with `@calc`, so the numbers stay live.
- **A button for automatic formatting** in the toolbar, next to the print preview.
- **`@block` may now move content outwards**: `left=-8mm` or `right=-1cm` shifts a paragraph past the
  edge – inside `@columns` that is how you move something left and right.
- **Turned dimension figures:** `@dimension[turn]` lays the number along the dimension line,
  `[turn=30]` turns it by an angle of your own; in the editor there is a switch for it.
- **Your own parts:** draw a symbol, select it and save it – points (`@point`) become its pins. It
  then sits in the parts bar and works in documents as `@part[name]{x,y}`, with rotation, size and
  magnetic pins like any built-in part.
- **Holes and chamfers in 3D:** a box or a cylinder can have a through hole (a cylinder with a hole
  becomes a tube) and broken edges – both in millimetres in the inspector.
- **The board in 3D:** a switch in the circuit tab shows the finished board as a solid – green
  substrate, copper, gold pads and the real parts on top. In a document: `@pcb[board=50x30, 3d]`,
  turned with `yaw=` and tilted with `pitch=`.
- **Every part can be resized** – `scale=1.5` on `@part` and `@footprint`, a size field in the
  inspector, and the plus and minus keys on the selection.
- **Dimensions** in drawings: `@dimension{0,0}{6,0}{60 mm}` with extension lines, arrows and the
  measured length when no text is given.
- **Several elements at once:** drag a frame to select, Ctrl+click to add single ones, then move,
  copy (Ctrl+C/V), duplicate (Ctrl+D), delete, mirror (Ctrl+M), align and distribute them evenly.
- **Much faster typing in large documents.** The syntax colouring used to rebuild the whole file on
  every keystroke; now only the visible part is coloured. In a 185 KB document a keystroke went from
  about three seconds to a fifth of a second.
- **`@circuit{…}`** puts such a diagram into a document: `@part[resistor, name=R1, value=10k]{0,0}`,
  `@wire{0,0 | 3,0}`, `@junction{3,0}`. `@part` also works inside `@drawing`.
- **Automatic formatting** – **Ctrl+Shift+F** in the editor, `poezicode-cli format file.pzc` in the
  command line. It tidies the source *and* repairs the usual mistakes: chains of `@newln` become
  paragraphs, needless `@pagebreak` go away, blocks get indented, options and table rows are evened
  out. Written for documents an AI wrote for you.
- **Header and footer spacing** is adjustable: `@style[headertop=1.5cm, headergap=0.8cm,
  footerbottom=1.5cm, footergap=0.6cm]`.
- **Font sizes in drawings**: `@label[size=12]`, `@point[size=9]` and `@drawing[labelsize=8]` for the
  axis and grid numbers. In the 3D editor a text body can have a fixed size in points.
- **Snapping can be switched off** in the 2D editor, and the grid step is now free to choose. Shift
  turns the setting around while you draw.
- **PoeziMath** – a worksheet like Mathcad in a window of its own, opened from the toolbar. A blue
  crosshair instead of a text field, formulas typeset while you type, units, fractions, matrices,
  ranges, solve blocks (Given … Find), derivative, integral, sums and plots. One click turns the
  whole sheet into PoeziCode in your document; regions snap to a grid, and the border of a region
  moves or removes it.
- **Fonts for the document:** `@document[font=serif|sans|latex|mono]` – `latex` is Computer Modern,
  the font from LaTeX.
- **`@left` and `@right` take everything with them:** displayed formulas, images, drawings, circuits
  and 3D models follow the alignment instead of staying in the middle.
- **Black-and-white printing really is black and white:** colours, drawings and pictures become grey
  while the document is set, so no printer driver can leave a tint behind.
- **Parts can be searched** in the circuit and board palettes, and a part may be given any angle you
  like instead of steps of 90°.
- **Faster:** large documents (200 kB) type smoothly, the preview rasterizes only the pages you can
  see, and the typesetter stays resident instead of starting again on every keystroke.

**Deutsch**

- **Neuer Schaltungs-Editor** – ein dritter Reiter im CAD-Editor neben 3D und 2D, mit Schaltzeichen
  nach IEC/DIN für die Elektrotechnik (Widerstand, Poti, Kondensator, Elko, Spule, Diode, LED,
  Z-Diode, Lampe, Sicherung, Schalter, Taster, Spannungs- und Stromquelle, Batterie, Masse, Motor,
  Voltmeter, Amperemeter) und für die Digitaltechnik (UND, ODER, Exklusiv-ODER, NICHT, NAND, NOR,
  Ein- und Ausgänge). Bauteile lassen sich drehen, spiegeln, benennen und mit einem Wert versehen,
  Leitungen und Verbindungspunkte verbinden sie.
- **Platinen-Modus** im selben Reiter: Bauformen in Millimetern (Widerstand, Diode, LED,
  Kondensator, Elko, TO-92, DIP-8/14/16, Stiftleisten, Klemme, Bohrung), Leiterbahnen auf beiden
  Seiten, Durchkontaktierungen und die Platine selbst – im Dokument als `@pcb[board=50x30]{
  @footprint[dip14]{25,15} @track[width=0.6]{…} @via{…} }`.
- **FPS-Anzeige** im Zeichenbrett, damit man sieht, wann eine Zeichnung schwer wird.
- **Anschlüsse sind magnetisch:** Mit dem Leitungs-Werkzeug zeigt sich jeder Pin, jedes Lötauge und
  jedes Leitungsende als kleiner Ring, und die Leitung rastet darauf ein – kein Zielen mehr.
- **Leitungen laufen im rechten Winkel** und machen die Ecke von selbst; die Leertaste dreht sie um.
  Endet eine Leitung auf einer anderen, entsteht der Verbindungspunkt automatisch.
- **Wahrheitstabellen:** `@circuit[truthtable]{…}` rechnet aus, was eine Logikschaltung tut, und
  setzt die Tabelle unter die Zeichnung. Im Editor gibt es dafür einen Schalter.
- **Schaltungsprüfung:** offene Anschlüsse, doppelte Bezeichnungen, Leitungen ins Nichts und zwei
  Ausgänge auf einer Leitung werden auf Knopfdruck aufgelistet.
- **Vom Schaltplan auf die Platine:** Ein Knopf setzt die Bauteile mit ihren Namen auf die Platine,
  dünne Luftlinien zeigen, was noch zu verbinden ist. Leiterbahnen laufen in 45°, die Abstände lassen
  sich prüfen, und `@pcb[ground]` füllt die freien Flächen mit Kupfer.
- **Rechenblatt im CAD-Editor** – ein vierter Reiter, der wie ein Blatt Papier mit Taschenrechner
  funktioniert: `a := 5` legt eine Größe fest, `f(x) := x^2 - 3` eine Funktion, jede andere Zeile
  wird ausgerechnet und das Ergebnis steht daneben. Ein Klick legt das ganze Blatt als `@set`,
  `@function` und Formeln mit `@calc` ins Dokument – die Zahlen bleiben also lebendig.
- **Knopf für die automatische Formatierung** in der Werkzeugleiste, neben der Druckansicht.
- **`@block` schiebt jetzt auch nach außen**: `left=-8mm` oder `right=-1cm` rückt einen Absatz über
  den Rand hinaus – in `@columns` verschiebt man damit etwas nach links und rechts.
- **Gedrehte Maßzahlen:** `@dimension[turn]` legt die Zahl längs der Maßlinie, `[turn=30]` dreht sie
  um einen eigenen Winkel; im Editor gibt es dafür einen Schalter.
- **Eigene Bauteile:** Ein Symbol zeichnen, auswählen und speichern – Punkte (`@point`) werden zu
  seinen Anschlüssen. Danach steht es in der Bauteilleiste und gilt im Dokument als
  `@part[name]{x,y}`, mit Drehung, Größe und magnetischen Anschlüssen wie jedes eingebaute Bauteil.
- **Bohrungen und Fasen im 3D-Editor:** Quader und Zylinder bekommen eine durchgehende Bohrung (aus
  dem Zylinder wird ein Rohr) und gebrochene Kanten – beides in Millimetern im Inspektor.
- **Die Platine in 3D:** Ein Umschalter im Schaltungs-Reiter zeigt die fertige Platine als Körper –
  grünes Material, Kupfer, goldene Lötaugen und die echten Bauteile darauf. Im Dokument:
  `@pcb[board=50x30, 3d]`, mit `yaw=` gedreht und `pitch=` geneigt.
- **Jedes Bauteil lässt sich in der Größe ändern** – `scale=1.5` bei `@part` und `@footprint`, ein
  Größenfeld im Inspektor und die Tasten Plus und Minus auf der Auswahl.
- **Bemaßung** in Zeichnungen: `@dimension{0,0}{6,0}{60 mm}` mit Maßhilfslinien, Pfeilen und – ohne
  eigenen Text – der gemessenen Länge.
- **Mehrere Teile auf einmal:** Auswahlrahmen ziehen, mit Strg+Klick einzelne dazunehmen, dann
  verschieben, kopieren (Strg+C/V), verdoppeln (Strg+D), löschen, spiegeln (Strg+M), ausrichten und
  gleichmäßig verteilen.
- **Tippen in großen Dokumenten ist viel schneller.** Die Syntaxfarben wurden bisher bei jedem
  Tastendruck für das ganze Dokument neu gebaut; jetzt nur noch für den sichtbaren Teil. In einer
  185 KB großen Datei dauerte ein Tastendruck vorher rund drei Sekunden, jetzt eine Fünftelsekunde.
- **`@circuit{…}`** bringt so eine Schaltung ins Dokument: `@part[resistor, name=R1, value=10k]{0,0}`,
  `@wire{0,0 | 3,0}`, `@junction{3,0}`. `@part` geht auch in `@drawing`.
- **Automatische Formatierung** – **Strg+Umschalt+F** im Editor, `poezicode-cli format datei.pzc` in
  der Befehlszeile. Sie räumt den Quelltext auf *und* repariert die üblichen Fehler: Ketten aus
  `@newln` werden zu Absätzen, überflüssige `@pagebreak` fallen weg, Blöcke werden eingerückt,
  Optionen und Tabellenzeilen vereinheitlicht. Gedacht für Dokumente, die eine KI geschrieben hat.
- **Abstände der Kopf- und Fußzeile** sind einstellbar: `@style[headertop=1.5cm, headergap=0.8cm,
  footerbottom=1.5cm, footergap=0.6cm]`.
- **Schriftgrößen in Zeichnungen**: `@label[size=12]`, `@point[size=9]` und `@drawing[labelsize=8]`
  für die Zahlen an den Achsen. Im 3D-Editor bekommt ein Textkörper eine feste Größe in Punkt.
- **Einrasten lässt sich abschalten** im 2D-Editor, und die Rasterweite ist frei wählbar. Umschalt
  dreht die Einstellung beim Zeichnen jeweils um.
- **PoeziMath** – ein Rechenblatt wie Mathcad in einem eigenen Fenster, aus der Werkzeugleiste zu
  öffnen. Ein blaues Kreuz statt eines Textfelds, gesetzte Formeln schon beim Tippen, Einheiten,
  Brüche, Matrizen, Bereiche, Lösungsblöcke (Given … Find), Ableitung, Integral, Summen und
  Diagramme. Auf Knopfdruck wird das ganze Blatt zu PoeziCode im Dokument; die Bereiche rasten ein,
  und an der Randlinie lässt sich ein Bereich verschieben oder entfernen.
- **Schriftarten im Dokument:** `@document[font=serif|sans|latex|mono]` – `latex` ist Computer
  Modern, die Schrift aus LaTeX.
- **`@left` und `@right` nehmen alles mit:** abgesetzte Formeln, Bilder, Zeichnungen, Schaltungen und
  3D-Modelle folgen der Ausrichtung statt in der Mitte zu bleiben.
- **Schwarz-weiß drucken** heißt wirklich schwarz-weiß: Farben, Zeichnungen und Bilder werden schon
  beim Setzen zu Grautönen, da kann kein Druckertreiber mehr einen Farbstich übrig lassen.
- **Bauteile lassen sich suchen** in den Leisten für Schaltung und Platine, und ein Teil bekommt
  jeden Winkel, den man eintippt, statt nur Schritte von 90°.
- **Schneller:** große Dokumente (200 kB) schreiben sich flüssig, die Vorschau rastert nur noch die
  Seiten, die man sieht, und der Setzer bleibt im Hintergrund wohnen statt bei jedem Tastendruck neu
  zu starten.

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
