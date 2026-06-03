# @acastellon/ws-dns

WS DNS system ( Ad-hoc Discovery WS system) - server side for service registration/discovery.

This module was incomplete/minimal in the original repo. It is the server counterpart to the `@acastellon/dns-client` module.

Typical endpoints (implement in Express or similar):
- GET /:version/ping
- GET /:version/get/:service_id
- POST /:version/set/:service_id  (with {PROTOCOL, IP_OR_CNAME, PORT, METHOD})

## Install

```bash
npm install @acastellon/ws-dns
```

## License

MIT
