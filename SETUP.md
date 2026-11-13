# Setup

## Run locally

No install needed. Just serve the folder over HTTP:

```bash
cd haven-portal
python3 -m http.server 8742
```

Then open [localhost:8742](http://localhost:8742).

> You can't just open `index.html` as a file — browsers block camera/mic access and WebRTC on `file://` URLs. Always use a local server.

## Deploy

The site is a single static folder. Any static host works.

**Netlify (current):**
```bash
npx netlify-cli deploy --dir . --prod
```

**GitHub Pages:** push to a `gh-pages` branch or point Pages at `main /` in repo settings.

**Anywhere else:** upload the folder. That's it.

## File structure

```
haven-portal/
├── index.html          # the entire app
└── images/
    ├── bg-forest.webp  # autumn forest background
    ├── bg-village.webp # village scene (unused, alternate bg)
    ├── cloud-corner.webp
    ├── divider.webp    # decorative top bar
    ├── hog-base.png    # Daven — normal
    ├── hog-sleeping.png # Daven — eyes closed
    ├── hog-winking.png  # Daven — wink
    └── hog-yawning.png  # Daven — yawn
```

## Customising

**Change the city label:** edit the `YOUR CITY` input placeholder in `index.html`.

**Add a Daven expression:** make a new PNG at the same canvas size as `hog-base.png`, drop it in `images/`, and add it to the `frames` logic in the `<script>` block near the bottom of `index.html`.

**Change the background:** swap `images/bg-forest.webp`. The CSS variable `--bg-img` in the `:root` block controls it.

## How the WebRTC mesh works

1. Creator joins PeerJS with a room code as the "host" peer ID
2. Joiners connect to the host peer on entry
3. The host sends each new joiner the list of all current peer IDs
4. Each joiner connects directly to every existing peer
5. If the host leaves, the longest-connected peer takes over

All connections are peer-to-peer. PeerJS only handles the initial signalling handshake.
