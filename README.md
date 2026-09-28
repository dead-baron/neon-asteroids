# Neon Asteroids: Duel

A neon, vector-style Asteroids duel for phones (portrait). One thumb steers, the other fires.
Best of 3 rounds, 30 seconds each; 3 hits and your ship is scrap. Round 3 brings UFOs.

**Play:** open the GitHub Pages URL for this repo on your phone.

## Modes
- **VS BOT**: a computer rival.
- **ONLINE → HOST**: you get a 4-letter room code. Tap *Share invite link* (on the menu or the waiting screen) and send it.
- **ONLINE → JOIN**: type your friend's code, or just open their invite link.
  Phones connect directly (WebRTC via [PeerJS](https://peerjs.com)); the free PeerJS cloud server only introduces them.
- **PRACTICE**: three rounds solo for a high score.

## Controls
- **FLY** (left half, bottom of screen): drag to steer, push far to thrust.
- **FIRE** (right half): tap to shoot, hold for steady fire.
- The FLY/FIRE guides fade once you've flown and fired a bit (remembered on your device).
- **☰ MENU** (top): keep playing, surrender, or quit. Sound on/off lives here and on the main menu.

## Notes
- Everything is in `index.html` (vanilla JS + Canvas, no build step).
- Rooms are 1v1. Room codes map to PeerJS ids `neon-asteroids-duel-v1-<code>`.
- If a network blocks direct connections (some strict mobile or office networks), add a TURN server to `peerOptions()`.
- To use your own PeerJS server, add `?peerhost=your.host:443` to the URL.
