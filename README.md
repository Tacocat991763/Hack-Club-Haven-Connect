# Hack Club Haven Connect

Peer-to-peer video chat for Hack Clubbers. Share a room code, join by city. No backend.

**Demo:** [havenconnects.netlify.app](https://havenconnects.netlify.app)

## Run locally

```bash
python3 -m http.server 8742
# open http://localhost:8742
```

Must use a server — `file://` blocks camera access and WebRTC.

## How it works

- WebRTC via PeerJS 1.5.2 (free public signalling server)
- Full mesh: every peer connects directly to every other peer
- Host peer ID = room code. First joiner becomes host if original host leaves
- No data leaves the browser except the WebRTC handshake through PeerJS

## Deploy

Static folder, any host works:

```bash
npx netlify-cli deploy --dir . --prod
```

## Files

```
index.html          — entire app (HTML + CSS + JS, no build step)
images/
  bg-forest.webp    — background
  cloud-corner.webp — corner decoration
  divider.webp      — top bar
  hog-*.png         — Daven expressions (base, sleeping, winking, yawning)
```

## Daven

Hedgehog mascot, bottom-left. Blinks and yawns on his own via a randomised idle loop in `index.html` near the bottom.
