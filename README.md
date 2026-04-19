# porada-schulungen.eu – statische Startseite (Relaunch-Entwurf)

Einzelne **Single-Page**-`index.html` mit Anker-Navigation für Word, Excel, PowerPoint und Teams. Styling in `styles.css`, Verhalten (Menü, Scroll, Sichtbarkeit) in `script.js`. Die **CI-Extraktion** von der bisherigen Live-Seite steht in `CI-ANALYSE.md`.

## Technische Entscheidungen

- **Kein Build-Tool, keine npm-Abhängigkeiten** – reines HTML/CSS/JS, lokal per Doppelklick oder statischem Server nutzbar.
- **Merriweather** für Überschriften und **Arial** für Fließtext über Google Fonts, passend zur Bestandsseite (siehe CI-Analyse). Bei fehlender Internetverbindung greifen Browser-Fallbacks (Georgia bzw. Helvetica).
- **Primärfarbe `#267565`**: In der CI-Analyse am häufigsten als Button-Hintergrund in den Section-Variablen der Live-Seite; die Bestandsseite nutzt zusätzlich weitere Akzente pro Bereich – für einen konsistenten Relaunch wurde eine Farbe gewählt.
- **Fließtext `#5c5c5c` statt `#8b8b8b`**: leicht dunkler für Lesbarkeit und WCAG-Kontrast auf hellem Grund; Referenzwerte der alten Seite bleiben in `CI-ANALYSE.md` dokumentiert.
- **Footer-Links** zu Impressum, Datenschutz und Haftungsausschluss zeigen auf typische Pfade unter `https://www.porada-schulungen.eu/`. Die exakten Slugs solltest du gegen die aktuelle WordPress-Struktur prüfen und bei Bedarf anpassen.

## Was du noch eintragen oder austauschen solltest

| Bereich | Hinweis |
|--------|---------|
| Portrait im Hero | Platzhalter-Box ersetzen durch echtes Bild (`img` mit `alt`-Text). |
| Logo | Aktuell SVG-Kompass + Text „Angela Porada“. Optional Bild-Logo (z. B. aus der CI-Analyse genannte OG-Grafik) einbinden. |
| Kontakt | Platzhalterzeilen für E-Mail und Telefon; Button **E-Mail schreiben** nutzt `mailto:kontakt@beispiel.de` – durch deine Adresse ersetzen. |
| Copyright-Jahr | Stand der Aufgabenstellung: © 2025 – bei Bedarf aktualisieren. |

## Lokales Öffnen

Datei `index.html` im Browser öffnen oder kurz einen statischen Server starten, z. B. `python3 -m http.server 8080` im Projektordner.

## Lighthouse

Scores hängen von Umgebung (localhost vs. HTTPS) und Fonts ab. Für produktive Nutzung eigenes Hosting und ggf. HTTPS einplanen.

## Übergabe (Repo)

Pfad: **`…/projekte/poradaa`** (nicht unter `berentai`). Eigenständiges Git-Repository mit Remote `git@github.com:peerendees/poradaa.git`. Schrittfolge für Commit und Push: siehe **`UEBERGABE.md`**.
