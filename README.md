# RadioNet RP — Full Standalone Radio Communications Platform

RadioNet RP is a browser-based radio communications system for roleplay communities. RP/game integration is intentionally not included in this release.

## Included

- Account registration/login/logout with salted scrypt password hashing
- Owner/admin/dispatch/unit roles
- Persistent JSON data store
- Multi-channel radio frequencies
- Browser microphone PTT with WebRTC voice
- Radio audio processing (band-pass + compressor) and PTT tones
- Spacebar PTT and F9 panic
- Panic alerts and dispatch queue
- Unit statuses and live roster
- Dispatch console
- Activity/incident logging
- Channel administration
- User role/profile administration
- PWA manifest
- Responsive desktop/mobile UI
- WebSocket signalling server
- Health endpoint
- Zero third-party runtime dependencies

## Run

Node.js 20+ is required.

```bash
ADMIN_USERNAME=admin ADMIN_PASSWORD='change-this-password' node server.js
```

Open `http://localhost:3000`.

The first registration is also promoted to owner if no users exist. For a hosted installation, set `ADMIN_USERNAME` and `ADMIN_PASSWORD` before the first start.

## Production deployment

This application needs a long-running Node server and WebSocket support. Do not deploy the backend as a static-only site. A Docker-capable Node host is recommended.

The included Dockerfile starts the server directly. Set:

- `ADMIN_USERNAME`
- `ADMIN_PASSWORD`
- optional `DATA_DIR`
- hosting platform's `PORT` if it does not provide one automatically

For persistence, mount a volume at `/app/data` (or set `DATA_DIR` to a persistent directory).

## Voice notes

Voice uses browser WebRTC and a lightweight WebSocket signalling layer. It is intentionally mesh-based for this standalone release, so it is best suited to small/medium RP radio groups. For a very large public service, replace the mesh media layer with an SFU such as LiveKit/mediasoup later.

HTTPS is required by browsers for microphone access when hosted remotely. The same host must support secure WebSockets (`wss`).

## RP integration

No FiveM/GTA/Garry's Mod/Minecraft or other game integration is included. The platform is intentionally standalone in this release.
