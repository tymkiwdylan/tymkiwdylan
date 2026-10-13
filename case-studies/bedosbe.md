# Bedosbe: B2B search and real-time messaging

[Product](https://bedosbe.com.ar) · [Back to profile](../README.md)

Bedosbe supports business discovery and communication between providers and buyers. My contributions span its search API, backend messaging, and related product interfaces.

## Contributions

- Updated search API documentation to describe implemented behavior, and revised tests around filters, saved searches, suggestions, pagination, and errors.
- Implemented internal messaging events for conversations, new messages, and read receipts over WebSockets.
- Added Redis message-queue integration for broadcasting events across application instances, while retaining local development without Redis.
- Worked on search filters, lead notifications, and billing-related access behavior.

## Architecture and evolution

The current monorepo combines a FastAPI / ASGI backend and a Next.js frontend. It includes Socket.IO messaging and shared data-model code. Earlier messaging work used Flask-SocketIO; the implementation has evolved with the product.

Search and messaging require different forms of feedback. Search needs understandable filters, bounded results, and predictable error responses. Messaging needs authenticated room membership and events that reach the correct conversation. Documentation and tests help frontend and backend changes agree on those contracts.

The implementation is private. This summary does not publish provider data, messages, or production configuration.
