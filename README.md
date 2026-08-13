# Azubi-Olympiade · Bewegungsstation

Web-App zum Erfassen der Punkte an der Bewegungsstation der Azubi-Olympiade: Werteingabe, Timer und
Gesamtauswertung für zwei Teams. Läuft im Browser auf dem Handy, **auch ohne
Internet**, und speichert alle Eingaben auf dem Gerät.

Eine Datei, keine Installation, kein Server, keine Datenübertragung.

---

## Für die Fachkraft vor Ort

1. Die Adresse der App im Handy-Browser öffnen (Link vom Team, siehe unten).
2. **Einmal zum Startbildschirm hinzufügen** – dann startet sie wie eine App und
   funktioniert in der Halle auch ohne Netz:
   - **iPhone (Safari):** Teilen-Symbol → *Zum Home-Bildschirm*
   - **Android (Chrome):** Menü ⋮ → *App installieren* bzw. *Zum Startbildschirm hinzufügen*
3. Vor dem Start im Tab **Ablauf**: Teamnamen eintragen und die **Antretenden pro
   Team** einstellen. Daraus ergeben sich Messreihen, Anzahl Duelle und
   Kistenanzahl (Antretende − 1).
4. Stationen der Reihe nach durchgehen. Der Punktestand steht immer oben.
5. Am Ende **Gesamtauswertung** → *Ergebnis kopieren* (z. B. in eine Notiz oder
   WhatsApp einfügen) oder *Drucken / PDF*.

**Gut zu wissen**

- Eingaben werden laufend auf dem Gerät gesichert. Ein versehentlich geschlossener
  Browser oder gesperrter Bildschirm kostet keine Punkte – beim erneuten Öffnen ist
  alles wieder da.
- Laufende Timer stehen nach einem Neustart still und laufen mit *Weiter* weiter.
- *Alles zurücksetzen* in der Gesamtauswertung löscht den gespeicherten Stand –
  vor jedem neuen Durchlauf einmal drücken.
- Das Display bleibt an, solange ein Timer läuft.
- Ist das Handy auf dunkles Design gestellt, zeigt die App sich dunkel.

---

## Stationen und Punkte

| Station | Zeit | Punkte | Wertung |
|---|---|---|---|
| Einführung | 2 min | – | Übersicht und Gruppen |
| 1 · Handkraftmessung | 4 min | 2 | besserer Median gewinnt, bei Gleichstand die höhere Summe |
| 2 · Plank | 6 min | 0,5 je Duell | alle Duelle gleichzeitig, ein gemeinsamer Timer |
| 2.1 · Wandsitzen *(Alternative)* | 6 min | 2 | 2 gegen 2, Limit 5 min → Gleichstand |
| 3 · Wasserkistenrennen | 7 min | 3 | erste Zielüberquerung, ein Tipp beendet das Rennen |

Station 2 ist im Tab *Ablauf* zwischen **Plank** und **Wandsitzen** umschaltbar –
Wandsitzen ist das Backup bei ungeeignetem Boden. Nur die gewählte Variante zählt.

---

## Veröffentlichen über GitHub Pages

1. Auf GitHub ein neues Repository anlegen, z. B. `bewegungsstation`.
2. Den **kompletten Inhalt dieses Ordners** hochladen – *Add file → Upload files*,
   die Dateien und den Ordner `icons/` per Drag & Drop ins Browserfenster ziehen,
   dann *Commit changes*.
3. **Settings → Pages**: unter *Build and deployment* → *Source* **Deploy from a
   branch**, Branch `main`, Ordner `/ (root)` → *Save*.
4. Nach ein bis zwei Minuten ist die App erreichbar unter
   `https://<benutzername>.github.io/bewegungsstation/`
5. Diesen Link an die Fachkraft geben – am einfachsten als QR-Code
   (z. B. im Browser über *Teilen → QR-Code erstellen*), dann muss nichts getippt werden.

> **Hinweis zur Sichtbarkeit:** GitHub Pages ist in kostenlosen Konten nur für
> **öffentliche** Repositories verfügbar. Damit wären App und Company-Move-Logo
> öffentlich im Netz erreichbar (nicht auffindbar, aber abrufbar). Wenn das nicht
> gewünscht ist: Repository privat halten und die Datei `index.html` stattdessen
> direkt verteilen – sie funktioniert eigenständig, siehe unten.

### Ohne GitHub nutzen

`index.html` enthält die komplette App inklusive Schrift und Logo. Die Datei per
Mail, Teams oder USB weitergeben und im Browser öffnen – alles funktioniert, außer
dem Installieren als App. Alternativ in einen Cloud-Ordner legen und den Freigabe-Link teilen.

---

## Dateien

| Datei | Zweck |
|---|---|
| `index.html` | die komplette App: Logik, Layout, Exo-2-Schrift und Logo eingebettet |
| `manifest.webmanifest` | Name, Farben und Icons für die Installation als App |
| `sw.js` | Service Worker – speichert die App fürs Offline-Öffnen |
| `icons/` | App-Icons (192, 512, maskable, Apple Touch) |

## Änderungen einpflegen

`index.html` ist eine einzelne Datei ohne Build-Schritt – direkt auf GitHub
bearbeiten (Stift-Symbol) und committen. Die häufigsten Stellen:

- **Punkteverteilung:** `const PTS = { grip:2, duel:0.5, wall:2, race:3 };`
- **Zeiten und Reihenfolge:** in der Funktion `vStart()`
- **Regeltexte:** in `vGrip()`, `vPlank()`, `vWall()`, `vRace()`
- **Farben:** die CSS-Variablen `--lime`, `--a`, `--b` ganz oben

Nach einer Änderung in `sw.js` die Zeile
`const VERSION = 'bewegungsstation-v1';` hochzählen (z. B. `-v2`), sonst behalten
schon installierte Geräte die alte Version. Die App holt das Update, sobald sie
einmal mit Internet geöffnet wird.

---

## Datenschutz

Die App sendet keine Daten. Eingaben liegen ausschließlich im lokalen Speicher des
verwendeten Browsers und werden mit *Alles zurücksetzen* gelöscht. Es gibt kein
Tracking, keine Cookies, keine externen Aufrufe – Schrift und Logo sind in die
Datei eingebettet.

---

Design und Logo: Company Move GmbH · Schrift: [Exo 2](https://fonts.google.com/specimen/Exo+2) (SIL Open Font License)
