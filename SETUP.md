# Wiring plan — build this invitation with Claude Code

This repo holds the complete invitation plus its artwork. Claude Code can
upload the artwork into a new artifact and publish it, so you get the real
thing — scenes, envelope and all — not an approximation.

**Why Claude Code and not the phone app:** an artifact can only load images
from its own asset store, a `data:` URI, or a `blob:`. Its sandbox sets
`img-src <the artifact's own domain> data: blob:` — so no GitHub link, no CDN,
no external URL will ever render inside it. Claude Code can upload files into
that asset store. The phone app generally cannot, which is why a pasted prompt
gives you the layout but bare backgrounds.

---

## What you need

- Claude Code installed, signed in to an account that can publish artifacts
- This repo cloned locally

```
git clone https://github.com/HirajG/wedding-invite-generator.git
cd wedding-invite-generator
claude
```

---

## The prompt — paste this into Claude Code

```
Read SETUP.md and template/invite.html in this repo, then build me my own
wedding invitation from it.

STEP 1 — ask me, in one numbered message, and then wait:
  1. The couple's first names, and how to write them together
  2. Both sets of parents' names, as they should appear
  3. Every ceremony: name, day, date, start time, venue, dress code, and
     whether it is day or night. Any number, in the order I want them.
  4. The main wedding date and time
  5. The venue name and full address
  6. A WhatsApp number for RSVP, with country code
  7. Any photos of my own I want to use, and which slot each belongs in
  8. A colour direction, or choose one

I am not technical, so keep it simple and tell me I can skip anything.

STEP 2 — build it:
  - Start from template/invite.html. Keep its structure, animations, scroll
    behaviour and timing exactly. Change only the content.
  - Publish it as a new artifact with capabilities {"assets": {}}.
  - Upload every file in assets/ to that artifact. Replace each
    ASSET:<name> placeholder in the HTML with the /_blob/<id> url the upload
    returns. There are 13 of them and every one must be replaced — if any
    ASSET: string is still in the file, the page will show a broken image.
    Twelve are in `<img src="...">`; the thirteenth, ASSET:envelope, sits
    inside a CSS `url(...)` on the cover element, so a search for `src=`
    alone will miss it.
  - If I gave you my own photos, upload those in place of the matching
    default and use the same wiring. Resize anything over ~1200px on its
    long edge first, and crop rather than squash.
  - If I have more ceremonies than there are scene images, reuse the closest
    scene by time of day. If I have fewer, drop the extra sections.

STEP 3 — hand it over:
  - Tell me the artifact is private and my guests cannot open it yet.
  - Walk me through making it shareable, step by step.
  - Tell me to test the link in a private window before I send it to anyone.
  - Then stay with me so I can change details and republish to the same url.
```

---

## What is in here

| path | what it is |
|---|---|
| `template/invite.html` | the whole invitation, one file, with `ASSET:<name>` placeholders |
| `assets/*.webp` | the 13 images the template expects |
| `PROMPT.txt` | the long written spec, for building without this repo |

### The 13 assets and where each one goes

| placeholder | file | used for |
|---|---|---|
| `ASSET:envelope` | `assets/envelope.webp` | the sealed cover you tap to open |
| `ASSET:scene-night` | `assets/scene-night.webp` | default night backdrop |
| `ASSET:scene-mayra` | `assets/scene-mayra.webp` | mayra, morning |
| `ASSET:scene-mayra2` | `assets/scene-mayra2.webp` | mayra, afternoon |
| `ASSET:scene-mehendi` | `assets/scene-mehendi.webp` | mehendi |
| `ASSET:scene-haldi` | `assets/scene-haldi.webp` | haldi |
| `ASSET:scene-sangeet` | `assets/scene-sangeet.webp` | sangeet, night |
| `ASSET:scene-pheras` | `assets/scene-pheras.webp` | pheras, firelight |
| `ASSET:scene-reception` | `assets/scene-reception.webp` | reception |
| `ASSET:couple-portrait` | `assets/couple-portrait.webp` | arched photo above the names |
| `ASSET:moment-her` | `assets/moment-her.webp` | Our Story, first frame |
| `ASSET:moment-him` | `assets/moment-him.webp` | Our Story, second frame |
| `ASSET:moment-us` | `assets/moment-us.webp` | Our Story, third frame |

---

## Checks before you send the link out

1. **No `ASSET:` left in the published page.** One missed placeholder is one
   broken image. Search the file for `ASSET:` before publishing.
2. **Open it on a phone.** It is built phone-first; a desktop window hides
   problems a tall screen will show.
3. **Open the link in a private window.** That is the only honest test of
   whether sharing is actually on.
4. **Tap every button.** Add to calendar, Get directions, Copy address, RSVP.
   The RSVP number is a placeholder in the template — replace it or remove
   the block.

## Notes

- The default photographs are of a fictional couple and are there so the
  invitation looks finished before you add your own. Replace them.
- Total artwork is about 2.2MB. Keep it near that — much heavier and the
  backdrop cross-fades start to stutter on older phones.
