# Design Decisions

## Streamable HTTP for the prototype

The integration used Streamable HTTP because it matched the MCP connection path being tested and allowed the local server to expose tools to the ChatGPT client.

## Persistence before notification behavior

The event should be stored before the system tries to surface it.

That makes the wake path less dependent on a single transient UI state.

## Listener and server are separate responsibilities

The bridge exposes capabilities and state.

The listener observes the event stream / persisted state and decides when a new event should be surfaced.

## Debug from the bottom up

When nothing happened, the system was checked layer by layer:

1. local process running
2. transport reachable
3. Developer Mode configured
4. tools visible
5. event persisted
6. listener observes it
7. mobile conversation reacts

## Device evidence stays precise

The validated device in this case study is **iPhone 12**.

No broader device compatibility claim is made from this test.

## Prototype is not production

The successful wake path does not by itself prove:

- always-on background reliability
- production authentication
- delivery guarantees
- scale
- multi-device parity

Those belong to a later hardening phase.
