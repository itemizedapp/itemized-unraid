# Itemized — Unraid Community Applications Template

Unraid Community Applications template repository for [Itemized](https://github.com/itemizedapp/itemized) — self-hosted household inventory management, expiration tracking, barcode scanning, and direct Zebra ZPL label printing.

## Repository Structure

- `ca_profile.xml`: Maintainer profile metadata for Unraid Community Applications.
- `templates/itemized.xml`: Unraid Docker container template (`ghcr.io/itemizedapp/itemized:latest`).

## Notes for Unraid Users

- **Permissions**: The template defaults to `PUID=99` (`nobody`) and `PGID=100` (`users`). The container entrypoint automatically updates ownership of `/data` before dropping privileges.
- **Networking & Printing**: Bridge networking works out of the box for outbound LAN connections to Zebra ZSB (IPP, port `631`) and Raw TCP ZPL (port `9100`) printers.
- **Mobile Barcode Scanning**: Mobile browsers require HTTPS to access the camera API (`navigator.mediaDevices`). Place Itemized behind a reverse proxy (e.g., Nginx Proxy Manager, Caddy, Traefik, SWAG, or Tailscale Serve) and set `TRUST_PROXY=true` and `BASE_URL=https://itemized.your-domain.com`.
