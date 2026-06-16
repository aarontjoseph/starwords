# ⭐ Star Words ⭐

A 2D phonics space shooter starring **Star Bear** and **Zeebrina**. Words fly in
towed by a saucer — blast the **silent E** (bake, kite, rope…) or the **quiet
second vowel** (foam, beam, boat…) out of the word, then say it out loud!
The game speaks each word with the Web Speech API to reinforce pronunciation.

## Play locally

```sh
python3 -m http.server 4173
# open http://localhost:4173
```

## Controls

- **← / →** or **A / D** (or drag on touch) — fly
- **Space / ↑** (or tap) — shoot
- **P** — pause

## Rules of the galaxy

- Hit the sneaky letter → points, streak multiplier, and the word is spoken aloud
- After every word, the kid must **say it out loud** — a grown-up taps
  **“✅ I SAID IT!”** (or presses Space/Enter) to continue; **🔊 HEAR IT** replays it
- Hit the wrong letter → streak resets; after 2 misses the target pulses gold as a hint
- Let a word fly past → lose a shield (you have 3); shields refill each level
- **Campaign:** 6 levels of 5 words, planet-to-planet on the Star Map —
  Bakery Moon → Foamia → Kite Belt → Boat Nebula → Seed Star → **CHRONUS**,
  the word pirate (silhouette placeholder until his art arrives). Each level is
  faster; clearing one earns a celebration screen with both characters
- Shields down → retry the same planet

## Hosting

100% static — no build step, no dependencies. Deploy the folder anywhere:
GitHub Pages, Netlify Drop (drag the folder onto https://app.netlify.com/drop),
Cloudflare Pages, or any web server.

## Tech / performance

- Single `index.html`, canvas 2D, `requestAnimationFrame`
- Object pools for bullets & particles (zero per-frame allocation)
- Ships pre-rendered once to offscreen canvases; character art chroma-keyed
  off its background at load via border flood-fill
- DPR-capped rendering, pauses on tab blur

Deep links (handy for testing): `?pilot=bear|zeeb` skips the menu;
add `&lv=N` to open the map at level N, `&go` to jump straight into the level.
