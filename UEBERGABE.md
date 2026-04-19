# Übergabe – Projekt Porada (porada-schulungen Relaunch)

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

Wenn das Remote-Repo **leer** ist:

```bash
git push -u origin main
```

### 4. SSH zu GitHub

Bei `Host key verification failed`:

- `ssh -T git@github.com` (Host-Key bestätigen), oder  
- `git remote set-url origin https://github.com/peerendees/poradaa.git` und mit Token pushen.

## Inhaltliche Nacharbeit (nicht Teil des Push)

Siehe `README.md` und `CI-ANALYSE.md`: Portrait, Logo, Kontaktdaten, `mailto`, Footer-URLs gegen die Live-Seite prüfen.

---

*Pfad: ausschließlich `projekte/poradaa` – kein Duplikat unter `berentai`.*
