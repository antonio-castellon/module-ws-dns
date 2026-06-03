# @acastellon/ws-dns

WS DNS system ( Ad-hoc Discovery WS system) - server side for service registration/discovery.

This module was incomplete/minimal in the original repo. It is the server counterpart to the `@acastellon/dns-client` module.

## Intended API / Endpoints (implement these)

Typical REST/WS endpoints a full implementation should expose (versioned):

- `GET /:version/ping` → 200/201 if healthy
- `GET /:version/get/:service_id` → returns { service: { PROTOCOL, IP_OR_CNAME, PORT, METHOD } } or error
- `POST /:version/set/:service_id` with body { PROTOCOL, PORT, METHOD } → registers the service address

**Example server skeleton (what you would implement):**

```js
const express = require('express');
const app = express();

app.use(express.json());

const services = {}; // or use a real store

app.get('/:version/ping', (req, res) => res.sendStatus(200));

app.get('/:version/get/:service_id', (req, res) => {
  const svc = services[req.params.service_id];
  if (svc) res.json({ service: svc });
  else res.status(404).json({ error: 'not found' });
});

app.post('/:version/set/:service_id', (req, res) => {
  services[req.params.service_id] = req.body;
  res.sendStatus(201);
});

app.listen(7777, () => console.log('WS DNS server stub running'));
```

## Install

```bash
npm install @acastellon/ws-dns
```

## Current stub

The index.js exports a factory that returns a minimal object with `start`, `register`, `get`. Replace with real Express + storage.

## License

MIT
