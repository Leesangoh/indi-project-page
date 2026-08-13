# INDI — Act with Intent · Project Page

Static project page for **"Act with Intent: Distilling Behavior Intent for Vision-Language-Action Models"** (under double-blind review, ICLR 2027).

Hand-rolled single page — no framework, no build step, no webfonts. One `index.html`, one stylesheet, ~50 lines of vanilla JS. Academic bones with an editorial rhythm: Charter/Georgia system serif on white, full-bleed light bands behind the demo and analysis sections, a green accent tied to the paper's own color language (the booktabs tables reuse the paper's light-green "ours" rows; the summary chart is matplotlib).

## Structure

```
.
├── index.html              # All content
├── static/
│   ├── css/style.css       # Hand-written styles (design tokens at the top)
│   ├── js/main.js          # Lazy video playback, BibTeX copy
│   ├── images/             # Figures rendered from the paper's vector sources + OG card
│   ├── videos/             # Web-encoded demo rollouts (H.264, faststart, muted)
│   ├── posters/            # Poster frames for each video
│   └── paper.pdf           # The submission PDF
└── .nojekyll
```

## Local preview

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

## Deploy (GitHub Pages)

Push to a repository and enable Pages on the root of the default branch. No build step needed.

Note: the page currently lists the authors. If the venue requires strict double-blind supplementary
material, swap the author block for "Anonymous Authors" before sharing the link with reviewers.

## Release checklist

- [ ] Point the arXiv button (`btn-soon`) at the arXiv abstract page and make it a real link
- [ ] Point the Code button at the GitHub repository
- [ ] Set absolute `og:image` / `og:url` URLs in `<head>` once the final domain is known
- [ ] `static/paper.pdf` is kept in the repo; re-add a Paper button if wanted

## Regenerating assets

Videos (from the synced composites):

```bash
ffmpeg -i in.mp4 -an -vf "scale=720:-2" -c:v libx264 -crf 24 -preset slow \
       -pix_fmt yuv420p -movflags +faststart out.mp4
```

Figures are rendered from the Overleaf `figures/*.pdf` vector sources at 2200–2400px width (PyMuPDF).
