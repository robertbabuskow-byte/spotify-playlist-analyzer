# Spotify Playlist Analyzer

A static, privacy-friendly browser app that authenticates with Spotify using Authorization Code with PKCE and analyzes playlists owned by or collaborative with the signed-in user.

## What it analyzes

- Track count and total runtime
- Unique artists and albums
- Top primary artists and albums
- Artist-diversity score
- Release-year and decade distribution
- Explicit-content share
- Duplicate tracks
- Playlist additions over time
- Track-level export-style table
- Plain-English summary based on computed metrics

The analyzer deliberately does not claim to measure mood, energy, danceability, or valence unless reliable audio-feature data is available. Spotify may restrict those endpoints for newer applications.

## Setup

1. Create an app in the Spotify Developer Dashboard.
2. Serve this folder from a local web server. Do not open `index.html` directly as a `file://` URL.
3. Open the analyzer in your browser and copy the displayed Redirect URI.
4. Add that exact Redirect URI to your Spotify app settings.
5. Paste the app Client ID into the analyzer and connect Spotify.
6. Paste a Spotify playlist URL. Under Spotify's current API rules, playlist items must come from a playlist you own or collaborate on.

## Run locally

Using Python:

```bash
cd spotify-playlist-analyzer
python3 -m http.server 8080
```

Then visit:

```text
http://127.0.0.1:8080/
```

Add this exact redirect URI in Spotify's dashboard:

```text
http://127.0.0.1:8080/
```

## Security

- Uses PKCE, so no Spotify client secret is embedded in browser code.
- Client ID and OAuth token are stored in the current browser's local storage.
- No server receives playlist data.

## Files

- `index.html` — interface
- `styles.css` — responsive design
- `app.js` — OAuth, API pagination, calculations, and report rendering
