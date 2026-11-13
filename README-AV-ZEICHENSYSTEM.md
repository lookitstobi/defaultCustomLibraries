# AV-Zeichensystem für draw.io

Eine A3-Masterdatei mit 10er-Raster, zwei Vorlagenseiten und zentralen Schriftfeld-Daten. Die bestehenden sechs AV-Libraries bleiben unverändert.

## Neue Dateien
- `AV_MASTER_A3.drawio`: **Signalplan** und **Verkabelungsplan**, A3 quer, 10er-Raster, Schriftfeld unten rechts, vier Ebenen. Die Ebene **01 – Rahmen + Schriftfeld** ist gesperrt.
- `drawio-config.json`: Editor-Voreinstellungen inklusive der sechs separat geladenen Custom-Libraries.
- `STARTLINK.txt`: direkter Startlink, der ein **neues Diagramm aus der Mastervorlage** erzeugt und die Libraries über `clibs` lädt.

## Vor der Nutzung auf fremden PCs
Das Repository ist derzeit **private**. Der Startlink lädt die Bibliotheken und Vorlage über `raw.githubusercontent.com` ohne GitHub-Authentifizierung. Dafür müssen diese Dateien öffentlich abrufbar sein. Niemals private GitHub-Download-Tokens in Links einfügen. Entweder Repository bewusst öffentlich machen oder die Dateien separat öffentlich hosten.

## Starten
1. Nach erfolgter Veröffentlichung Link aus `STARTLINK.txt` öffnen.
2. Der Editor lädt das A3-Master als **neue Zeichnung**, nicht als zu bearbeitende GitHub-Quelldatei.
3. Über **Datei → Eigenschaften → Daten bearbeiten** die Datei-Variablen `projekt`, `kunde`, `ort`, `erstellt`, `geprueft`, `datum`, `revision`, `status`, `plannummer` ändern.
4. Nicht benötigten der beiden Reiter unten löschen bzw. die jeweils passende Seite kopieren. `%page%`, `%pagenumber%` und `%pagecount%` befüllen sich automatisch.
5. Eine Kopie als eigene `.drawio`-Datei speichern.

## Ebenen
- `01 – Rahmen + Schriftfeld (gesperrt)`: Rahmen, Titelblock und Legende, geschützt vor versehentlichem Verschieben.
- `02 – Geräte`: für Geräteblöcke.
- `03 – Verbindungen`: Linien, Signalwege.
- `04 – Beschriftungen`: Kommentare und externe Hinweise.

## Lokale Alternative
Wer GitHub privat lassen möchte, kann `AV_MASTER_A3.drawio` direkt herunterladen und in draw.io öffnen. Das Dokument selbst ist portabel, aber die Custom-Libraries müssen auf jedem Gerät manuell geladen oder lokal konfiguriert werden. Die separate Editor-Konfiguration wird **nicht** in der `.drawio`-Datei gespeichert.

## Editor-Konfiguration
In draw.io **Extras → Konfiguration** öffnen und den Inhalt von `drawio-config.json` einfügen. Das gilt jeweils für den verwendeten Browser bzw. die Desktop-Installation. Der Startlink benötigt diese lokale Einrichtung nicht, sofern die sechs Raw-URLs öffentlich verfügbar sind.

## Hinweise
Das Raster sind 10 draw.io-Zeicheneinheiten, nicht automatisch typografische Punkte. Das Datum im Titelblock ist eine bewusst feste, editierbare Variable. Die Bibliotheken werden aus dem Branch `main` geladen; Änderungen dort sind beim nächsten Laden sichtbar.

## Hinweis zum Startlink
Der Link verwendet bewusst `splash=1`: draw.io benötigt bei `?create=<URL>` den Erstellen-Dialog. Bei `splash=0` kann der Dialog unterdrückt werden und die Zeichenfläche bleibt ohne Dokument leer.

Nach dem Aufruf erscheint die Vorlagenvorschau bzw. der Dialog für eine neue Zeichnung. Dort eine Speicheroption auswählen und **Erstellen** bestätigen. Dadurch wird aus der A3-Mastervorlage eine eigene Datei mit beiden Reitern. Das GitHub-Original bleibt unverändert.

## Asset-Update: Ghielmetti und mittige Anschlusspunkte

- Die sechs vorhandenen Bibliotheken bleiben getrennt. Die Kategorie `06_Patchfelder_Layout.xml` enthält **7 neue Ghielmetti-Elemente**: 1×24 AV, 1×32 AV, 1×48 AV, 2×32 AV, 2×48 (schematisch), 8-Kanal-Ausschnitt und eine 8×8-Patchmatrix (schematisch).
- **Alle 1.478 bisherigen Kreisports** haben genau einen festen Connection Point im Mittelpunkt (`points=[[0.5,0.5,0]]`), `perimeter=centerPerimeter` und `snapToPoint=1`. Richtungsrestriktionen der Ports wurden entfernt, damit sie sich nicht gegenseitig behindern.
- Die Gerätecontainer, die echte Anschlussports besitzen, sind nicht mehr selbst mit Kabeln verbindbar (`connectable=0`), damit nicht irrtümlich an der Gerätekante angeschlossen wird.
- Besondere Ausnahmen: freie Elemente ohne Portkreis behalten ihre bisherigen Anschlussmöglichkeiten. Die Kreuzungspunkte in der schematischen Matrix sind **nur grafische interne Knoten** und keine externen Steckplätze.
- **Wichtige Einschränkung:** Ein einzelner Verbindungspunkt begrenzt in draw.io nicht die Anzahl gleichzeitig angeschlossener Linien. Die Darstellung führt sie auf denselben Mittelpunkt, erzwingt aber nicht „maximal ein Kabel“.
- Ghielmetti-Kanallayouts sind schematische Planbausteine, keine mechanisch exakten Frontplattenzeichnungen. Normalisierung ist bewusst nicht vorausgewählt.
- Bestehende Zeichnungsdateien enthalten weiterhin die bisher eingefügten Shapes. Ersetze diese aus der aktualisierten Library, wenn du die neuen Anschlussregeln brauchst.

## Update: 4-Port-Switch, feste Hausverbindungen, skalierbare Gruppen

- Neuer herstellerneutraler **Netzwerk-Switch 4-Port** in `04_Netzwerk_Steuerung.xml`: vier physische, frei beschriftbare RJ45/Ethernet-Port-Symbole, ohne zusätzlichen fünften Uplink-Port.
- Zwei neue Assets in `06_Patchfelder_Layout.xml`: **Hausverbindung fest · Duplex TX/RX** (zwei gerichtete Signalwege mit kreuzender TX/RX-Beschriftung) und **Hausverbindung fest · Simplex** (ein gerichteter Signalweg), jeweils mit zwei gegenüberliegenden Orts-/Feldkästen und externen Anschlusskreisen. Alle Labels sind editierbar.
- Gruppenstile der vorhandenen Assets: `recursiveResize=1`, `resizable=1`, `rotatable=1`. Damit werden Kinder beim proportionalen Skalieren und Rotieren als Gruppe mitgeführt. Bislang gesperrte Child-Transformations-Flags (`resizable=0`, `rotatable=0`, `movable=0`) wurden in den Container-Assets entfernt; Port-Connection-Points bleiben mittig.
- Beschriftungen in Gerätecontainern: `whiteSpace=wrap;overflow=hidden`, damit überlaufender Text nicht außerhalb der vorgesehenen Felder gezeichnet wird. **Wichtig:** draw.io bietet keine zuverlässige native automatische Verringerung der Schriftgröße abhängig von der Containergröße. Bei extremer Verkleinerung bleibt die Schriftgröße gleich; Text bricht um oder wird abgeschnitten. Schriftgröße bei Bedarf über den Text-Tab anpassen. Beim proportionalen Resize möglichst die Seitenverhältnisse beibehalten.
- Bereits in Zeichnungen eingefügte Assets werden durch Updates an der Library nicht automatisch ersetzt.
