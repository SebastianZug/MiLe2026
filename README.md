# MiLe 2026

Website zum **2. Workshop „Autonome Mikromobilität und smarte Logistik auf der letzten Meile"** —
5. November 2026, Deutsches Technikmuseum in Berlin.

Der Workshop wird gemeinsam mit der mFUND-Begleitforschung durchgeführt.

## Inhalt

| Datei | Beschreibung |
|---|---|
| `index.html` | Die Website (kein Build-Schritt, kein Framework) |
| `cfp-de.pdf` / `cfp-en.pdf` | Call for Papers, deutsch und englisch |
| `preview-de.jpg` / `preview-en.jpg` | Titelseiten-Vorschau für die Download-Karten |
| `logos/` | Logos der beteiligten Institutionen |

Die LaTeX-Quellen der PDFs liegen außerhalb dieses Repositories im Projektordner
(`Call_for_Paper_2026/PDF/`).

## GitHub Pages aktivieren

1. Im Repository unter **Settings → Pages**
2. Bei *Source* **Deploy from a branch** wählen
3. Branch `main`, Ordner `/ (root)` — speichern

Die Seite ist anschließend unter <https://sebastianzug.github.io/MiLe2026/> erreichbar
(der erste Build dauert ein bis zwei Minuten).

## PDFs aktualisieren

Nach Änderungen an den LaTeX-Quellen im Projektordner:

```bash
# im Ordner Call_for_Paper_2026/PDF/
xelatex cfp-de.tex && xelatex cfp-de.tex     # zweimal wegen Seitenzählung
xelatex cfp-en.tex && xelatex cfp-en.tex

# PDFs und Vorschaubilder ins Repository übernehmen
cp cfp-de.pdf cfp-en.pdf /pfad/zu/MiLe2026/
for l in de en; do
  convert -density 150 "cfp-$l.pdf[0]" -background white -alpha remove \
          -resize 800x -quality 92 "/pfad/zu/MiLe2026/preview-$l.jpg"
done
```

Anschließend committen und pushen — Pages baut automatisch neu.

## Einreichung

Beiträge werden über EasyChair eingereicht:
<https://easychair.org/conferences/?conf=mile2026>
