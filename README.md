# Vokabeltrainer

Schlichte Web-App zum Vokabellernen.

**Online (Handy/iPad/PC):** https://lennardf203-lang.github.io/vokabeltrainer/

Lokal: `index.html` doppelklicken — laeuft ohne Server.

## Veroeffentlichen

Die Online-Version liegt im oeffentlichen Repo `lennardf203-lang/vokabeltrainer` (GitHub Pages).
Nach jeder Aenderung an `decks.js` oder `index.html`: `sh tools/vokabeltrainer/publish.sh`
ausfuehren (spiegelt den Ordner dorthin). Devin macht das automatisch mit, wenn es Vokabeln eintraegt.

## Features

- **Richtung waehlbar:** Deutsch → Fremdsprache, Fremdsprache → Deutsch, oder gemischt
- **Schwer-Markierung (★):** markierte Woerter kommen 3x haeufiger dran; optional "Nur schwere"-Modus
- **Akzenttoleranz:** fuehlt fuer Spanisch etc. (abschaltbar)
- **Info-Feld:** Beispiel, Genus, Unregelmaessigkeiten pro Vokabel
- **Mehrere Antworten:** mit `/` getrennt (`"rápido/rápida"`)
- **Statistik:** richtig/falsch pro Session, Fortschritt bleibt lokal gespeichert

## Vokabeln hinzufuegen

**Foto-Import (empfohlen):** Foto der Vokabelliste in den Chat legen oder in
`material/vokabeln/` ablegen, dann Devin sagen: "importiere das in den Vokabeltrainer".
Devin liest das Bild und traegt die Woerter in `decks.js` ein.

**Funktioniert auch aus der Cloud (iPad/Handy):** In app.devin.ai eine Session mit
diesem Repo starten, Foto in den Chat laden, Prompt:
"Lies die Vokabeln vom Bild und trage sie in `tools/vokabeltrainer/decks.js` als
Deck '<name>' ein, dann commit + push auf main."

**Paste-Import:** In der App unten aufklappen — Format pro Zeile:
`deutsch;fremdsprache;info(optional)`

**Manuell:** Eintraege in `decks.js` — `{ de: "…", fs: "…", info: "…" }`.

## Dateien

- `index.html` — die App (oeffnen, fertig)
- `decks.js` — alle Vokabel-Decks (wird von Devin gepflegt, synced via Git)
