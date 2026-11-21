# Links & Rechts Trainer

Web-App (PWA), die Kindern und Erwachsenen hilft, links und rechts sicher zu unterscheiden.

## Aufbau
- `index.html`: die komplette App (HTML, CSS, JavaScript in einer Datei, kein Build-Schritt)
- `manifest.json`, `icon.svg`, `sw.js`: PWA (installierbar, offline nutzbar)
- Fortschritt wird nur im Browser gespeichert (`localStorage`, Schlüssel `lr-progress`)

## Übungen (Objekt `EX` in index.html)
Jede Übung hat `name`, `icon`, `desc`, `levels` (3 Stufen) und `gen(level)`.
`gen` gibt eine Aufgabe zurück: `{ answer: 'L'|'R', prompt, html, limit (ms, 0 = ohne), hint, audio?, speak? }` (speak = Satz für die Sprachausgabe).
- pfeil: Pfeil-Reaktion
- wort: Wort-Übung mit Stroop-Effekt
- hand: Hände erkennen (SVG mit Hautverlauf, Nägeln, Gelenkfalten und Handlinien; Handrücken/Handfläche, gedreht)
- spiegel: Person von vorne/hinten hebt einen Arm
- weg: Auto biegt ab, Sicht des Fahrers
- hoeren: Stereo-Ton über Web Audio
- stimme: Sprachausgabe (speechSynthesis, deutsche Stimme), z. B. „Heb die linke Hand.“; Stufe 3 mit „nicht“
- mix: zufällig aus pfeil, wort, hand, spiegel, weg

Eine neue Übung = neuer Eintrag in `EX` mit `gen()`, danach in `order` (Funktion `home`) und ggf. `MIX_KEYS` eintragen.

## Regeln
- Alle Texte auf Deutsch, einfache Sprache, auch für Kinder verständlich.
- Keine Gedankenstriche (Em-Dashes) in Texten.
- Mobil zuerst: große Buttons, Pfeiltasten am PC.
- Keine Farben als Antwort-Hinweis (Links/Rechts-Buttons bleiben neutral).
- Keine externen Bibliotheken und kein Backend, solange es nicht nötig ist.
- Nach Änderungen die App im Browser testen und Logik prüfen: Bei Handbildern gilt
  Handrücken + rechte Hand = Daumen links; Handfläche + rechte Hand = Daumen rechts.

## Starten
`index.html` im Browser öffnen. Für PWA/Offline: lokalen Server starten, z. B. `npx serve .` oder `python -m http.server`.

## Ideen für später
- Elternbereich mit Statistik über mehrere Tage
- Weg-Übung mit mehreren Abbiegungen hintereinander
- Kamera-Übung (Hand vor die Kamera halten)
- Native App über Capacitor
