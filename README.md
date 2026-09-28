# Neon Asteroids: Duel

A neon, vector-style Asteroids duel for phones (portrait). One thumb steers, the other fires.
Best of 3 rounds, 1 minute each; 3 hits and your ship is scrap. Round 3 brings UFOs.

**Play:** open the GitHub Pages URL for this repo on your phone.

## Modes
- **QUICK PLAY** (main menu): one tap into an online match with the next pilot searching.
- **PRACTICE → WITH BOT**: a computer rival.
- **ONLINE → HOST**: you get a 4-letter room code. Tap *Share invite link* (on the menu or the waiting screen) and send it.
- **ONLINE → JOIN**: type your friend's code, or just open their invite link.
- **ONLINE → RANDOM**: Quick Match. Join a pool of searching pilots; the next two are paired automatically
  (one hosts, one joins) and dropped into a fresh room.
  Phones connect directly over WebRTC. [Trystero](https://github.com/dmotz/trystero) introduces them through
  several public Nostr relays at once, so one busy relay doesn't block a match. [PeerJS](https://peerjs.com)
  is the fallback if Trystero can't load (force it with `?net=peerjs`).
- **PRACTICE → SOLO**: three rounds on your own for a high score.

## Controls
Phones and tablets get touch controls; computers get keyboard + mouse automatically
(force either with `?controls=touch` or `?controls=desktop`).

**Keyboard:** W/↑ thrust · A D/← → turn · S/↓ brake · Space fire · Esc menu
**Mouse:** the ship faces the cursor · right-click (hold) thrust · left-click (hold) fire

**Touch:**
- **FLY** (left half, bottom of screen): drag to steer, push far to thrust.
- **FIRE** (right half): tap to shoot, hold for steady fire.
- The on-screen control guides fade once you've flown and fired a bit (remembered per device).
- **☰ MENU** (top): keep playing, surrender, or quit. Sound on/off lives here and on the main menu.

## Notes
- Everything is in `index.html` (vanilla JS + Canvas, no build step).
- Rooms are 1v1. Room codes map to Trystero room `room-<code>` (app id `neon-asteroids-duel-v1`),
  or PeerJS id `neon-asteroids-duel-v1-<code>` on the fallback.
- When a network blocks direct connections (common on mobile data), traffic goes through a TURN relay.
  The default is the Open Relay Project's public static-auth service. For a dedicated relay, sign up for a free
  Metered account and paste your credentials URL into `TURN_API_URL` in `index.html`.
- Connections reset themselves: a joiner that can't link in 25 s retries from scratch, an idle host reopens its
  room every minute, and when a rival leaves the host reopens a clean room while the joiner's next match starts fresh.
- To use your own PeerJS server, add `?peerhost=your.host:443` to the URL.
