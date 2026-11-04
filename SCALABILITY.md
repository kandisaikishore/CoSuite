# Scalability and capacity plan

- Keep API instances stateless; move shared sessions and durable data out of process memory.
- Paginate high-volume member, space, booking, invoice, and activity endpoints where implemented.
- Enforce transactions and unique constraints for booking and billing invariants.
- Use idempotency keys for booking/payment mutations to prevent duplicate operations.
- Configure per-replica database pools within the database connection budget.
- Move exports, billing runs, and notifications to bounded background work.
- Add rate limits and bounded payload sizes to expensive endpoints.
- Track p95/p99 latency, booking conflicts, payment retry outcomes, DB pool wait, and job queue depth.

## Release gates
- [ ] Concurrent booking tests prove no double allocation.
- [ ] Billing operations are idempotent and auditable.
- [ ] Migrations and recovery procedures are rehearsed.
- [ ] Load tests support any increase in replicas.

This checklist does not claim those features are currently implemented.
