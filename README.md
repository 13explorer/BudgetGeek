# The Budget Geek Website

A static Astro marketing site for The Budget Geek, covering managed IT, networking, repairs, AI infrastructure, websites, and technology consulting. Production uses a multi-stage Docker build: Node builds the static files, then `nginx:alpine` serves only the generated output.

## Customize before publishing

Replace every obvious placeholder in `src/`:

- `[Service Area]`
- `[Business Hours]`
- `hello@example.com`

When the public domain is ready, set `SITE_URL` to its full HTTPS origin before building. This enables canonical and social-preview URLs.

## Deploy on the Ubuntu web server

Place or clone the repository at `~/docker/msp-site`, then run:

```bash
cd ~/docker/msp-site
docker compose up -d --build
```

Open the site at:

```text
http://<ubuntu-server-ip>:8082
```

Verify the page and health endpoint:

```bash
curl -I http://127.0.0.1:8082/
curl http://127.0.0.1:8082/healthz
docker compose ps
```

## Common commands

Build without starting:

```bash
docker compose build
```

Start:

```bash
docker compose up -d
```

Stop and remove the container:

```bash
docker compose down
```

Rebuild after site changes:

```bash
docker compose up -d --build
```

View logs:

```bash
docker compose logs -f website
```

Build with the future public URL:

```bash
SITE_URL=https://your-domain.example docker compose up -d --build
```

## Local Astro development

Node.js 22+ and pnpm are only needed for development outside Docker:

```bash
corepack enable
pnpm install
pnpm dev --host 0.0.0.0
```

Pangolin and public DNS are intentionally not configured in this project.
