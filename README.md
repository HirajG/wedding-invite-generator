# Wedding Invite Generator

An interactive digital wedding invitation you open on your phone and scroll
through — not a PDF. Tap the seal and the envelope unfolds. Pull the tassel and
the date is revealed. Every ceremony takes over the whole screen, and the page
travels from morning to night as you scroll.

Made by **Hiraj Gajera** — [@hiraj.ai](https://instagram.com/hiraj.ai)

**Live example:** https://claude.ai/artifact/EmBZBSf7STcRge4BJ5Agvg

---

## Make your own

1. Open [`PROMPT.txt`](PROMPT.txt), copy all of it.
2. Paste it into a new Claude chat — the phone app or claude.ai.
3. Answer the questions it asks: names, dates, venues, your ceremonies, photos.
4. It builds your invitation and tells you how to share it.

You do not need to know any code. You do not need this repository — the prompt
is enough. Everything here is just for people who want to look under the hood.

---

## What's in here

| | |
|---|---|
| `PROMPT.txt` | the prompt to paste into Claude |
| `template/wedding-invite-template.html` | the complete working invitation, one file |

The template runs on its own — open it in any browser. It has no photos in it:
every ceremony is drawn with gradients and light instead, so you can see the
structure before you add your own pictures.

## How it is built

- **One fixed stage behind everything.** The background is not a stack of
  cards. As you scroll, whichever section is nearest the middle of the screen
  takes over the whole stage and cross-fades into place.
- **Day and night follow the ceremonies.** Morning functions get sunlit skies,
  evening ones get moon and stars, so the page moves from day to night.
- **The scrim is anchored to the viewport, not the artwork** — so text stays
  readable no matter how a photo crops on a given phone.
- **Photos crop, they never squash.**
- Honours `prefers-reduced-motion`.
- Any number of ceremonies, in any order. Nothing is hardcoded to five.

## Licence

MIT — see [`LICENSE`](LICENSE). Use it for your own wedding, or a client's.
A credit is appreciated but not required.
