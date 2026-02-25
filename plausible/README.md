# Plausible Analytics

Lightweight, privacy-friendly web analytics — a simple alternative to Google Analytics.

## What's Included

- **Plausible** — Analytics application (port 8000)
- **PostgreSQL** — User accounts and site configuration
- **ClickHouse** — Time-series database for event data

## Getting Started

After deploying, visit your domain to create an account and add your first website. Then add the Plausible tracking script to your site:

```html
<script defer data-domain="yourdomain.com" src="https://your-plausible-url/js/script.js"></script>
```

### Why Plausible?

- No cookies — compliant with GDPR, CCPA, and PECR out of the box
- Lightweight script (~1KB) — won't slow down your site
- Simple dashboard — all the metrics you need, nothing you don't
- Open source — full transparency and control

## Links

- [Plausible Documentation](https://plausible.io/docs)
- [Self-Hosting Guide](https://plausible.io/docs/self-hosting)
