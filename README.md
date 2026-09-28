# Neon Asteroids: Duel

A neon, vector-style Asteroids duel for phones (portrait). One thumb steers, the other fires.
Best of 3 rounds, 1 minute each; 3 hits and your ship is scrap. Round 3 brings UFOs.

**Play:** open the GitHub Pages URL for this repo on your phone.

## Menu
- **LAUNCH**: one tap into an online Quick Play match with the next pilot searching.
- **ONLINE → HOST**: get a 4-letter room code; share the invite link (menu or waiting screen).
- **ONLINE → JOIN**: type your friend's code, or just open their invite link.
- **ONLINE → QUICK PLAY**: same as LAUNCH.
- **PRACTICE → WITH BOT**: best of 3 against a computer rival.
- **PRACTICE → SOLO**: three rounds on your own for a high score.

Phones connect directly over WebRTC. [Trystero](https://github.com/dmotz/trystero) introduces them through
several public Nostr relays at once; [PeerJS](https://peerjs.com) is the fallback (force it with `?net=peerjs`).

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
