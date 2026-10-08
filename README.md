<p align="center">
  <img src="https://global.media.stux.cloud/logo.png" height="100" alt="Stux.Cloud Logo">
</p>

# Region Page

### *Powering everything, quietly & securely!*

A clean and simple region landing page template for Stux.Cloud regions.

## Overview

Each Stux.Cloud region (for example [uk.stux.cloud](https://uk.stux.cloud)) has its own website on the web server. That website serves a tiny wrapper page that frames this hosted template full-screen. The template works out which region is framing it, shows that region's servers with their live status, and links to every other region.

## Features

- 🌍 One page for every region: the region's name and flag, its servers, and a switcher linking to all regions
- 🟢 Live server status (Online / Degraded / Offline) from [status.stux.group](https://status.stux.group)
- 🗺️ A "Stux.Cloud regions" index when no region is known
- 🌗 Light and dark themes, responsive down to phone widths
- 🚀 Deployed at [regionpage.stux.cloud](https://regionpage.stux.cloud)

## Regions

<!-- regions:start -->
| Region | Code | Website | Servers |
|---|---|---|---|
| United Kingdom | `uk` | [https://uk.stux.cloud](https://uk.stux.cloud) | `robo1.servers.uk.stuxedo.net`<br>`tiny1.servers.uk.stuxedo.net`<br>`web1.servers.uk.stuxedo.net` (not monitored) |
| Europe | `eu` | [https://eu.stux.cloud](https://eu.stux.cloud) | None yet |
| Spain | `es` | [https://es.stux.cloud](https://es.stux.cloud) | `mixr1.servers.es.stuxedo.net` |
| United States | `us` | [https://us.stux.cloud](https://us.stux.cloud) | `down1.servers.us.stuxedo.net` |
| Canada | `ca` | [https://ca.stux.cloud](https://ca.stux.cloud) | `kitt1.servers.ca.stuxedo.net` |
| Australia | `au` | [https://au.stux.cloud](https://au.stux.cloud) | None yet |
| Japan | `jp` | [https://jp.stux.cloud](https://jp.stux.cloud) | None yet |
| Singapore | `sg` | [https://sg.stux.cloud](https://sg.stux.cloud) | None yet |
| India | `in` | [https://in.stux.cloud](https://in.stux.cloud) | None yet |
| Eco | `eco` | [https://eco.stux.cloud](https://eco.stux.cloud) | None yet |
<!-- regions:end -->

The regions and servers live in one file, [`assets/regions.js`](assets/regions.js). To add a region or a server, edit it there, then run `python scripts/build-readme.py` to refresh this table.

> **TODO:** confirm what the **Eco** region is and its proper name. For now it is described neutrally as "Stux.Cloud's Eco region", with a leaf icon in place of a flag.

Flags come from the [flag-icons](https://flagicons.lipis.dev) stylesheet on cdnjs (no emoji flags: they don't render on Windows).

## How a region is chosen

1. `?region=uk` in the address wins. Use it for previews and direct links, for example `https://regionpage.stux.cloud/?region=uk`.
2. Otherwise, when the page is framed, the first label of the framing site's host is used, read from `document.referrer`: `uk.stux.cloud` gives `uk`.
3. If neither names a known region, the page shows the Stux.Cloud regions index.

The page also mirrors its title to the framing page with a `page-title` `postMessage`, so the browser tab shows the region's name.

## The wrapper

[`wrapper/index.html`](wrapper/index.html) is the small page each region's website serves. It frames `https://regionpage.stux.cloud` full-screen and updates its own title from the framed page.

**The same file is uploaded, unchanged, to every region's website** (uk.stux.cloud, ca.stux.cloud and so on). The template does the rest, because it reads the region from the host of the site framing it. The wrapper is a deployment artefact: it is not part of the Pages site or the sitemap.

## Live status

Server badges are read from the Stux.Group status page's public `summary.json` (with a cache-busting query string). Servers with a `monitor` slug in `assets/regions.js` get an Online / Degraded / Offline badge; servers without one show "Not monitored". If the status can't be fetched, no badge is shown.

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/StuxCloud/regionpage.git
   ```

2. Run it locally:
   ```bash
   ./dev-server.sh        # or dev-server.bat on Windows
   ```
   Then open `http://127.0.0.1:8000/?region=uk` (or any region code, or no `?region` for the index).

## Customization

Edit `assets/regions.js` to change regions and servers, and `index.html` for the page itself.

## Deployment

This project uses GitHub Pages and can be automatically deployed to your desired domain.

The live version is deployed at [regionpage.stux.cloud](https://regionpage.stux.cloud).

## Previous designs

This repository always holds the current Stux.Cloud design (v3, single teal `#07878e`). Earlier designs are preserved as their own archived repositories:

- [regionpage-v2](https://github.com/StuxCloud/regionpage-v2): the two-tone green design, live at [regionpage-v2.stux.cloud](https://regionpage-v2.stux.cloud/)

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to get involved, and [CHANGELOG.md](CHANGELOG.md) for release history.

## License

Copyright (c) 2026 Stux.Group. This project is open source and available for use and modification.

---

*Built & Maintained by <img src="https://github.com/StuxCloud.png" height="14" alt="Stux.Cloud" valign="middle"> [Stux.Cloud](https://github.com/StuxCloud), Hosted by <img src="https://github.com/Stuxedo.png" height="14" alt="Stuxedo" valign="middle"> [Stuxedo](https://stuxedo.com).    
Stux.Cloud is a part of the <img src="https://global.media.stux.group/icon.png" height="14" alt="Stux.Group" valign="middle"> Stux.Group brand of businesses.*

## Local preview

Run `./dev-server.sh` (or `dev-server.bat`, add a port as the last argument) to serve the site at `http://127.0.0.1:8000` the way GitHub Pages does, with the dev-mode banner on. Add `--no-dev-mode` to see it exactly as production does, or `?banner=soon,maintenance,site` to preview the other banner types. It uses PHP 7.4's built-in server (set `PHP_BIN` to pick another PHP).
