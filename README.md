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

## Notice and Disclaimer

NOTICE AND DISCLAIMER: This software automatically retrieves, accesses or interacts with external materials. Those retrieved materials are not distributed with this software and are governed solely by separate terms, conditions and licenses. You are solely responsible for finding, reviewing and complying with all applicable terms, conditions, and licenses, and for verifying the security, integrity and suitability of any retrieved materials for your specific use case. This software is provided "AS IS", without warranty of any kind. The author makes no representations or warranties regarding any retrieved materials, and assumes no liability for any losses, damages, liabilities or legal consequences from your use or inability to use this software or any retrieved materials. Use this software and the retrieved materials at your own risk.

External materials module-ws-dns interacts with at run time:

- The services that register with it or that you configure, under your agreements for those systems.
