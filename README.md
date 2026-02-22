# Today's Brief

A daily business & tech news podcast, generated each morning from a curated email newsletter.

## How it works

1. **`text_to_podcast.py`** fetches the day's Headlines email via Gmail, summarizes it with Claude, and converts it to audio with ElevenLabs TTS.
2. Episode metadata (title, description, date, audio URL) is written to `episodes.json`.
3. **`index.html`** reads `episodes.json` and renders the episode list with embedded audio players.

## File structure

```
website/
├── index.html          # Static podcast website
├── episodes.json       # Episode metadata — update this for each new episode
├── podcast_cover.png   # Cover art (3000×3000px)
└── README.md
```

## Adding an episode

Add an entry to the **top** of `episodes.json` (newest first):

```json
{
  "date": "2026-02-22",
  "title": "Today's Brief - February 22, 2026",
  "description": "One or two sentences highlighting the top stories.",
  "audio_url": "https://your-host.com/audio/podcast-2026-02-22.mp3"
}
```

`audio_url` should be a publicly accessible URL. Audio files can be hosted on GitHub (if under 100 MB), AWS S3, Cloudflare R2, or any static file host.

## Deploying to GitHub Pages

1. Push this folder to a GitHub repository.
2. Go to **Settings → Pages** and set the source to the branch/folder containing these files.
3. Your site will be live at `https://<username>.github.io/<repo>/`.

## Running locally

```bash
cd website
python3 -m http.server 8080
# open http://localhost:8080
```

> The site uses `fetch()` to load `episodes.json`, so it must be served from a server — not opened directly as a `file://` URL.
