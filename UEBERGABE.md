# Übergabe – Projekt Porada (porada-schulungen Relaunch)

> **Dateiname im Repo:** `UEBERGABE.md` (ASCII). Gemeint ist dieselbe „Übergabe“-Datei.

Diese Datei ist für den **nächsten Chat** gedacht: Commit- und Push-Stand prüfen, bei Bedarf nachziehen, dann zu GitHub pushen.

## Projektpfad (lokal) – verbindlich

Eigenständiges Git-Repository, **nicht** unter `berentai`:

```
/Users/kunkel/Entwicklung/projekte/poradaa
```

Der Ordner `berentai/poradaa` ist **kein** Projektstand mehr und soll leer bzw. entfallen. Wenn du den Ordner verschiebst: nur den **gesamten** Ordner inkl. `.git` mitnehmen – relative Pfade im Projekt bleiben gültig.

## Remote (GitHub)

| Feld   | Wert |
|--------|------|
| Repo   | `peerendees/poradaa` |
| Remote | `origin` → `git@github.com:peerendees/poradaa.git` |
| Branch | `main` |

HTTPS-Alternative: `https://github.com/peerendees/poradaa.git`

## Was im Repo liegen soll

- `index.html`, `styles.css`, `script.js`, `CI-ANALYSE.md`, `README.md`, `.gitignore`, diese `UEBERGABE.md`

**Hinweis:** Wenn `git status` „nothing to commit“ zeigt, gibt es **nichts zu committen** – nur noch **push** (nach Prüfung des Remotes).

## Nächster Chat – Checkliste (Commit und Push)

### 1. Ordner öffnen und prüfen

```bash
cd /Users/kunkel/Entwicklung/projekte/poradaa
git status
git log --oneline -8
git remote -v
```

### 2. Falls `UEBERGABE.md` (oder andere Dateien) neu / geändert

```bash
git add -A
git status
git commit -m "docs: Übergabe-Hinweise und Pfad projekte/poradaa"
```

### 3. Remote-Stand abgleichen (falls auf GitHub schon Commits existieren)

Browser: https://github.com/peerendees/poradaa  

Wenn dort bereits Historie liegt und der Push abgelehnt wird:

```bash
git fetch origin
git pull origin main --allow-unrelated-histories
# Konflikte lösen, dann:
git push -u origin main
```

Wenn das Remote-Repo **leer** ist (Standard nach leerem GitHub-Repo):

```bash
cd /Users/kunkel/Entwicklung/projekte/poradaa
git push -u origin main
```

### 4. SSH zu GitHub

Bei `Host key verification failed`:

- `ssh -T git@github.com` (Host-Key bestätigen), oder  
- `git remote set-url origin https://github.com/peerendees/poradaa.git` und mit Token pushen.

## Inhaltliche Nacharbeit (nicht Teil des Push)

Siehe `README.md` und `CI-ANALYSE.md`: Portrait, Logo, Kontaktdaten, `mailto`, Footer-URLs gegen die Live-Seite prüfen.

## Vorschau: Blog (`projekte/blog`) und Porada im Editor-Browser (Cursor)

Der **BERENT-Blog** liegt **nebendran** im Workspace, nicht im `poradaa`-Repo:

```
/Users/kunkel/Entwicklung/projekte/blog/index.html
```

`blog/index.html` verlinkt **Wurzelpfade** (`/css/…`, `/assets/…`). Deshalb **nicht** zuverlässig per `file://` testen — kurz einen **HTTP-Server im Ordner `blog`** starten und die Seite im eingebetteten Browser öffnen.

### Schritte

1. **Blog-Server** (eigenes Terminal, Arbeitsverzeichnis `blog`):

   ```bash
   cd /Users/kunkel/Entwicklung/projekte/blog
   python3 -m http.server 8787
   ```

2. **Porada-Server** (zweites Terminal, Arbeitsverzeichnis `poradaa`):

   ```bash
   cd /Users/kunkel/Entwicklung/projekte/poradaa
   python3 -m http.server 8788
   ```

3. **Editor-Browser in Cursor:** Befehlspalette (**Cmd+Shift+P**) → **„Simple Browser: Show"** (oder je nach Version **„Browser: Open"** / integrierter Browser).  
   - Blog: `http://127.0.0.1:8787/` bzw. `http://127.0.0.1:8787/index.html`  
   - Porada-Startseite: `http://127.0.0.1:8788/` bzw. `http://127.0.0.1:8788/index.html`  

   Optional zweites Simple-Browser-Panel für die jeweils andere URL.

4. **Einstellung (Cursor/VS Code):** z. B. `workbench.browser.openLocalhostLinks` (Links zu `localhost` im Editor-Browser) und ggf. `simpleBrowser.useIntegratedBrowser` — siehe aktuelle Dokumentation zu *Simple Browser* / *Integrated Browser*.

---

*Pfad: ausschließlich `projekte/poradaa` – kein Duplikat unter `berentai`.*
