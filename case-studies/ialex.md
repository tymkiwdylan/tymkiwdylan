# iAlex: legal workflows, document processing, and product infrastructure

[Product](https://ialex.com.ar) · [Back to profile](../README.md)

iAlex brings case management, clients, legal research, documents, and collaborative writing into one workspace for Argentine legal practices. I work on the application and its supporting services through Norte Development.

## Contributions

- Implemented a subscription and billing flow with Stripe and Convex, including subscription-derived team access and plan changes.
- Implemented streaming document processing with checkpointed job state, progress reporting, and separate extraction, transcription, chunking, and embedding stages.
- Added pagination across case, client, document, event, team, and template screens, connecting frontend list behavior to backend queries.
- Work across legal research, document editing, and court integration flows, including recovery and error handling around external systems.

## Architecture

The product uses React, TypeScript, and Vite for the application, with Convex for backend functions and data. Document processing runs as a separate service, using Redis / BullMQ for queued work, cloud storage for files, and Qdrant for semantic search. Shared packages contain editor, diff, and domain utilities.

Keeping ingestion outside the interactive application gives long-running file work its own job lifecycle. Checkpoints and progress updates let the product communicate partial progress and support recovery. Billing also affects collaboration and access, so changes need to account for team behavior as well as checkout.

## Engineering practices

The current repository contains frontend and backend tests, document-processing tests, domain documentation, and verification tooling. The work involves permissions, list-query behavior, job retries, and integration failures alongside interface design.

The implementation is private. This overview describes engineering scope without publishing customer documents, credentials, or internal operational details.
