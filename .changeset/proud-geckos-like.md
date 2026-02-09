---
"agents": patch
---

partykit releases

## partyserver

### `0.1.3` (Feb 8, 2026)

- [#319](https://github.com/cloudflare/partykit/pull/319) — Add `configurable: true` to the `state`, `setState`, `serializeAttachment`, and `deserializeAttachment` property descriptors on connection objects. This allows downstream consumers (like the Cloudflare Agents SDK) to redefine these properties with `Object.defineProperty` for namespacing or wrapping internal state storage. Default behavior is unchanged.

### `0.1.4` (Feb 9, 2026)

- [#320](https://github.com/cloudflare/partykit/pull/320) — **Add CORS support to `routePartykitRequest`**. Pass `cors: true` for permissive defaults or `cors: { ...headers }` for custom CORS headers. Preflight (OPTIONS) requests are handled automatically for matched routes, and CORS headers are appended to all non-WebSocket responses — including responses returned by `onBeforeRequest`.
- [#260](https://github.com/cloudflare/partykit/pull/260) — Remove redundant initialize code as `setName` takes care of it, along with the nested `blockConcurrencyWhile` call.

---

## partysocket

### `1.1.12` (Feb 8, 2026)

- [#317](https://github.com/cloudflare/partykit/pull/317) — Fix `PartySocket.reconnect()` crashing when using `basePath` without `room`. The reconnect guard now accepts either `room` or `basePath` as sufficient context to construct a connection URL.
- [#319](https://github.com/cloudflare/partykit/pull/319) — Throw a clear error when constructing a `PartySocket` without `room` or `basePath` (and without `startClosed: true`), instead of silently connecting to a malformed URL containing `"undefined"` as the room name.

### `1.1.13` (Feb 9, 2026)

- [#322](https://github.com/cloudflare/partykit/pull/322) — Fix `reconnect()` not working after `maxRetries` has been exhausted. The `_connectLock` was not released when the max retries early return was hit in `_connect()`, preventing any subsequent `reconnect()` call from initiating a new connection.
