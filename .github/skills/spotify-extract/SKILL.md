---
name: spotify-extract
description: "Extract Spotify track metadata (image, link, preview audio, title) from a track URL and add it to the DJ Yovan website. Use when: adding a new Spotify promo card, extracting Spotify track data, adding music to the website."
argument-hint: 'Paste a Spotify track URL (e.g. https://open.spotify.com/track/...)'
---

# Spotify Track Extraction

Extract metadata from a Spotify track URL and add it as a promo card entry to `index.html`.

## When to Use

- Adding a new Spotify track/song to the DJ Yovan website
- Extracting cover art, preview audio, and title from a Spotify URL
- Populating the `spotifyPromoCards` array with a new entry

## Input

The user provides a Spotify track URL in the format:
```
https://open.spotify.com/track/<TRACK_ID>
```

If the user hasn't provided a URL, ask them to paste one.

## Procedure

### 1. Validate the URL

Confirm the URL matches the pattern `https://open.spotify.com/track/<ID>`. Extract the track ID.

### 2. Fetch oEmbed Data

Fetch the Spotify oEmbed endpoint to get the track title and thumbnail:
```
https://open.spotify.com/oembed?url=https://open.spotify.com/track/<TRACK_ID>
```

Extract from the JSON response:
- `title` → used for the card title (append " - Spotify Promo")
- `thumbnail_url` → extract the image hash (format: `ab67616d00001e02<hash>`)

### 3. Build the Image URL

Convert the thumbnail hash to the standard Spotify CDN format:
```
https://i.scdn.co/image/ab67616d00001e02<HASH>
```

### 4. Extract the Preview Audio URL

Fetch the Spotify embed page HTML:
```
https://open.spotify.com/embed/track/<TRACK_ID>
```

Search the HTML for a URL matching the pattern:
```
https://p.scdn.co/mp3-preview/<HEX_STRING>
```

If no preview URL is found, set `audioUrl` to an empty string `""`.

### 5. Assemble the Card Object

Build the promo card object:
```javascript
{
    imageUrl: "https://i.scdn.co/image/ab67616d00001e02<HASH>",
    linkUrl: "https://open.spotify.com/track/<TRACK_ID>",
    audioUrl: "https://p.scdn.co/mp3-preview/<PREVIEW_HASH>",
    title: "<Track Title> - Spotify Promo"
}
```

### 6. Add to index.html

Insert the new entry at the **top** of the `spotifyPromoCards` array in `index.html` (after `const spotifyPromoCards = [`), so the newest track appears first.

### 7. Confirm

Show the user the assembled card object and confirm it was added to the file.

## Output Format

```javascript
{
    imageUrl: "https://i.scdn.co/image/ab67616d00001e02...",
    linkUrl: "https://open.spotify.com/track/...",
    audioUrl: "https://p.scdn.co/mp3-preview/...",
    title: "Track Name - Spotify Promo"
}
```

## Notes

- The `ab67616d00001e02` prefix in image hashes corresponds to Spotify's 300x300 album art size
- Preview audio URLs may not be available for all tracks (Spotify has been limiting these)
- The `linkUrl` uses the original track URL provided by the user
