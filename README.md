# Adventskalender-Kompass · Your Help

Interaktives Quiz, mit dem Coaches und Selbstständige in ca. 20 Minuten ihren Business-Adventskalender planen: Ziel, Zielgruppe, Ergebnis-Versprechen, Inhalte & Format, Rhythmus, Technik-Check, Titel. Am Ende gibt es:

- den persönlichen Kalender-Typ und einen „Startklar-Score“
- einen Steckbrief mit allen Antworten
- einen Türchen-Fahrplan mit echten Kalenderdaten (zum Ausfüllen)
- einen Zeitplan bis zum Start, zum Abhaken
- einen 4-Wochen-Promo-Plan für Social Media, Ideen für die gewählten Kanäle und eine Caption-Vorlage
- Export als PDF (Drucken) und als Text (Kopieren)

Alles steckt in einer einzigen Datei (`index.html`). Antworten werden nur im Browser der Nutzer:innen gespeichert (localStorage), es gibt keine Datenbank und kein Tracking.

## Auf Netlify veröffentlichen

1. In Netlify: **Add new project → Import an existing project → GitHub** und dieses Repository auswählen.
2. Build-Einstellungen leer lassen. `netlify.toml` setzt das Veröffentlichungsverzeichnis auf `.`.
3. Optional eine eigene Domain verbinden, z. B. `adventskompass.yvonneheinrich.de`.

Die Seite ist per `X-Robots-Tag: noindex` von Suchmaschinen ausgeschlossen, damit nur Käufer:innen sie finden.

## Über Tentary verkaufen

- Lege in Tentary ein digitales Produkt an und hinterlege den Netlify-Link im Bereich für die Auslieferung bzw. in der Bestätigungsmail.
- **Optionaler Zugangscode:** In `index.html` steht oben im Script `const ZUGANGSCODE = "";`. Trag dort einen Code ein (z. B. `"ADVENT26"`). Käufer:innen müssen ihn dann einmal eingeben. Schick den Code in der Tentary-Bestätigung mit.
  Hinweis: Der Code ist ein einfacher Schutz gegen zufälliges Teilen und keine echte Sicherheit. Wer den Quelltext liest, findet ihn. Für echten Schutz die Netlify-Passwortfunktion (Site protection) nutzen.

## Anpassen

- Farben und Schriften: CSS-Variablen ganz oben in `<style>` (`--pink`, `--ink-strong` usw.)
- Fragen, Antworten und Texte: die Konstanten `ZIELE`, `INHALTE`, `KANAELE`, `STEPS` usw. im Script
- Footer und Name: unten im `<footer>`
