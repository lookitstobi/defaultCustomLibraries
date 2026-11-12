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
