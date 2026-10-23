# Architecture

## End-to-end path

```text
External event
→ MCP bridge
→ persistent message state
→ wake listener
→ MCP tool surface
→ live ChatGPT conversation
→ assistant response
```

## Local test environment

The validated prototype used:

- iPhone 12 as the mobile ChatGPT client
- Mac as the local development machine
- two local terminal processes
- Streamable HTTP transport
- ChatGPT Developer Mode

## Component boundaries

### MCP bridge

Owns the integration boundary exposed to the connected AI client.

### Persistence

Keeps incoming messages durable enough for the listener to observe them independently of a transient UI action.

### Listener

Detects new persisted events and triggers the wake path.

### ChatGPT / MCP connection

Discovers the tool through Developer Mode and the configured transport.

### Conversation surface

Receives the event in the live interaction context.

## Why persistence matters

Without persistence, an event can disappear if a consumer is not ready at the exact moment of delivery.

The prototype therefore treats the event as state first and a wake signal second.
