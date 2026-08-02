# csg-site-assets

Shared front-end assets for citizen-starter-guide.com.

Kept out of the tool repos deliberately: these load on **every page of the
site**, so they must not depend on a repo that might be renamed, archived, made
private, or restructured. A tool repo going away should never take the site-wide
navigation with it.

## nav-i18n.js

Translates the site-wide header into German, French, Japanese and Simplified
Chinese, reading the language from `<html lang>` (set by Polylang). Does nothing
at all on English pages.

Loaded from WordPress with a single line at the end of the nav template:

```html
<script src="https://quattrobaje3na-png.github.io/csg-site-assets/nav-i18n.js" defer></script>
```

The nav HTML itself is never edited. Add a link or change a label and this keeps
working -- the new string simply renders in English until it is added to
`wp-translate/nav/nav_strings.json` and the file is regenerated.

Covers: nav links, CTA row, LIVE FEED bar and its status words, UPCOMING EVENTS,
the GameGlass promo including its countdown, the Invictus dropdown, and
SYSTEM_LINKS. It also rewrites the Blueprint Finder and Mining Material Finder
links to the current language.

Regenerate with `py -3 build_nav_i18n.py` in `wp-translate/nav/`, then copy
`nav-i18n.js` here and push. No build step runs in this repo.
