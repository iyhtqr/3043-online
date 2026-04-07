# LIKELIKE Online

A lightweight multiplayer MMORPG / virtual art gallery built with Node.js, Express, Socket.io, and p5.js. Originally created by Molleindustria.

## Architecture

- **Single process**: The Node.js server (`server.js`) serves both the backend (Socket.io) and frontend (static files from `public/`).
- **No build step**: Frontend is plain JavaScript served as static files — no bundler needed.
- **Port**: Runs on port 5000 (set via `PORT` environment variable).

## Key Files

- `server.js` — Main server entry point (Express + Socket.io, game logic)
- `serverMod.js` — Server-side room-specific mod logic (chat filters, role-play, etc.)
- `data.js` — Room definitions, NPCs, assets, and configuration
- `public/` — All frontend static assets
  - `index.html` — Main entry page
  - `client.js` — Core frontend game engine (p5.js + Socket.io)
  - `clientMod.js` — Client-side mod logic
  - `p5.play.js` — Local copy of p5.play library
  - `assets/` — Images (PNG), sounds (MP3/OGG), fonts (TTF)

## Running

```bash
npm install
PORT=5000 node server.js
```

## Dependencies

- `express` — HTTP server and static file serving
- `socket.io` v2.3.0 — Real-time multiplayer communication
- `bad-words` — Chat profanity filtering
- `rita` — NLP for rhyming room mod
- `dotenv` — Environment variable loading

## Environment Variables

- `PORT` — Server port (default: 3000, set to 5000 for Replit)
- `ADMINS` — Admin credentials in format `username1|pass1,username2|pass2`

## Deployment

Uses VM deployment target (always-on) since it maintains WebSocket connections and in-memory game state.
