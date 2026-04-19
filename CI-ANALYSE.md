# CI-Analyse – porada-schulungen.eu (Stand: Extraktion aus Live-Startseite)

## Quellen

| Quelle | URL / Pfad |
|--------|------------|
| HTML Startseite | `https://www.porada-schulungen.eu/` (gespeichert als `/tmp/porada-index.html` während der Analyse) |
| Theme-Stylesheet (go-x) | `https://www.porada-schulungen.eu/wp-content/uploads/go-x/style.css?ver=1.0.6+ebb0f381f8` → `/tmp/porada-gox-style.css` |
| Plugin-Stylesheet | `https://www.porada-schulungen.eu/wp-content/plugins/go-x-post-editor/src/index-fe.css?ver=1776416171` → `/tmp/porada-index-fe.css` |
| Weitere eingebundene CSS | `wp-content/plugins/gutenberg/build/block-library/style.css` (WordPress-Standard, wenig markenspezifisch) |

## Farbpalette

Werte aus **inline `styles` der go-x Page-Konfiguration** (`wp:go-x/page` JSON) und **section-inline-Variablen** im HTML, ergänzt um im generierten `style.css` vorkommende Hex-Werte.

| Rolle | Wert | Herkunft / Hinweis |
|-------|------|-------------------|
| Seitenhintergrund | `#f8f8f8` | `--page-background-color` in Page-JSON |
| Fließtext (Theme) | `#8b8b8b` | `--page-color` / `--website-theme-color` Kontext |
| Überschriften (helle Sektionen) | `#6c6c6c` | `--heading-color-h1` … `h6` in Section-Styles (Text auf hellem Grund) |
| Überschriften/Text (dunkle Hero-Sektionen) | `#f8f8f8` | `--heading-color-h*` in abwechselnden Section-Styles |
| Primär-Akzent (Buttons/Links, häufig) | `#267565` | `--button-background-color`, `--button-color-link`, `--button-color-ghost` in mehreren Modul-Sections |
| Primär-Akzent (Consent/UI, nahe liegend) | `#267570` | Abweichung 1 RGB-Stufe – vermutlich Rundung/Theming; **nicht zweifelsfrei identisch zur Hauptmarke** |
| Sekundär-Akzente (modulspezifisch) | u. a. `#14d4c8`, `#2b579a`, `#3fb2cb`, `#1d6f42`, `#7e2294`, `#c83b20` | unterschiedliche `--button-background-color` je nach Bereich – **keine einzelne „Marken-Akzentfarbe“ für alle Buttons** |
| UI-Blau (Privacy/Links) | `#1183D1`, `#3c9ddb` | Consent-/Privacy-Settings |
| Dunkelblau (Modal-Text) | `#001b41` | `.page-blocker-title` im Theme-CSS |
| Neutral Grau | `#a0a0a0`, `#777777` | Buttons/Schalter |

**Unsicherheit:** Es gibt **keine eine** durchgängige Akzentfarbe; die Live-Seite wechselt Button-Farben nach Kontext. Für den Relaunch wird **ein konsistentes Primär-Grün `#267565`** (häufigste CTA-Variante) als Hauptakzent empfohlen; Abweichungen in der Analyse dokumentiert.

**Kontrast:** Reiner Fließtext `#8b8b8b` auf `#f8f8f8` kann für kleine Schrift unter AA liegen. Im Relaunch wird der Body-Text bewusst **etwas dunkler** gewählt (`#5c5c5c`), die Analyse-Werte bleiben oben als Referenz der Bestandsseite erhalten.

## Typografie

| Verwendung | Family | Größen / Gewichte (Bestand) |
|------------|--------|-----------------------------|
| Überschriften | **Merriweather** | H1: 45px, H2: 37px, H3: 31px, H4: 26px, H5: 22px, H6: 18px; `font-weight: 400` (inline-Variablen) |
| Fließtext | **Arial** | 16px (medium), 14px/18px small/large laut Theme-JSON |
| Buttons | **Arial** | 16px, `font-weight: 400`, `letter-spacing: 1px` (typisch in Section-Styles) |

**@font-face:** Im HTML eingebettete Merriweather-Dateien unter `/wp-content/themes/gox/public/fonts/` (Host: `porada-schulungen.eu`).

**OpenSans** taucht in Consent-/Privacy-Blocks auf – sekundär.

## Buttons (Theme-CSS)

Aus `gox-style.css` (Auszug):

- `.button-button`: `border-radius: 8px`
- `.button-primary-button`: Hintergrund/Border über `var(--button-background-color)`, Textfarbe `var(--button-color-primary)`
- Fokus: u. a. `outline: 2px solid #00f`, `box-shadow: 0 0 0 2px #fff` (Browser-Standard-Fokus)

Padding ist über Theme-Variablen gesteuert und nicht als feste px-Angabe in einem kurzen Snippet isoliert – **konkretes Padding auf der Live-Seite: nicht aus einem einzelnen statischen Wert ablesbar**, im Relaunch: angemessenes horizontales/vertikales Padding (ca. 0,75–1,25em) nach visueller Nähe zu 8px-Radius.

## Logo

| Beschreibung | URL |
|--------------|-----|
| **OG-Image / identitätsnahes Bild** | `https://porada-schulungen.eu/wp-content/uploads/go-x/u/0a39e7c4-7ed5-4762-b3e2-9ef6b4df2c21/image-1200x743.png` (auch in `og:image`) |
| **Schema.org logo** (Pfad relativ, CDN-Resize) | `/-_-/resources/images/files/62e6ed57-e8c6-4ddc-b43f-eb99f13a43a3/0a39e7c4-7ed5-4762-b3e2-9ef6b4df2c21?o=rs:fill:1476:914:1:1/g:sm/` |

**Hinweis:** Das aus der Navigation extrahierbare „Logo“ ist das **große OG-Bild**; eine separate kleine Logo-SVG-URL stand im untersuchten HTML-Header nicht klar als Navigationslogo gelabelt. Für die neue `index.html` wird ein **lokales Platzhalter-Logo** empfohlen; Angela kann die OG-URL oder ein exportiertes Bild einsetzen.

## Zusammenfassung für Umsetzung

- **Farben:** Hintergrund `#f8f8f8`, Überschriften `#6c6c6c`, Akzent **`#267565`**, neutrale Textfarbe für Lesbarkeit leicht angepasst.
- **Fonts:** Merriweather (Überschriften) + Arial/Systemsans (Fließtext) – über Google Fonts spiegeln, mit Fallbacks.
- **Buttons:** 8px Radius, kräftige Füllfarbe `#267565`, helle Schrift auf Primary.
