# Neon Asteroids: Duel

A neon, vector-style Asteroids duel for phones (portrait). One thumb steers, the other fires.
Best of 3 rounds, 30 seconds each; 3 hits and your ship is scrap. Round 3 brings UFOs.

**Play:** open the GitHub Pages URL for this repo on your phone.

## Modes
- **VS BOT**: a computer rival.
- **ONLINE**: tap *Share invite link* and send it. Your friend's game opens straight into your room.
  Phones connect directly (WebRTC via [PeerJS](https://peerjs.com)); the free PeerJS cloud server only introduces them.
- **PRACTICE**: three rounds solo for a high score.

## Notes
- Everything is in `index.html` (vanilla JS + Canvas, no build step).
- Rooms are 1v1. Room codes map to PeerJS ids `neon-asteroids-duel-v1-<code>`.
- If a network blocks direct connections (some strict mobile or office networks), add a TURN server to `peerOptions()`.
- To use your own PeerJS server, add `?peerhost=your.host:443` to the URL.
