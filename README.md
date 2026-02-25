# Launcher Templates

Public infrastructure templates for [Launcher](https://lnchr.cloud). Browse the gallery at [templates.lnchr.cloud](https://templates.lnchr.cloud).

## Structure

```
registry.json           # Template index (auto-displayed on gallery)
<slug>/
  template.yaml         # Infrastructure definition
  metadata.json         # Author info
  README.md             # Template documentation
```

## Adding a Template

1. Create a folder with your template slug (lowercase, hyphens): `my-app/`
2. Add the required files (see below)
3. Add an entry to `registry.json`
4. Open a PR

### `template.yaml`

```yaml
version: "1.0"

metadata:
  name: my-app
  display_name: My App
  description: Short description of what this deploys.
  tags: [web, example]
  icon: search

variables:
  SECRET_KEY:
    type: secret
    generate: true
    length: 32
    description: App secret key

databases:
  my-db:
    type: postgres

applications:
  my-app:
    app_type: web
    source_type: docker_image
    image_url: myorg/myapp:latest
    exposed_ports: [8080]
    replicas: 1
    icon_url: https://cdn.jsdelivr.net/gh/selfhst/icons@main/png/my-app.png
    color: "#3b82f6"
    depends_on: [my-db]
    env:
      DATABASE_URL: postgres://${my-db.USER}:${my-db.PASSWORD}@${my-db.HOST}:${my-db.PORT}/${my-db.DATABASE}
      SECRET_KEY: ${SECRET_KEY}
```

**Key fields:**

| Field | Description |
|---|---|
| `app_type` | `web`, `worker`, or `api` |
| `source_type` | `docker_image` or `git` |
| `image_url` | Docker image (for `docker_image` source) |
| `exposed_ports` | Array of ports to expose |
| `icon_url` | Product icon URL (use [selfhst/icons](https://github.com/selfhst/icons) when available) |
| `color` | Hex color for the product brand |
| `depends_on` | Array of database/service names this app depends on |

**Database types:** `postgres`, `mysql`, `redis`, `mongodb`

**Variable references:** Use `${VAR_NAME}` for variables, `${db-name.HOST}`, `${db-name.PORT}`, `${db-name.USER}`, `${db-name.PASSWORD}`, `${db-name.DATABASE}` for database connection info.

### `metadata.json`

```json
{
  "author": "you@example.com",
  "author_name": "Your Name",
  "created_at": "2026-01-01"
}
```

### `README.md`

Short documentation for the template. Include what's deployed, default configuration, and links to official docs.

### `registry.json` entry

Add to the root `registry.json` array:

```json
{
  "slug": "my-app",
  "display_name": "My App",
  "description": "Short description for the gallery card",
  "tags": ["web", "example"],
  "icon": "Box",
  "icon_url": "https://cdn.jsdelivr.net/gh/selfhst/icons@main/png/my-app.png",
  "color": "#3b82f6",
  "category": "Category Name"
}
```

`icon` is a [Lucide](https://lucide.dev/icons/) icon name used as fallback when `icon_url` fails to load.

## Guidelines

- Use official Docker images when possible
- Generate secrets with `generate: true` — never hardcode credentials
- Keep descriptions concise (one sentence for registry, a paragraph for YAML metadata)
- Test your template YAML imports correctly before submitting
