# Adventskalender-Kompass · Your Help

Interaktives Quiz mit KI-Türchen-Generator: Coaches und Selbstständige planen in ca. 20 Minuten ihren Business-Adventskalender (Ziel, Zielgruppe, Ergebnis-Versprechen, Inhalte & Format, Rhythmus, Versand, Technik-Check, Titel). Danach schreibt Claude Opus 5.5 für jedes Türchen den kompletten Inhalt: Überschrift, E-Mail-Betreff, Mail-Text, Mini-Aufgabe und Instagram-Story.

Die Ergebnisseite enthält außerdem Kalender-Typ, Startklar-Score, Türchen-Fahrplan mit echten Daten, Zeitplan bis zum Start, 4-Wochen-Promo-Plan, Export als PDF, Text und CSV.

## Aufbau

| Pfad | Inhalt |
| --- | --- |
| `public/index.html` | Das Quiz (eine Datei, keine Build-Tools) |
| `netlify/functions/generate.mts` | Serverfunktion `/api/generate`: prüft den Zugangscode und ruft die Claude API auf |
| `netlify.toml` | Netlify-Einstellungen (veröffentlicht `public/`) |

Antworten und KI-Texte werden nur im Browser der Nutzer:innen gespeichert (localStorage). Zur Texterstellung werden die Quiz-Antworten an die Claude API von Anthropic gesendet.

## Einrichten auf Netlify (einmalig)

Wichtig: Weil eine Serverfunktion dabei ist, funktioniert **kein Drag & Drop** mehr. Netlify muss das Projekt aus GitHub bauen.

1. Netlify-Projekt öffnen → **Project configuration → Build & deploy → Link repository** → GitHub → `yheinrich74-ai/netlify`, Branch auswählen. Build-Befehl leer lassen, Publish directory `public` (wird aus `netlify.toml` übernommen).
2. **Project configuration → Environment variables** → zwei Variablen anlegen, Scope mindestens „Functions“:
   - `ANTHROPIC_API_KEY` = dein API-Schlüssel aus der Claude Console
   - `ACCESS_CODES` = deine Zugangscodes, durch Komma getrennt, z. B. `ADVENT26`
3. **Deploys → Trigger deploy → Deploy site**, damit die Variablen greifen.

## API-Schlüssel & Kosten

- Schlüssel anlegen in der Claude Console (platform.claude.com): Guthaben aufladen, unter **API Keys** einen Schlüssel erstellen.
- In der Console unter **Limits** ein monatliches Ausgabenlimit setzen (z. B. 30 €), damit nichts aus dem Ruder läuft.
- Ein kompletter Kalender (24 Türchen) kostet je nach Textlänge ca. 0,30–0,50 €. „Neu vorschlagen“ für ein einzelnes Türchen kostet ein paar Cent.
- Die Funktion begrenzt die Anfragen pro IP-Adresse auf 20 pro Minute.

## Verkauf über Tentary

- Produktpreis: 47 €. In der Auslieferung den Link zur Netlify-Seite und den Zugangscode angeben.
- Code wechseln (z. B. wenn er öffentlich geteilt wurde): `ACCESS_CODES` in Netlify ändern und neu deployen. Mehrere Codes gleichzeitig sind möglich.
- In die Datenschutzerklärung gehört ein Hinweis, dass die Quiz-Antworten zur Texterstellung an Anthropic übermittelt werden.

## Anpassen

- Farben und Schriften: CSS-Variablen oben in `public/index.html`
- Fragen und Texte: Konstanten `ZIELE`, `INHALTE`, `VERSAND`, `STEPS` usw. im Script
- Schreibstil der KI: `SYSTEM_PROMPT` in `netlify/functions/generate.mts`
