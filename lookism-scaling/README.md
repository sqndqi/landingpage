# Lookism Scaling Index

A structured power-scaling reference for **Lookism** (Park Tae-joon) — character
dossiers, an explicit feat chain, a tier ladder and a head-to-head comparator.

Open `index.html` in a browser. No build step, no dependencies, no server.

## What's in it

- **Dossiers** for James Lee (DG), Gun Park, Goo Kim, Daniel Park's 2nd body,
  Taesoo Ma, Gongseob Ji and Sinu Han — stat lines quoted from VS Battles Wiki.
- **The scaling chain** — five steps from the verse's one quantified anchor up to
  the apex, each tagged for whether it rests on on-page evidence, inference, or
  the author's own read.
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

One thing is flagged in the page itself: the Younger Goo dual-wield exchange
that anchors the verse's Supersonic band is cited inconsistently across wiki
profiles as to whose feat it is. The resulting band holds under either reading.

## Licence / affiliation

Unofficial fan analysis. No affiliation with Park Tae-joon, WEBTOON or any
publisher. All character names and story events belong to their rights holders.
