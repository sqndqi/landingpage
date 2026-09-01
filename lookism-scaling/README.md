# Lookism Scaling Index

A structured power-scaling reference for **Lookism** (Park Tae-joon) — character
dossiers, an explicit feat chain, a tier ladder and a head-to-head comparator.

Open `index.html` in a browser. No build step, no dependencies, no server.

## What's in it

- **21 dossiers** across four bands — apex, God tier, high tier and mid tier —
  with stat lines quoted from VS Battles Wiki and 45 feat cards.
- **The scaling chain** — five steps from the verse's one quantified anchor up to
  the apex, each tagged for whether it rests on on-page evidence, inference, or
  the author's own read.
- **Relation graph** — every on-page comparison the ladder is built from, drawn
  as a network. Hover a node to isolate its edges, click to open the dossier. A
  degree count underneath names the load-bearing nodes and the placements that
  hang off a single comparison.
- **Arc-by-arc timeline** from the 1st Generation through to DG's return.
- **Per-character key selector** — 13 separately-rated versions across 10
  fighters, each merging over the character's base stat block.
- **Chapter fields** on every feat card, saved to your browser, so citations
  become real as you fill them in.
- **Tier list builder** — drag fighters into S/A/B/C/D rows, saved to your
  browser. Seed it from the site's ladder and then disagree with it.
- **Bracket simulator** — eight fighters resolved by band gap, then unbounded
  escalators, then ladder order. Every call shows its reasoning, and genuine
  coin flips are labelled as such.
- **Tier ladder**, **comparator**, and a **method section** that states where the
  argument is weakest rather than hiding it.

## Adding panels

Every feat card is a drop target. Drag an image onto it, or click to browse.

Images are stored in your **own browser** (`localStorage`) — not uploaded, not
committed, not part of git history. A personal reading copy stays personal.

- **Export panel set** writes your panels to a JSON file for backup or transfer.
- **Import panel set** reads one back in.
- Roughly 5MB of browser storage is available; resize large scans first. The
  counter in the panel manager shows current usage.

To commit an image normally instead, put it in `panels/` and add a
`file:"panels/name.jpg"` field to that feat in the `CHARS` data block near the
bottom of `index.html`. Committed images load automatically and are used until
something is dropped on top of them.

Use panels you have the right to use, and credit the author. Official English
chapters are on WEBTOON. Citing the chapter beside a panel is what makes a
scaling claim checkable rather than merely asserted.

## Accuracy

Tier ratings are quoted from VS Battles Wiki, which revises Lookism tiers
regularly — treat every rating as a dated snapshot. The chain, the ladder
placements and the matchup verdicts are the author's own reasoning.

Two things are flagged in the page itself:

- The Younger Goo dual-wield exchange that anchors the verse's Supersonic band is
  cited inconsistently across wiki profiles as to whose feat it is. The resulting
  band holds under either reading.
- Feat cards ship with **era and arc tags, not chapter numbers**. A fabricated
  citation is worse than none, because it looks checkable and isn't — so each
  card has an editable chapter field for you to fill in from your own reading.
  Whatever you type is saved to your browser alongside the panels.

## Licence / affiliation

Unofficial fan analysis. No affiliation with Park Tae-joon, WEBTOON or any
publisher. All character names and story events belong to their rights holders.
