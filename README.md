# DJ Yovan — Official website

Static site with Bandcamp embeds. This repository contains the site source (HTML/CSS/JS) and assets.

Preview

- Open `index.html` in a browser to preview locally.

Development notes

- Bandcamp embeds are defined in the `bandcampTracks` array inside `index.html` and are rendered dynamically by the included script.
- To add a new track, add an object with { iframeTitle, playerSource, songUrl, songName } to the array or call `addBandcampTrack(...)` in the browser console.

License

This repository contains assets and code provided by the project owner.
