# Swimlane-Test v2: Kantenverankerte Ports und gemeinsame Farbdaten

Neue, separate Testassets. Die produktiven sechs Custom-Libraries und die vorherige Swimlane-Testversion bleiben unverändert.

## 1. Ports und Beschriftungen an Kanten

Jeder bisherige Anschluss und sein Text stehen nun auf **relativer Geometrie** mit der gleichen bisherigen Höhe. Links: `relative=1, x=0`, rechts: `relative=1, x=1`, plus fester Pixel-Offset. Die Anschlusskreise behalten ihre Größe und ihren Mittelpunkt-Connection-Point. `recursiveResize=0` am Swimlane-Container verhindert eine proportionale Verteilung der Child-Koordinaten beim horizontalen Resize. Damit bleiben die rechten Anschlusspositionen an der rechten Außenkante, die linken an der linken. Die Port-Reihen bleiben in festem Abstand zur Oberseite. Wenn der Container niedriger gemacht wird als die nötige Portfläche, können Ports überstehen.

## 2. Farbinformationen zentral am Container

Der Parent ist jetzt ein `UserObject` mit folgenden Feldern (im draw.io-Dialog **Bearbeiten → Daten bearbeiten**):

- `avHeader` – Header-Füllfarbe
- `avBody` – Swimlane-Bodyfarbe
- `avOutline` – Rahmenfarbe
- `avText` – Farbe **aller Child-Beschriftungen**
- `avTitle` – Titeltextfarbe

Diese Werte werden mit `stylePlaceholders=1` in den Style-Feldern eingesetzt. Die fünf Farben sind in einer Stelle (Containerdaten) zentral editierbar; keine Einzelbearbeitung der Texte nötig. Aktuell ist der blaue Audio-Stil vorbelegt.

**Grenze:** Farb-Presets in der normalen Style-Palette ändern nicht automatisch die Datenfelder `avBody` oder `avText`. Ein Farb-Preset kann die gesamte mehrteilige Palette daher nicht in einem Klick umrechnen. Dafür wäre ein draw.io-Plugin oder ein gesonderter Theme-Wechsel nötig.

## 3. Test

1. `00_TEST_Swimlane_v2.xml` in draw.io als Library laden (oder `TEST_Swimlane_v2.drawio` öffnen).
2. Breite des Automixers vergrößern: rechte Ports und ihre Labels sollen rechts bleiben; linke Ports und Beschriftungen links.
3. Container verschieben und drehen, Kabelverbindungen zu den Anschlusskreisen prüfen.
4. Beim Parent **Daten bearbeiten** öffnen und `avBody` auf `#171C24`, `avText` auf `#AFC9FA` setzen – so kannst du eine dunkle Bodyfarbe mit heller Beschriftung testen.
5. Bei Bedarf `avHeader` und `avOutline` ändern. Die Child-Portfarben bleiben absichtlich nach Signalrichtung codiert.

Kein automatisches Verkleinern der Schrift bei schmalen Containern. Header- und Porttexte können bei sehr geringer Breite umbrechen oder abgeschnitten werden.
