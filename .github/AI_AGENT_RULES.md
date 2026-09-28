# AI-Agent Repository Rules

Diese Regeln gelten für alle Arbeiten von KI-Agenten in diesem Repository.

## 1. Automatisch pushen

Wenn ein KI-Agent eine angeforderte Aufgabe im Repository vollständig umgesetzt hat, sollen die fertigen Änderungen automatisch in das Repository gepusht werden. Es soll nicht jedes Mal separat nachgefragt werden, ob ein Push gewünscht ist.

Ausnahmen:
- Der Nutzer verlangt ausdrücklich, nicht zu pushen.
- Die Änderung ist offensichtlich unfertig oder fehlerhaft.
- Ein Push würde bestehende, fremde Änderungen überschreiben oder einen Konflikt verursachen, der nicht sicher aufgelöst werden kann.
- Für den Push fehlen notwendige Berechtigungen.

## 2. AI-Agent-Kennung

Jeder Commit, der von einer KI erstellt oder maßgeblich verändert wurde, muss eine eindeutige Kennzeichnung enthalten.

Für ChatGPT:
`AI-Agent: ChatGPT`

Wenn mehrere KI-Agenten an derselben Änderung beteiligt waren, werden sie durch Kommas getrennt angegeben, zum Beispiel:

`AI-Agent: ChatGPT, Devin, Cloud Devin`

Die Kennzeichnung soll im Commit-Text enthalten sein. Bei geeigneten Dokumenten oder Dateien kann zusätzlich eine sichtbare Agenten-Kennung verwendet werden.

## 3. Fertig bedeutet fertig

Eine Änderung gilt als fertig, wenn die angeforderte Aufgabe umgesetzt wurde und die erzeugten Dateien bzw. Änderungen sinnvoll überprüft wurden. Danach soll der Agent ohne zusätzliche Aufforderung committen und pushen.

## 4. Keine unnötigen Commits

Zusammengehörige Änderungen einer Aufgabe sollen möglichst in einem sinnvollen Commit zusammengefasst werden. Der Commit-Titel soll kurz beschreiben, was geändert wurde.

## 5. Transparenz

Nach dem Push soll dem Nutzer kurz mitgeteilt werden:
- was gepusht wurde,
- welcher Commit erstellt wurde,
- welche KI-Agenten beteiligt waren.

Diese Regel gilt als Standard für zukünftige Arbeiten von KI-Agenten in diesem Repository.
