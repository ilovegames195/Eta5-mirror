# ETA5 public-site mirror for GitHub Pages

This repository includes an automated **best-effort website mirroring and deployment workflow** for the publicly accessible frontend at https://eta5.vercel.app/.

**Important:** This ZIP does **not** contain ETA5's original source, GTA V, GTA III, game assets, or anything private. It instructs GitHub Actions to attempt downloading publicly linked HTML/CSS/JS/images when you run the workflow. Dynamic server-side routes, scripts that load undocumented assets, authenticated resources, and game data may not work. Copy or republish a site only if you have the right to do so.

## Set up without installing software

1. Extract this ZIP on your computer.
2. Create a **public GitHub repository** (for example, `eta5-mirror`).
3. Upload the contents of the extracted folder **including the hidden `.github` directory** into the repository's `main` branch. (Do not upload the ZIP without extracting it.)
4. In your repository, open **Settings → Pages** and set **Build and deployment → Source: GitHub Actions**.
5. Open **Actions → Download public ETA5 pages and deploy → Run workflow**. (Pushing to `main` also triggers it.)
6. After the workflow succeeds, use the deployment URL shown on the Actions page. It is usually `https://USERNAME.github.io/REPOSITORY/`.

## If the website opens but games don't work

GitHub Pages serves static files only. It can't run a Vercel backend or recreate proprietary game engines/data by copying a launcher. Root-relative paths such as `/_next/...` can also break when deploying to a project URL (`/REPOSITORY/`). For the best root-path compatibility, use a repo named `USERNAME.github.io` or a GitHub Pages custom domain. That still doesn't restore any missing game runtime.

## Troubleshooting

- **No `index.html`:** The source blocked the downloader or was unavailable. Check the Actions logs.
- **Blank page:** Check the browser DevTools Console and Network tabs for missing scripts or paths; public mirror isn't guaranteed to work.
- **404 for images/scripts:** Some assets are loaded dynamically and weren't linked in the initial crawl.
- **Game says files are missing:** The launcher alone is not the game. You need appropriately licensed and compatible game assets and an actual browser-compatible runtime.

Re-running the workflow may refresh the public frontend. The workflow caps its download at 200 MB and doesn't cross to other domains.
