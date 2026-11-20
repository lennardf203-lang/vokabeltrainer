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

## Ordnung

Jedes Deck in `decks.js` hat diese Form:

```js
"Spanisch — U2 Bloque A": { fach: "Spanisch", unit: "U2", added: "2026-11-19", words: [ { de: "…", fs: "…", info: "…" } ] }
```

- `fach` = Fach, `unit` = Unit/Kapitel/Lektion wie im Buch (`""`, falls keine),
  `added` = Tag der Eintragung (`YYYY-MM-DD`, also heute).
- Optional `gesamt: true` markiert ein Sammel-Deck (z. B. "Englisch — K6 gesamt: The World of Work").

Die App sortiert automatisch: Faecher A-Z; innerhalb eines Fachs zuerst die Unit mit dem neuesten `added`;
Decks ohne Unit zuletzt; innerhalb einer Unit Buchreihenfolge (= Reihenfolge in `decks.js`), Sammel-Deck zuerst.
Dropdown und Fortschrittstabelle sind gruppiert als "Fach · Unit · Datum".

**Regel beim Eintragen (verbindlich fuer alle KI-Agenten):**
1. Pro Buchabschnitt ein neues Deck, Name `<Fach> — <Unit> <Abschnitt>`.
2. `fach`, `unit`, `added` (heute) setzen.
3. In `decks.js` im Block des Fachs an die Stelle seiner Unit setzen (Buchreihenfolge).
4. Danach `sh tools/vokabeltrainer/publish.sh`.

Bestehende Deck-Namen **nie umbenennen**: der Lernfortschritt im Browser haengt am Deck-Namen.

## Vokabeln hinzufuegen

**Foto-Import (empfohlen):** Foto der Vokabelliste in den Chat legen oder in
`schule/_eingang/` ablegen, dann Devin sagen: "importiere das in den Vokabeltrainer".
Devin liest das Bild und traegt die Woerter in `decks.js` ein.

**Funktioniert auch aus der Cloud (iPad/Handy):** In app.devin.ai eine Session mit
diesem Repo starten, Foto in den Chat laden, Prompt:
"Lies die Vokabeln vom Bild und trage sie in `tools/vokabeltrainer/decks.js` als
Deck '<name>' ein (mit fach, unit, added = heute, einsortiert wie im Abschnitt "Ordnung"),
dann commit + push auf main."

**Paste-Import:** In der App unten aufklappen — Format pro Zeile:
`deutsch;fremdsprache;info(optional)`. Deck-Name z. B. "Spanisch U3 Bloque A": Fach und Unit
werden aus dem Namen gelesen, das Datum ist der Importtag.

**Manuell:** Deck in `decks.js` mit `fach`, `unit`, `added` anlegen (siehe "Ordnung"), Eintraege als
`{ de: "…", fs: "…", info: "…" }`.

## Dateien

- `index.html` — die App (oeffnen, fertig)
- `decks.js` — alle Vokabel-Decks (wird von Devin gepflegt, synced via Git)
