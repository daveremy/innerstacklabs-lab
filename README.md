# Inner Stack Labs · Lab

Source for **https://lab.innerstacklabs.com**, the publishing home of Inner Stack Labs: decks, papers and field notes.

## How it is hosted
- Spacesheep Pro space `998b9ee9-47b4-46f8-ac33-f8ff77a7841b` (account davidlremy@gmail.com), public.
- Custom domain `lab.innerstacklabs.com`: Cloudflare zone innerstacklabs.com has `CNAME lab → domains.spacesheep.io` (DNS only, grey cloud) and `TXT _spacesheep.lab` (domain verification). Do not proxy the CNAME.

## Layout
```
site/
  index.html              landing page
  paper-latex.css         LaTeX-style layer loaded by every paper
  agent-scrum/            paper (index.html), deck/ (web deck), deck.pdf, agent-scrum.pdf, og-cover.png
  persistent-agents/      paper, deck/ (pdf.js viewer over deck.pdf), PDFs, og-cover.png
  .spacesheep.json        pins the folder to the space above
```

## Deploy
From the `site/` folder:
```
npx -y spacesheep@1.34.0 deploy . -m "<what changed>"
```
`.spacesheep.json` names the space, so a deploy updates the live site. Check afterwards that `curl -sI https://lab.innerstacklabs.com/` returns 200.

## Papers
Each paper's canonical source is its own repo (github.com/daveremy/agent-scrum, github.com/daveremy/persistent-agents). This repo carries a copy with lab URLs and two edits: a `<link>` to `/paper-latex.css` and a `labbar` nav above `<article>`. When a paper gets a new version, copy `docs/index.html` and the PDFs over, then re-apply those two edits.

## Adding a publication
Make a folder under `site/` with the deck first and the paper second, then add a card to `site/index.html`.
