# Base44 Dev Environment

## Project Overview
Static HTML/CSS/JS Minecraft server website template. No build step, no backend, no dependencies — just static files served by nginx.

## Directory Structure
The repo was imported with all files flat in the root, but the HTML references a nested directory structure (`css/`, `JS/`, `html/`, `assets/images/`, `assets/Vote-link-Imgs/`, `assets/Loading-screen-texture/`). Symlinks were created to bridge the flat files to the expected paths. **Do not delete these symlinked directories** or the site will break.

## Running the App
```bash
docker compose -f docker-compose.base44.yml up -d
```
Serves on port 3000 via nginx:alpine with a custom `nginx.conf` (runs worker as `root` because the sandbox root dir has 700 permissions).

## Configuration
All site content (server name, Discord link, staff data, rules, FAQ) is configured in `config.js` at the repo root. This is the only file users need to edit to customize the site.

## Verification
- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` should return 200
- Subpages at `/html/vote.html`, `/html/rules.html`, `/html/staff.html`, `/html/FAQ.html`
- CSS at `/css/*.css`, JS at `/JS/*.js`, images at `/assets/images/*`
