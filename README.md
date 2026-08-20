# for Mar 💕

A single-page, Three.js interactive site — house exterior → 360° foyer with a
date-quiz box → photo room with a birthday letter → rose room with a voice
message → the ask.

No build step, no framework, no dependencies to install. It's one static
`index.html` (Three.js loads from a CDN in the browser).

## Project structure

```
mari-project/
├── index.html        the entire site
├── audio/             drop your own audio files in here (see below)
│   └── .gitkeep
├── vercel.json         tells Vercel this is a static site, no build needed
├── .gitignore
└── README.md
```

## Before you deploy — add your audio

Create these three files inside the `audio/` folder, using exactly these
names (the code already looks for them):

| File | What it's for |
|---|---|
| `audio/happy-birthday.mp3` | plays in the photo room |
| `audio/all-of-me.mp3` | plays in the rose room |
| `audio/voice-message.mp3` | your recorded voice message |

The site still works without them — those steps just play silently, and the
voice-message screen shows a "continue" button automatically if the file
isn't found.

## Push to your repo

```bash
cd mari-project
git init
git add .
git commit -m "for Mar"
git branch -M main
git remote add origin https://github.com/nahombrook/YOUR-REPO-NAME.git
git push -u origin main
```

## Deploy on Vercel

**Option A — dashboard (easiest):**
1. Go to vercel.com → **Add New → Project**
2. Import the GitHub repo you just pushed
3. Framework preset: choose **Other** (it's static — no build command needed)
4. Deploy

**Option B — CLI:**
```bash
npm i -g vercel
cd mari-project
vercel
```
Follow the prompts (link to your Vercel account, accept the defaults). It'll
give you a live URL immediately, and a production one after `vercel --prod`.

Because there's no build step, deploys are fast — usually live in under a
minute.

## Mobile

Fully responsive — tested against phone-sized viewports. Touch drag looks
around the 360° rooms, tap selects things, pinch-zoom and page-scroll are
disabled so it behaves like an app rather than a webpage. One thing to know:
mobile browsers (especially iOS Safari) sometimes block audio from
autoplaying without a direct tap — the voice-message screen already requires
a tap to play for this reason, but the background music (birthday song,
"All of Me") might occasionally need that first tap too rather than starting
instantly the moment the room loads. It'll still play, just possibly a beat
later than on desktop.

## Editing the content

Everything you're likely to want to change — the welcome text, the date
quiz's correct answer, the location question's answer, the birthday letter,
the final message, audio file paths — lives in one place near the top of the
`<script>` block in `index.html`, in the `CONFIG` object. No need to touch
anything below it for text/date changes.
