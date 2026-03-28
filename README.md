# artist spotlight //

A client-side Spotify tool for replacing a playlist's contents with every track from a searched artist. Runs entirely in the browser — no server, no backend, no dependencies.

## what it does

1. Authenticate with your Spotify account
2. Search for an artist
3. Select one of your playlists
4. Replace that playlist's contents with the artist's full catalog (deduplicated, sorted by release date)

## setup

### 1. Spotify Developer App

You'll need a Spotify app at [developer.spotify.com/dashboard](https://developer.spotify.com/dashboard).

- Create an app if you don't have one
- Under **Edit Settings → Redirect URIs**, add your GitHub Pages URL:
  ```
  https://yourusername.github.io/your-repo-name/
  ```
- Copy your **Client ID**

### 2. Add your Client ID

In `index.html`, find this line near the top of the script and replace the placeholder:

```js
const CLIENT_ID = 'your_client_id_here';
```

### 3. Deploy to GitHub Pages

- Push `index.html` to a public GitHub repo
- Go to **Settings → Pages → Source** → select `main` branch → Save
- Your app will be live at `https://yourusername.github.io/your-repo-name/`

## local development

Open `index.html` directly in a browser, or serve it with any static file server:

```bash
npx serve .
# or
python3 -m http.server
```

Add `http://localhost` (or `http://localhost:PORT`) as an additional Redirect URI in your Spotify app settings.

## notes

- Uses the [Implicit Grant](https://developer.spotify.com/documentation/web-api/tutorials/implicit-flow) OAuth flow — no client secret is needed or used in the browser
- The replace operation is destructive and permanent — there's a confirmation prompt before anything is deleted
- Playlists and search results over 100 items are handled automatically with pagination
- Only playlists you own are shown (Spotify-curated playlists are excluded)

## originally

Ported from an R/Shiny app that used the same Spotify Web API under the hood. Rewritten as a single static HTML file for easier hosting and access.
