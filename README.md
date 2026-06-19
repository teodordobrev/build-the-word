# 🦉 Build the Word

A cheerful, offline-friendly **spelling game for kids aged 4–7** learning to read English. Drag letter tiles to build a word, and an obscured picture is revealed as you go. Works great on an **iPhone or iPad** (and any modern browser), and can be installed to the Home Screen as a full-screen app.

> Vocabulary is adapted from the common CEFR/A1-level and Cambridge kids book word list — ~170 words across topics like school, animals, food, toys, sports, clothes and the beach.

- **Single file**, no build step, no dependencies — the whole game is one `index.html`.
- **Offline-capable PWA** — install it once and play with no internet.
- **Free and open** — MIT licensed; fork it, change the words, deploy your own.

## ▶️ Play it

If you've deployed it (see below), it lives at:

```
https://<your-github-username>.github.io/build-the-word/
```

## 📱 Install on iPhone / iPad

1. Open the link above in **Safari**.
2. Tap the **Share** button (the square with the arrow).
3. Tap **Add to Home Screen** → **Add**.
4. Launch it from the new 🦉 icon — it runs full-screen like a real app and works offline.

> Tip: tap the speaker 🔈 to mute/unmute. The first tap on any screen unlocks sound and speech on iOS.

## 🎮 How to play

- Tap **Play**, then pick a level from the forest trail map.
- **Drag or tap** letter tiles to fill the slots and spell the word.
- Tap an already-placed letter to **send it back** to the tray.
- When the last slot is filled, the word is checked: get it right and the picture is revealed with confetti ⭐; get it wrong and the slots clear so you can try again.
- Two hints per word: 👁 reveals more of the picture, **A?** drops the next correct letter in.
- Words that don't have a clear picture (rooms, actions, phrases) show a friendly **topic card** instead.

## 💻 Run locally

It's just static files — no server or install needed.

```bash
# easiest: open the file directly
open index.html        # macOS

# or serve it (recommended, so the service worker / offline mode works)
python3 -m http.server 8000
# then visit http://localhost:8000
```

## 🚀 Deploy your own (free, via GitHub Pages)

This repo includes a GitHub Actions workflow that publishes the site automatically.

1. **Fork** this repository (or push your copy to a new repo).
2. In your repo, go to **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **GitHub Actions**.
4. Push to `main` (or run the **Deploy to GitHub Pages** workflow from the Actions tab).
5. After it finishes, your game is live at `https://<your-username>.github.io/<repo-name>/`.

> Prefer no workflow? You can instead pick **Deploy from a branch → `main` / `/ (root)`** under Settings → Pages. All asset paths are relative, so it works from any subpath.

Because the app uses relative URLs and a service worker scoped to `./`, it works whether it's hosted at a domain root or in a `/repo-name/` subfolder — Netlify, Cloudflare Pages, Vercel, or any static host will also work.

## ✏️ Customize the word list

Open `index.html` and find the `WORDLIST` array near the top of the `<script>`:

```js
const WORDLIST = [
  ["CAT", "🐱"],
  ["PENCIL CASE", "#school"],   // "#category" shows a topic card instead of an emoji
  ...
];
```

- `["WORD", "🙂"]` — spell `WORD`, reveal that emoji as the picture.
- `["WORD", "#category"]` — no clear emoji, so show a text/topic card. Categories: `school, body, animal, food, toy, place, sport, action, home, clothes, beach, family`.
- Spaces and hyphens (e.g. `PLAY FOOTBALL`, `T-SHIRT`) are auto-filled — kids only place A–Z letters.

Levels are generated automatically: words are sorted by length and grouped 6 per level, with the picture-obscuring effects (blur → silhouette → peephole → falling tiles) getting harder as you climb. **Bump the `CACHE` version string in `sw.js`** after editing so returning players get the update.

## 🗂️ What's in here

| File | Purpose |
|------|---------|
| `index.html` | The entire game (HTML + CSS + JS, inline). |
| `manifest.webmanifest` | PWA metadata (name, icons, colors). |
| `sw.js` | Service worker for offline play. |
| `icon-192.png`, `icon-512.png`, `icon.svg`, `apple-touch-icon.png` | App icons. |
| `.github/workflows/deploy.yml` | Auto-deploy to GitHub Pages. |

## 📄 License & credits

Code is released under the [MIT License](LICENSE) — use, modify, and deploy freely.

The vocabulary is adapted from thethe common CEFR/A1-level and Cambridge kids book word list. Only the plain list of common English words was used to build the game. All related marks/trademarks belong to their respective owners. This is an independent, non-commercial educational project and is not affiliated with or endorsed by anyone.

Emoji artwork is rendered by the player's own device/operating system.
