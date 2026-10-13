# INMOTO: connected inventory and sales workflows

[Back to profile](../README.md)

INMOTO is an internal operations application under active development. Its scope connects products, inventory, customers, suppliers, sales, orders, customer accounts, and electronic invoicing.

## Contributions

- Built and refined point-of-sale workflows, including customer selection, payment collection, and sale confirmation.
- Added indexed stock-state views for low-stock, out-of-stock, and negative-stock conditions, with permission checks and paginated queries.
- Implemented an idempotent backfill for existing stock-state records, with tests for repeat execution.
- Refined the invoicing flow so missing customer tax details can be completed within the task.
- Worked on user roles, audit interfaces, inventory movement forms, and consistent application UI primitives.

## Architecture and tradeoffs

The application has a React / TypeScript backoffice and a Convex backend. Inventory queries use explicit access permissions and indexes. Backend dependencies include tooling for electronic invoicing, spreadsheets, and PDF generation.

The central product challenge is keeping related business workflows coherent: a sale, a stock movement, a payment, and an invoice each have their own state and responsibilities. The interface must make the next action clear while backend rules preserve those distinctions.

Stock-state indexing is one concrete example. Maintaining an index during writes makes filtered inventory views possible without rebuilding the classification from every product at read time. A backfill supports older records, and idempotency makes reruns predictable.

## Verification

The repository includes backend and UI tests, typechecking, formatting and lint checks, and documented verification evidence. These notes describe implemented engineering work and the intended product; they do not claim a public launch or measured business outcomes.
