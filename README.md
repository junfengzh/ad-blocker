# ad-blocker

Tiny Chrome extension (no JavaScript) for sites whose ads spawn dozens of
iframes/processes and bog the machine down.

- `rules.json`
  - rule 1: on the listed sites (`initiatorDomains`), block every third-party
    script, iframe, XHR, beacon and websocket.
  - rule 2: on the listed sites, also block known ad/tracking domains
    (`requestDomains`), including the site's own ad subdomains and images.
  - rule 3: still allow YouTube embeds on the listed sites.
  - Images are never blocked.
- `css/<site>.css` — hides the empty ad boxes on that site.

Only permission: `declarativeNetRequest` (Chrome applies the rules itself; the
extension cannot read your browsing).

## Install
chrome://extensions → Developer mode → Load unpacked → this folder.
After editing any file, click the reload icon on the extension card.

## Adding a site
1. Add its domain (e.g. `"example.com"`) to `initiatorDomains` in rules 1, 2 and 3.
2. Optional: create `css/example.css` with selectors for its ad boxes and add a
   `content_scripts` entry for it in `manifest.json`.
3. Optional: add that site's own ad subdomains to rule 2.
4. If something breaks (login, comments, video), find the blocked domain in
   DevTools → Network and add an allow rule like rule 3.

## Sites
- wenxuecity.com
