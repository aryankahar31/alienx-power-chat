# AlienX Power Chat - Agent Memory

## Project
- **Repo**: https://github.com/aryankahar31/alienx-power-chat.git
- **Live**: https://alienx-chat.vercel.app
- **Type**: Single-file P2P chat app (HTML/CSS/JS)
- **Deployed via**: Vercel CLI (authenticated as `aryankahar31`)

## Tech Stack
- Vanilla HTML + inline JS (no build step, no framework)
- PeerJS 1.5.2 (WebRTC signaling via `0.peerjs.com:443`)
- Tailwind CSS via CDN
- Google STUN servers for NAT traversal

## Architecture
- Single `index.html` file (~350 lines)
- PeerJS public cloud for signaling only, all data is P2P
- Peer IDs prefixed with `ax-` (e.g. `ax-a1b2c3d4`)
- Connection flow: User A copies ID → sends to User B → B pastes in input → clicks Connect

## Key Files
- `index.html` — the entire app
- `README.md` — project description
- `AGENTS.md` — this file

## Deployed Version (Working)
- Connection logic: **exact same as original** (random ID, manual paste to connect)
- Name modal instead of `prompt()`
- XSS fixes: `escapeHtml()` on all dynamic content, `sanitizeFile()` on filenames
- 25MB file size limit
- Image preview in chat
- Toast notifications
- Click-to-copy peer ID
- Self-destruct messages (visual only, 10s)

## What Was Done
1. Full review of original code — found XSS vulns, hardcoded TURN creds, no auth, no file limits
2. First rewrite: overengineered with room code hashing → broke connection (PeerJS ID collisions)
3. Second rewrite: room-based auto-connect → still broken (hash collision on guest IDs)
4. Final rewrite: **reverted to original connection logic** with security/UI improvements on top

## Known Issues
- PeerJS public server (`0.peerjs.com`) can be unreliable/slow
- No TURN server (removed hardcoded public TURN; STUN-only works for most NATs)
- Self-destruct is visual only (receiving peer has full data access)
- No E2E application-layer encryption (only WebRTC transport encryption)
- No tests, no linting, no CI/CD

## User Context
- User is `aryankahar31` on Vercel and GitHub
- Prefers simple, working code over complex features
- Said "my old html work well" — the original connection flow must be preserved
- Deployment target: free, zero-cost hosting
