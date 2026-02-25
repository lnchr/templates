# N8N (w/ Workers)

A powerful workflow automation tool that lets you connect anything to everything.

## What's Included

- **N8N** — Main application with web UI on port 5678
- **N8N Worker** — Background worker for queue-based execution
- **PostgreSQL** — Primary database for workflow data
- **Redis** — Message broker for job queue

## Architecture

This template runs N8N in **queue mode** with a dedicated worker process. This gives better performance and reliability for production workloads — the main process handles the UI and API while workers execute workflows in the background.

## Configuration

After deploying, you can access the N8N UI at your assigned domain. On first launch, you'll create an owner account.

### Environment Variables

| Variable | Description |
|----------|-------------|
| `EXECUTIONS_MODE` | Set to `queue` for worker-based execution |
| `N8N_ENCRYPTION_KEY` | Encryption key for credentials (auto-generated) |

## Links

- [N8N Documentation](https://docs.n8n.io)
- [N8N Community](https://community.n8n.io)
