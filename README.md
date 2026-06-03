# @acastellon/ws-dns

WS DNS system ( Ad-hoc Discovery WS system) - server side for service registration/discovery.

This module was incomplete/minimal in the original repo. It is the server counterpart to the `@acastellon/dns-client` module.

## Intended API / Endpoints (implement these)

Typical REST/WS endpoints a full implementation should expose (versioned):

- `GET /:version/ping` → 200/201 if healthy
- `GET /:version/get/:service_id` → returns { service: { PROTOCOL, IP_OR_CNAME, PORT, METHOD } } or error
- `POST /:version/set/:service_id` with body { PROTOCOL, PORT, METHOD } → registers the service address

## Install

```bash
npm install @acastellon/ws-dns
```

## Current stub

The index.js exports a factory that returns a minimal object with `start`, `register`, `get`. Replace with real Express + storage.

## License

MIT
