# Swimlane-Strukturtest für die AV-Library

Die produktiven sechs Bibliotheken sind bewusst unverändert.
Diese Datei enthält zwei Test-Assets: Automixer 8×2 und DI-Box Stereo.

Was geändert wurde:
- Gerät ist eine einzige Swimlane mit eigenem Header und direktem Titeltext.
- Headerfarbe über fillColor, Body über swimlaneFillColor.
- Beide früheren Header-Children sind entfernt.
- Bestehende 14 Port-Children sind unverändert, samt Mittelpunkt-Connection-Points.
- Resizable, rotatable und recursiveResize sind eingeschaltet.

Test in draw.io:
1. 00_TEST_Swimlane.xml als eigene Bibliothek importieren oder TEST_Swimlane.drawio öffnen.
2. Geräte verkleinern, vergrößern, drehen und die Ports verbinden.
3. Headerfarbe im Style-Panel ändern und separate Lane-Farbe prüfen.
4. Titel durch Doppelklick ändern.

Bekannte Grenze: Es gibt keine native automatische Verringerung der Schriftgröße im Child-Text beim Verkleinern.
Nach erfolgreichem grafischem Test lässt sich das Prinzip auf die übrigen Geräte übertragen.
