# Hack Club Haven Connect

A cozy WebRTC video portal where Hack Clubbers can find each other by city and hang out face-to-face. No accounts, no servers — just a room code and a forest.

## What it does

- Enter your city and create a portal, or join one with a room code
- Peer-to-peer video and audio via WebRTC (PeerJS)
- Full mesh — everyone sees everyone, no central relay
- Room codes are shareable; anyone with the code can join

## Live site

**[havenconnects.netlify.app](https://havenconnects.netlify.app)**

## Stack

| Thing | What |
|---|---|
| `index.html` | The whole app — HTML, CSS, and JS in one file |
| PeerJS 1.5.2 | WebRTC signalling + peer connections |
| Images | Forest background + Daven the hedgehog mascot |

No build step, no dependencies to install.

## Daven

The hedgehog in the bottom-left corner. He blinks, winks, and yawns on his own. Leave the tab open long enough and you'll catch a yawn.
