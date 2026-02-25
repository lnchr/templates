# Redis

High-performance in-memory data store used for caching, message brokering, and real-time applications.

## What's Included

- **Redis** — Single Redis instance with default configuration

## Use Cases

- **Caching** — Store frequently accessed data for fast retrieval
- **Session storage** — Manage user sessions across app instances
- **Message queue** — Pub/sub messaging and job queues
- **Rate limiting** — Track API usage with atomic counters

## Connecting

Other workloads in the same control plane can connect using the injected environment variables (`HOST`, `PORT`). No authentication is required for internal access.

## Links

- [Redis Documentation](https://redis.io/docs)
- [Redis Commands](https://redis.io/commands)
