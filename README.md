# Chatulileo

A personal German vocabulary learning app — A1 to B1, with Leitner spaced repetition plus dedicated drill decks for articles (`der/die/das`) and verb details (full conjugation, prepositions, cases). Single-file PWA, installs to your iPhone home screen.

> Personal use only. Seed vocabulary references Hueber Verlag wordlists (Lagune 1, Lagune 3, Schwache Verben, Bellingua A2 Modul 16) for personal study — not redistributable.

## Files

- `index.html` — the entire app (CSS + JS inline)
- `data.js` — seed vocabulary (~145 cards)
- `manifest.json` — PWA install metadata
- `sw.js` — service worker for offline use
- `icon-192.png`, `icon-512.png` — home-screen icons

## Deploy to GitHub Pages

You need a free GitHub account. The whole thing takes about 5 minutes.

### 1. Create a free GitHub account
Go to **github.com** and sign up if you don't already have one.

### 2. Create a new public repository
- Click the **+** in the top-right → **New repository**
- Name it `chatulileo` (or whatever you like)
- Visibility: **Public** (required for the free GitHub Pages tier)
- Don't add a README, .gitignore, or license — leave it empty
- Click **Create repository**

### 3. Upload all the files
On the new empty repo page, click **uploading an existing file** (the link in the middle).
Drag in **all six files** from this folder:
- `index.html`
- `data.js`
- `manifest.json`
- `sw.js`
- `icon-192.png`
- `icon-512.png`
- (`README.md` is optional)

Scroll down → **Commit changes**.

### 4. Turn on GitHub Pages
- In your repo, go to **Settings** (top tab) → **Pages** (left sidebar)
- Under **Source**, pick **Deploy from a branch**
- Branch: **main**, folder: **/ (root)**
- Click **Save**

Wait about 1 minute. GitHub will build and publish the site. Refresh the Pages settings page — you'll see a green box with the URL:

```
https://YOUR-USERNAME.github.io/chatulileo/
```

### 5. Install on your iPhone
- Open that URL in **Safari** on your iPhone (it has to be Safari — Chrome on iOS can't install PWAs)
- Tap the **Share** button (square with arrow up) at the bottom
- Scroll down → **Add to Home Screen**
- Confirm the name "Chatulileo" → **Add**

The Chatulileo cat icon now appears on your home screen. Tap it — the app opens fullscreen, just like a native app, and works offline once you've opened it once.

## Updating the app later

After any edit (e.g. tweaking `data.js` to add new words), just upload the changed files to the same repo:
- Click the file in the GitHub repo → pencil icon → paste new contents → Commit.
- Or drag-drop a replacement using **Add file → Upload files**.
- Wait ~1 minute; the live site updates automatically.

If you change `index.html` and the service worker doesn't pick it up on your phone, bump `CACHE_VERSION` inside `sw.js` (e.g. `chatulileo-v1` → `chatulileo-v2`) so the old cache is cleared.

## How the app works

**Home screen** — three practice tiles plus an Alle Karten browser and a collapsible progress view.

- **Allgemein üben** (general practice): all your nouns + verbs in a single Leitner system. 5 boxes with intervals 1 / 2 / 4 / 8 / 16 days. Each day starts with up to 50 Box-1 cards (failed cards plus newly introduced ones), then everything else due that day.
- **Artikel** (articles): a mini 3-box deck (1 / 3 / 7 days) for nouns where you got the article wrong in general practice. Need 3 correct in Box 3 to graduate out.
- **Verben** (verb details): a mini 3-box deck for verbs where you marked "details wrong". Each verb tracks a personal *weakness profile* — only the parts you've gotten wrong come up next time. Conjugation, Perfekt, Präteritum, prepositions (atomic — must select all correct ones), per-preposition case, object case.

**Card flow** — front shows English; tap to flip; back shows the full German details. After flipping, three buttons:
- *Ich wusste es* → +1 Leitner box
- *Artikel falsch / Details falsch* → stays in current Leitner box, copy added to the relevant mini deck
- *Ich wusste es nicht* → drops to Box 1

**Strict typing in verb drills** — case-insensitive, and `ae/oe/ue/ss` are accepted as `ä/ö/ü/ß`. Otherwise spelling matters.

**Adding your own words** — the `+` footer button. Two tabs (Nomen / Verb). The verb form has an "Auto-fill (regelmäßig)" button that fills in regular weak conjugation for you.

**Storage** — everything lives in your browser's `localStorage`. Clearing site data wipes your progress (the seed vocab will reload, but Leitner state and your custom cards will be gone). No cloud sync.

## License / personal use

Source vocabulary (Hueber Verlag materials) is for personal study only. Don't redistribute.
