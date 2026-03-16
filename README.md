# 🎬 *Arr Bulk Importer

A free, open-source, single-file web tool for bulk importing movies, shows, artists and indexers into your self-hosted **Radarr**, **Sonarr**, **Prowlarr** and **Lidarr** instances — all from a clean, dark UI that runs entirely in your browser.

No installation. No server. No accounts. Just open the HTML file (or visit the GitHub Pages link) and go.

---

## ✨ Features

### 🟡 Radarr
- Drag & drop CSV import for bulk movie adding
- Fetches your **quality profiles** and **root folders** live from Radarr after connecting — pick exactly where movies go
- **Director filter** — type a director name to filter your list, searches both your CSV data and Radarr's TMDB lookup
- Auto-searches TMDB by title + year if no TMDB ID is provided
- Per-row live status (queued / adding / added / exists / failed)
- Genre filter chips and title search

### 🔵 Sonarr
- Drag & drop CSV import for bulk TV show adding
- Monitor mode selector (All Seasons, First Season, Latest, Missing Episodes etc.)
- Search on add toggle
- Auto-searches TVDB by title + year if no TVDB ID is provided

### 🟢 Prowlarr
- Built-in list of **45+ indexers** — public torrents, private trackers, and Usenet
- Filter by: All / Public Only / Private Only / Torrents Only / Usenet Only
- Upload your own indexer CSV as an alternative
- **Push Prowlarr → Radarr** — syncs all your Prowlarr indexers into Radarr as Torznab/Newznab sources automatically
- **Push Prowlarr → Sonarr** — same thing for Sonarr
- **🍪 Cookie Manager** for private trackers:
  - Cards for every supported private tracker (IPTorrents, TorrentLeech, HDBits, PassThePopcorn, BTN, BeyondHD, AnimeBytes, Redacted, and many more)
  - Paste your session cookie and User-Agent per tracker
  - **Auto-strips password fields** (`oldpass`, `password`, `passwd`, `pwd`, `pass`) from cookie strings the moment you paste — with a visible notice
  - **Save & Push to Prowlarr** — if Prowlarr is connected, pushes the cookie directly to the existing indexer via the API instantly
  - Jump-to-tracker dropdown so you can quickly navigate to the right card

### 🟣 Lidarr
- Drag & drop CSV import for bulk artist adding
- Monitor mode and search-on-add selectors
- Supports MusicBrainz ID (MBID) for accurate lookups, or searches by name automatically

### All tabs
- **⬇ Template CSV** download button on every tab — gives you a correctly formatted example CSV to fill in
- Live progress bar and scrollable log during import
- Select All / Deselect All / filter chips
- Per-item status badges that update in real time
- Handles "already exists" gracefully — marks as exists, doesn't fail

---

## 🚀 How to Use

1. Download `arr-importer.html`
2. Open it in your browser
3. That's it — no install, no server, nothing to set up

---

## 📋 CSV Formats

Download ready-to-fill templates directly from the tool using the **⬇ Template CSV** button on each tab. Here are the column formats for reference:

### Radarr Movies
```csv
Title,Year,TMDB_ID,Genre,Vibe,Director
The Dark Knight,2008,155,Action/Drama,Blockbuster Hit,Christopher Nolan
Spirited Away,2001,129,Anime/Fantasy,Award Winner,Hayao Miyazaki
```

### Sonarr Shows
```csv
Title,Year,TVDB_ID,Genre,Network
Breaking Bad,2008,81189,Drama,AMC
The Bear,2022,392462,Drama/Comedy,FX
```

### Prowlarr Indexers
```csv
Name,DefinitionName,Type,Privacy
The Pirate Bay,thepiratebay,torrent,public
NZBGeek,nzbgeek,usenet,private
```

### Lidarr Artists
```csv
Artist,Genre,MBID,Origin
Taylor Swift,Pop,20244d07-534f-4eff-b4d4-930878889970,USA
Daft Punk,Electronic,056e4f3e-d505-4dad-8ec1-d04f521cbb56,France
```

> **Tips:**
> - `TMDB_ID` / `TVDB_ID` / `MBID` are optional but give instant, accurate results. Without them the tool searches by title + year.
> - Column order doesn't matter — the tool auto-detects headers (case-insensitive).
> - If headers can't be matched automatically, a column mapper UI appears so you can assign them manually.

---

## 🍪 Getting Your Cookie (Private Trackers)

Private trackers that use cookie authentication need a session cookie to work in Prowlarr. Here's how to get it:

1. **Log into the tracker** in your browser
2. Press **F12** to open DevTools → go to the **Network** tab
3. **Refresh the page**
4. Click any request to the tracker's domain → open the **Headers** tab
5. Find **`Cookie:`** under Request Headers — copy the entire value
6. Copy the **`User-Agent:`** value from the same section
7. Paste both into the Cookie Manager in the Prowlarr tab
8. Click **Save & Push to Prowlarr**

> The tool automatically strips common password-related fields (`oldpass`, `password`, `passwd` etc.) from your cookie string the moment you paste it.

---

## 🔒 Privacy & Security

- **100% client-side** — this tool is a single HTML file with no backend, no server, no tracking, no analytics, and no external dependencies beyond Google Fonts
- **Nothing is ever transmitted** to any third party — all API calls go directly from your browser to your own local *arr instances
- **Cookies and API keys** are only held in browser memory for the duration of your session and are never stored or sent anywhere except your own Prowlarr/Radarr/Sonarr instances
- **Open source** — the full code is right here in this repository, you can read every line

---

## ⚖️ Legal Notice

This tool is **just an interface** — it automates the same actions you would perform manually inside Radarr, Sonarr, Prowlarr and Lidarr. It does not download, host, or distribute any content.

- Using this tool to manage your self-hosted *arr stack is completely legal
- What you choose to download using those apps, and whether that is legal, depends on your country, the content, and how you use it — **that is your responsibility**
- This project is not affiliated with the Radarr, Sonarr, Prowlarr or Lidarr projects

---

## 🛠 Tech Stack

Just vanilla HTML, CSS and JavaScript. No frameworks, no npm, no build step. One file.

- **UI** — custom dark theme with CSS variables, Bebas Neue + DM Mono + DM Sans via Google Fonts
- **API** — standard `fetch()` calls to the v3 REST APIs of Radarr, Sonarr, Lidarr and the v1 API of Prowlarr
- **No dependencies** — nothing to install, nothing to update

---

## 🤝 Contributing

Pull requests are welcome! Some ideas for contributions:

- Duplicate checker — pre-scan your library before importing
- Rating filter — only import above a certain TMDB/IMDB score
- Year range slider filter
- Export results to CSV after a run
- Bulk retry failed imports button
- Dark/light theme toggle

If you find a bug or have a feature request, open an issue.

---

## 📄 Licence

MIT — do whatever you want with it, just don't hold the author liable.

```
MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software to deal in the Software without restriction, including without
limitation the rights to use, copy, modify, merge, publish, distribute,
sublicense, and/or sell copies of the Software, and to permit persons to whom
the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.
```

---

## ⭐ Support

If this tool saves you time, a star on the repo goes a long way!

And if you really want to show some love — you can buy me a coffee ☕

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-Drunk0Smurf-yellow?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://www.buymeacoffee.com/Drunk0Smurf)

<img src="qr-code.png" alt="Scan to buy me a coffee" width="180"/>

> No pressure at all — this tool is free and always will be. But if bulk importing 200 movies saved you an afternoon, a coffee is always appreciated. Cheers! 🍺
