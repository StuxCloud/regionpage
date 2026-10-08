# Changelog

All notable changes to regionpage are documented here.

## v3.4.0

### Changed

- EMEA, AMER and APAC each have their own globe in place of a flag (no flags exist for them), turned to face the area it covers: Europe and Africa, the Americas, and Asia with Australia. They replace the single generic globe, are drawn slightly larger in the flag box so the continents stay readable, and follow the brand colour in both themes (`globe-emea`, `globe-amer` and `globe-apac` in `assets/regions.js`)

## v3.3.0

### Added

- Regions are grouped into **EMEA**, **AMER** and **APAC**: Europe sits inside EMEA, with the United Kingdom and Spain inside Europe; the United States and Canada are in AMER; Australia, Japan, Singapore and India are in APAC. Each region in `assets/regions.js` names the region it belongs to (`parent`), and EMEA, AMER and APAC have a globe icon and a full name (`longName`)
- The region list is a tree: each group spans the row with its regions indented beneath it, and every count adds up the servers of the regions inside it (EMEA and Europe show 4 servers, AMER 2)
- A group's page (EMEA, AMER, APAC, Europe) lists every server inside it, under a heading for each region, and says it covers e.g. "Europe, the Middle East and Africa"
- A region's page shows where it sits, with links: "· EMEA › Europe" above the United Kingdom
- The README's region table has a "Part of" column, and a group's row gives its server total

### Fixed

- Europe said "No servers yet" although the United Kingdom's and Spain's servers are European; it now counts and lists them

## v3.2.0

### Changed

- The overview's heading is "Server Regions" (it was the brand's name followed by "regions"); the brand name stays in the line above it, and the browser tab reads "Server Regions — " plus the brand

### Removed

- The Eco region, which isn't a region any more. The page now lists nine regions; an old `?region=eco` link shows the overview instead

## v3.1.0

### Added

- `brand.serverDomain` in `assets/regions.js`: the domain the servers' hostnames use, when it differs from the region domain. Stux.Cloud's servers now live under `stuxedo.net` (e.g. `robo1.servers.uk.stuxedo.net`), so the page and the README's region table show those hostnames, while the regions themselves stay at `https://<code>.stux.cloud/`

## v3.0.0

### Changed

- Rebranded from Stux.Cloud's two-tone green to the single teal `#07878e`, which reads at about 4.1:1 on both the dark and light themes. Every green accent, gradient stop, floating-particle shade and site-banner accent is now `#07878e`; the dark and light backgrounds and text shift from green-tinted to teal-tinted (`#031d1e`, `#e6feff`, `#eef2f2`); button hover is a slightly brighter `#0a9ea6`
- The logo, icon and favicon pick up the new teal Stux.Cloud assets automatically from `global.media.stux.cloud`
- README links the archived earlier designs: [regionpage-v2](https://github.com/StuxCloud/regionpage-v2) (the two-tone green design)

## v1.0.1

### Changed

- down1 (United States) shows its live status, now that it is monitored on status.stux.group

## v1.0.0

### Added

- The region page template: a Stux.Cloud region's name and flag, its servers with live Online / Degraded / Offline badges, and a switcher linking to every region (opening the region's own website, outside the frame)
- A "Stux.Cloud regions" index, shown when no region is known
- Region detection from `?region=` (which wins) or the first label of the framing site's host in `document.referrer`, plus a `page-title` `postMessage` mirroring the title to the wrapper
- `assets/regions.js`, the single list of regions and servers (10 regions; servers on uk, es, us and ca) shared by the page and the README's region table (`python scripts/build-readme.py`)
- `wrapper/index.html`, the small page each region's website serves to frame the template full-screen; the same file is uploaded unchanged to every region
- Live status from the Stux.Group status page's `summary.json`, with "Not monitored" for servers that have no monitor and no badge if the fetch fails
- Light and dark themes, flags from flag-icons, and a leaf icon for the Eco region
- The shared Stux page set: `changelog`, `404`, `legal` and its six sub-pages, `sitemap` and `sitemap.xml` (regenerated with `python scripts/build-sitemap.py`), the dev-mode banner, `dev-server.sh`/`.bat` (PHP 7.4, DEV_MODE on by default, `--no-dev-mode`), `commit.sh`/`.bat`, CI and the GitHub Pages workflow
