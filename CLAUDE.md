# CLAUDE.md

Website der Autorin **Jule Peuckmann**, die sich und ihre Arbeit
(Bücher, Lesungen, Presse) vorstellt. Kein Projekt aus Melis' Portfolio,
sondern eine Seite für eine Kundin. Aufgebaut wie `~/roze-esthetique`.
Repo: `github.com/Brokkoli2173/autorin-website`.

## Stand

- Das Gerüst steht, der Name ist eingesetzt. Texte, Bücher, Termine,
  Bilder und der gestalterische Stil („Vibe“) kommen noch von der
  Nutzerin. Alles in eckigen Klammern (`[Buchtitel]`, …) ist
  Platzhalter und muss vor dem Livegang ersetzt werden:
  `grep -rn "\[" --include=*.html .`
- Farben, Schriften und Abstände sind bewusst neutral und stehen als
  Variablen oben in `assets/css/style.css` (`:root`). Den Stil dort
  festlegen, nicht verstreut in den Regeln.
- GitHub Pages ist noch **nicht** eingeschaltet (Platzhalter sollen
  nicht live gehen). Pushen nur, wenn die Nutzerin es sagt.

## Hosting

- Gedacht für **GitHub Pages** (Branch `main`, Root-Ordner). Alles, was
  auf `main` gepusht wird, geht live. `.nojekyll` sorgt dafür, dass die
  Dateien unverändert ausgeliefert werden.
- Eigene Domain später über eine `CNAME`-Datei im Root.

## Projektumfang

- Nur statische Website: HTML, CSS und bei Bedarf einfaches JavaScript.
- Kein Backend, keine Datenbank, kein Build-Schritt, keine Frameworks,
  solange nicht ausdrücklich gewünscht. Die Dateien müssen so, wie sie im
  Repo liegen, auf GitHub Pages funktionieren.
- Einstiegspunkt ist `index.html` im Root.
- Alle sichtbaren Texte auf Deutsch. Keine Gedankenstriche (– oder —)
  in sichtbaren Texten.

## Regeln

- **Cache-Busting:** Ändert sich `style.css` oder `main.js`, in jeder
  HTML-Seite die Versionsnummer `?v=…` an beiden Links erhöhen (Format
  `JJJJMMTT-n`), sonst sehen Besucher alte Dateien.
- **Keine externen Dienste ohne Absprache:** keine Google Fonts, kein
  Tracking, keine eingebetteten Karten oder Videos von Drittanbietern.
  Schriften werden als `.woff2` in `assets/fonts/` selbst gehostet. So
  bleibt die Datenschutzerklärung kurz und stimmt. Kommt doch etwas
  dazu, muss `datenschutz.html` mitgeändert werden.
- **Impressum und Datenschutz** (`impressum.html`, `datenschutz.html`)
  sind Vorlagen mit Platzhaltern, keine Rechtsberatung. Vor dem Livegang
  mit den echten Angaben füllen und von der Autorin prüfen lassen.
- Bilder als JPG/WebP in `assets/images/`, vorher verkleinern (lange
  Seite höchstens etwa 1600 px), immer mit `alt`-Text, `width`/`height`
  und `loading="lazy"` außer im ersten Bildschirm.
- Barrierefreiheit: echte Überschriften-Reihenfolge, sichtbarer Fokus,
  `prefers-reduced-motion` respektieren (die Einblend-Animation ist dann aus).

## Aufbau

- `index.html`: Start, Bücher, Über mich, Lesungen und Termine, Presse,
  Kontakt.
- `impressum.html`, `datenschutz.html`, `404.html` (die 404-Seite nutzt
  absolute Pfade `/assets/...`, weil GitHub Pages sie unter jeder
  Adresse ausliefert; das stimmt erst mit eigener Domain. Unter
  `nutzer.github.io/repo/` fehlt dort das Styling.)
- `assets/css/style.css`, `assets/js/main.js` (Menü, Header beim
  Scrollen, Einblenden, Jahreszahl)
- `assets/images/`, `assets/fonts/`
- `favicon.svg`, `robots.txt`, `.nojekyll`

## Lokal ansehen

```bash
python3 -m http.server 8080
```

dann http://localhost:8080 öffnen.
