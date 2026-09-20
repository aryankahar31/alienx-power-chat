# AlienX Power Chat V4.0

P2P encrypted chat app using WebRTC + PeerJS.
No server, no database, pure frontend.

## Features

- Direct peer-to-peer chat (WebRTC)
- File sharing with image preview (max 25MB)
- Voice messages (hold-to-record)
- Self-destruct messages (10s, visual only)
- Anonymous mode
- Typing indicators
- One-click ID copy
- Connection status indicator
- Toast notifications

## Security

- All inputs sanitized (XSS protection)
- File size limits
- Filename sanitization
- WebRTC encrypted transport
- No data stored on any server

## Usage

1. Open `index.html` in a browser
2. Enter your name
3. Copy your ID (click on it)
4. Share ID with a peer
5. Peer pastes ID and clicks Connect
6. Start chatting

## Tech Stack

- Vanilla HTML/CSS/JS (single file)
- PeerJS 1.5.2 (WebRTC)
- Tailwind CSS

## Self-Destruct Disclaimer

Self-destruct is visual only. The message is removed from the DOM after 10 seconds, but the receiving peer has full access to the data.
