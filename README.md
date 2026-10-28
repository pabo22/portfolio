# Pauls Depot

Persönliches Depot-Dashboard als statische Seite für GitHub Pages.

- **Depotwert live:** Bitcoin und EUR/USD von Binance (alle 20 Sekunden), Aktien und ETFs über Twelve Data (alle 5 Minuten während der US-Handelszeit, Key wird nur im Browser gespeichert).
- **Verlauf:** 1T, 1W, 1M, 1J, Max, als Wert oder Gewinn (ohne Ein- und Auszahlungen). Mit dem Finger über den Chart wischen zeigt oben den Wert zu jedem Zeitpunkt.
- **Handy:** Tab-Leiste unten (Depot, Markt, Termine), Positionen zum Aufklappen, Einstellungen als Panel von unten. Lässt sich als App auf den Home-Bildschirm legen.
- **Aufteilung:** nach Positionen, Sektoren und Regionen.
- **Markt heute, Sektoren, Gewinner/Verlierer, Auslöser, Termine:** aus `data/brief.json`, jeden Werktag morgens von einer geplanten Claude-Aufgabe aktualisiert (siehe `UPDATE.md`).

## Datenschutz

Der Transaktionsexport (CSV) und der API-Key werden nur im Browser gespeichert (localStorage) und nie ins Repo geschrieben. Im Repo stehen nur die Marktanalyse und Schlusskurse.

## Einrichtung

Nichts zu installieren. Im Repo unter *Settings → Pages* die Quelle *Deploy from a branch*, Branch `main`, Ordner `/ (root)` wählen. Danach die Seite öffnen, unter *Einstellungen* den Twelve-Data-Key eintragen und den Transaktionsexport hochladen.

Keine Anlageberatung. ETF-Kurse sind Schätzungen über US-Vergleichs-ETFs.
