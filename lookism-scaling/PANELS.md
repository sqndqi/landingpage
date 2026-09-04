# Panel Integration Spec

Handoff document for anyone — human or AI — attaching panel images to this
site. The scaling content is complete; images are the only thing missing.

## Context

| | |
|---|---|
| Repo | `github.com/sqndqi/lookism-scaling` (private) |
| File | `index.html` — single self-contained page, no build step, no dependencies |
| Mirror | `sqndqi/landingpage`, branch `claude/lookism-scaling-website-ndkwb0`, under `lookism-scaling/` |

21 character dossiers, 45 feat cards, a scaling chain, relation graph, arc
timeline, tier ladder, tier-list builder, bracket simulator, and a comparator
with 61 written matchup verdicts.

## Task

Attach panel images to the 45 feat cards. **The user supplies the image files.**

Do not source, download, or scrape artwork from WEBTOON, hivetoons, or any scan
aggregator — that redistributes Park Tae-joon's copyrighted work. Work only with
files the user provides.

## Architecture

Every feat lives in the `CHARS` array in the `<script>` block near the bottom of
`index.html`:

```javascript
{id:"james-taesoo",
 era:"1ST GEN",
 cap:"Taesoo Ma loses his right eye",
 title:"Permanently marked the apex",
 text:"Ma carries that injury for the rest of the series...",
 w:"Weight: high · attack potency"}
```

`id` is the slot key, used by localStorage, the panel renderer and the
checklist. **Never change an id** — it orphans any panel already saved.

### Two ways an image reaches a slot

**1. Committed file.** Put the image in `panels/` and add a `file` field:

```javascript
{id:"james-taesoo",
 era:"1ST GEN",
 cap:"Taesoo Ma loses his right eye",
 file:"panels/james-taesoo.jpg",     // <-- add this
 title:"Permanently marked the apex",
 text:"...",
 w:"Weight: high · attack potency"}
```

`paintSlot()` reads `store[id] || feat.file`, so a committed file renders
automatically and stays until something is dropped on top. Name files after the
slot id to keep them traceable.

**2. Runtime drop** (the user's path — already built, do not rebuild).
Every `.slot` is a drop target. Dropped images pass through `shrink()`, which
clamps the longest edge to `MAX_EDGE` (1100px) and re-encodes as JPEG at
`JPEG_Q` (0.82), then saves to localStorage under the slot id. Measured:
7159 KB in, 283 KB out.

## Constraints

- **localStorage caps near 5MB total.** Runtime drops are downscaled to fit.
  Committed files are **not** — resize those yourself. Target ~1100px longest
  edge, JPEG, under ~150KB each.
- **Do not remove `shrink()`.** It exists because the quota blew out at a
  handful of raw screenshots.
- **Do not alter the rollback in `readInto()`.** On a quota failure it restores
  the slot's previous value; without it a failed save clobbers the panel.
- **The page is deliberately single-theme dark.** It paints its own background
  from tokens. Do not add a light theme.

## The 45 slots

Ids follow `character-feat`.

| Character | Slot ids |
|---|---|
| James Lee | `james-kings`, `james-taesoo`, `james-legs`, `james-path` |
| Kitae Kim | `kitae-god`, `kitae-jinyoung` |
| Gun Park | `gun-goo`, `gun-stalemate`, `gun-ui` |
| Goo Kim | `goo-moonlight`, `goo-gun`, `goo-younger` |
| Daniel Park | `daniel-arms`, `daniel-adapt`, `daniel-ui` |
| Charles Choi | `charles-prime`, `charles-tom`, `charles-geniuses` |
| Taesoo Ma | `taesoo-eye`, `taesoo-king` |
| Gongseob Ji | `gongseob-leg` |
| Tom Lee | `tom-jinyoung` |
| Jinyoung Park | `jinyoung-plate`, `jinyoung-kitae` |
| Johan Seong | `johan-stated`, `johan-copy` |
| Samuel Seo | `samuel-jake`, `samuel-eli` |
| Jake Kim | `jake-sinu`, `jake-vasco`, `jake-gun` |
| Sinu Han | `sinu-band` |
| Vasco | `vasco-class5`, `vasco-forbidden` |
| Seokdu Wang | `seokdu-headbutt`, `seokdu-cluster` |
| Eli Jang | `eli-keys`, `eli-beast`, `eli-samuel` |
| Zack Lee | `zack-statues` |
| Vin Jin | `vinjin-chains`, `vinjin-range` |
| Olly Wang | `olly-cluster` |
| Xiaolung | `xiaolung-cheon`, `xiaolung-jake` |

Each feat's `cap` field states exactly what the panel should show. Read it
before placing an image — match the moment, not just the character. That
caption is what the reader sees underneath.

## Chapter citations

Each card has an editable chapter input, persisted to localStorage under `CKEY`.
The page ships **no** chapter numbers by design: an unverifiable citation looks
checkable and isn't, which undermines the one thing the page is for. If the user
supplies verified chapter numbers, hardcoding them is fine. **Do not invent
them.**

## Checklist

The panel manager renders a live checklist of all 45 slots grouped by character,
showing era tag, caption, filled state and chapter number, with an
"N of 45 filled" counter. It stays in sync by wrapping `usage()`. Committed
files are reflected automatically — no extra work.

## Verify before calling it done

Run headless (Playwright was used previously):

- all 21 roster tabs render, 45 slots present across them
- every committed `file` path resolves and renders an `<img>`
- checklist counter matches the number of filled slots
- a runtime drop still downscales and persists across reload
- no console or page errors

## Mirror the change

The site lives in two repos and must stay identical. The hosted copy is
republished from the same file. Keep all three in step.

## Do not

- Source images from scan sites. User-supplied only.
- Rename slot ids.
- Fabricate chapter numbers.
- Remove the downscaler or the quota rollback.
- Restructure the scaling content. The verdicts, chain and confidence labels are
  deliberate; the method section states the argument's weak points on purpose.
