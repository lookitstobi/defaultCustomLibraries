# Swimlane-Test v2: Kantenverankerte Ports und gemeinsame Farbdaten

Neue, separate Testassets. Die produktiven sechs Custom-Libraries und die vorherige Swimlane-Testversion bleiben unverändert.

## 1. Ports und Beschriftungen an Kanten

Jeder bisherige Anschluss und sein Text stehen nun auf **relativer Geometrie** mit der gleichen bisherigen Höhe. Links: `relative=1, x=0`, rechts: `relative=1, x=1`, plus fester Pixel-Offset. Die Anschlusskreise behalten ihre Größe und ihren Mittelpunkt-Connection-Point. `recursiveResize=0` am Swimlane-Container verhindert eine proportionale Verteilung der Child-Koordinaten beim horizontalen Resize. Damit bleiben die rechten Anschlusspositionen an der rechten Außenkante, die linken an der linken. Die Port-Reihen bleiben in festem Abstand zur Oberseite. Wenn der Container niedriger gemacht wird als die nötige Portfläche, können Ports überstehen.

## 2. Neutraler, fester Body und hellgraue Labels

- **Lane-/Bodyfarbe:** `light-dark(#E8E8E8,#191919)` – hellgrau im Light Mode, dunkelgrau im Dark Mode.
- **Beschriftungen der Children:** `light-dark(#333333,#C8C8C8)` – dunkelgrau im Light Mode, hellgrau im Dark Mode.
- Beide Werte stehen jetzt direkt im Style und werden **nicht mehr durch Datenfelder gesteuert**.
- Über **Daten bearbeiten** sind weiterhin `avHeader`, `avOutline` und `avTitle` veränderbar. Headerfüllung und Rahmen können damit Akzentfarben behalten.
- Die Anschlusskreise behalten ihre Signalfarben (Eingang türkis, Ausgang blau).
- Achtung: Ein gewöhnlicher Farb-Preset-Klick auf den Parent färbt nicht automatisch alle Child-Elemente um. Durch die festen neutralen Body-/Textwerte sollte sich die Farbwirkung aber deutlich ruhiger verhalten.

## 3. Test

1. `00_TEST_Swimlane_v2.xml` in draw.io als Library laden (oder `TEST_Swimlane_v2.drawio` öffnen).
2. Breite des Automixers vergrößern: rechte Ports und ihre Labels sollen rechts bleiben; linke Ports und Beschriftungen links.
3. Container verschieben und drehen, Kabelverbindungen zu den Anschlusskreisen prüfen.
4. Zwischen Light und Dark Mode wechseln: Der Body soll von `#E8E8E8` zu `#191919` wechseln und die Child-Schrift von `#333333` zu `#C8C8C8`. Header- und Rahmen-Akzent bleiben separat editierbar.
5. Bei Bedarf `avHeader` und `avOutline` unter **Daten bearbeiten** anpassen. Die Child-Portfarben bleiben absichtlich nach Signalrichtung codiert.

Kein automatisches Verkleinern der Schrift bei schmalen Containern. Header- und Porttexte können bei sehr geringer Breite umbrechen oder abgeschnitten werden.
