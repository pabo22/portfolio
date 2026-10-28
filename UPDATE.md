# Anleitung für die tägliche Aktualisierung (geplante Claude-Aufgabe)

Diese Datei beschreibt, was die geplante Aufgabe jeden Werktag morgens erledigt. Die Seite selbst (`index.html`) wird dabei nicht verändert, nur die Dateien in `data/`.

## 1. `data/brief.json` neu schreiben

Recherchiere mit der Websuche den Stand von heute (Zeitzone Europe/Berlin) und schreibe die Datei im bestehenden Format neu. Alle Texte auf Deutsch, kurz und sachlich, keine Kauf- oder Verkaufsempfehlungen.

- `updated`: aktueller Zeitpunkt mit Offset (ISO 8601).
- `headline`, `summary`: Was den Markt gestern Abend (USA) und heute früh (Europa/Asien) bewegt hat.
- `indices`: S&P 500, Nasdaq, Dow, Russell 2000 (letzter Schluss), DAX (letzter Schluss oder Vorbörse), US-Rendite 10 Jahre, Öl (WTI), optional Bitcoin. `chg` in Prozent oder `null`.
- `sectors`: 6-9 Sektoren mit `strength` von −2 (sehr schwach) bis +2 (sehr stark) und einem Satz mit konkreten Beispielen. Erlaubte Schlüssel: `it, comm, disc, staples, health, fin, ind, energy, mat, util, re, crypto`.
- `movers.us` und `movers.de`: je 3-4 Gewinner und Verlierer mit Prozent und Grund.
- `triggers`: 3-5 Auslöser mit betroffenen Sektoren.
- `positions`: je ein bis zwei Sätze, was die Lage für jede Position heißt. Schlüssel: `NVDA, AMZN, BTC, WORLD, EM, EUROPE` (und neue Positionen, siehe unten).
- `events`: alle wichtigen Termine der nächsten ~6 Wochen (Zinsentscheide Fed/EZB, CPI, Arbeitsmarkt, Zahlen der gehaltenen Aktien und großer Index-Schwergewichte, Wahlen, große Optionsverfälle). Vergangene Termine entfernen. Zeiten in deutscher Zeit. Jeder Termin mit `sectors` und `positions` (was er für den Sektor bzw. die Position bedeutet); politische Ereignisse mit `scenarios`.
- `sources`: die tatsächlich genutzten Quellen als Titel + URL.

Politische Themen ausgewogen darstellen: Szenarien beschreiben, keine Partei bevorzugen.

## 2. `data/closes.json` ergänzen

Für jede Position den letzten Schlusskurs in Euro anhängen (`["JJJJ-MM-TT", Kurs]`), falls für das Datum noch kein Eintrag existiert:

| Schlüssel | Wertpapier | Wo |
|---|---|---|
| NVDA | NVIDIA (US67066G1040) | Xetra/Tradegate in EUR |
| AMZN | Amazon (US0231351067) | Xetra/Tradegate in EUR |
| BTC | Bitcoin | BTC/EUR |
| WORLD | iShares Core MSCI World (IE00B4L5Y983, EUNL) | Xetra in EUR |
| EM | Xtrackers MSCI EM 1C (IE00BTJRMP35, XMME) | Xetra in EUR |
| EUROPE | iShares MSCI Europe Screened (IE00BFNM3D14) | Xetra in EUR |

Nur Kurse eintragen, die aus einer Quelle stammen. Wenn kein verlässlicher Kurs zu finden ist, den Tag auslassen. Die Seite nutzt diese Werte, um die Euro-Schätzung der ETFs zu eichen.

## 3. Neue Positionen

Der aktuelle Bestand steht nicht im Repo (er liegt nur im Browser des Nutzers). Wenn in den Daten oder in einem Hinweis des Nutzers neue Positionen auftauchen, Schlüssel und Eintrag ergänzen. Neue Wertpapiere müssen außerdem im Objekt `REG` in `index.html` eingetragen werden (ISIN, Name, Art, US-Ticker, Sektor- und Regionsaufteilung); das nur machen, wenn der Nutzer darum bittet.

## 4. Commit

JSON vor dem Commit prüfen (`python3 -m json.tool data/brief.json`). Commit-Nachricht: `Marktanalyse JJJJ-MM-TT`. Direkt auf `main` pushen.

## Schreibstil

Keine Gedankenstriche (– oder —) in den Texten, stattdessen Punkt, Komma oder Bindestrich. Zahlenbereiche mit Bindestrich (79.000-86.500 $). Sätze kurz halten, damit sie am Handy gut lesbar sind.
