# CompassU

A single-page PWA that matches a Fall 2027 freshman housing + dining plan across the
University of Kansas, the University of Arkansas, and Oklahoma State University.

Ten guided questions (budget, roommates, bathroom, kitchen, walk time, hall size,
building age, dining appetite, tie-breaker priority) produce a ranked top pick per
school, priced with real 2026–27 room rates, meal-plan tiers, non-resident tuition,
and the merit award the student qualifies for.

## Contents

```
index.html              self-contained app (all markup, logic, fonts and images inlined)
manifest.webmanifest    PWA manifest — name, colors, icons, standalone display
sw.js                   service worker — cache-first app shell, offline capable
icon-*.png              192 / 512 / 1024 px icons, maskable variant, apple-touch, favicon
.nojekyll               tells GitHub Pages to serve files starting with _ verbatim
```

## Publish on GitHub Pages

1. Repository: **`CompassU`**.
2. Copy the **contents of this folder** into the repository root and push:
   ```bash
   git init
   git add .
   git commit -m "CompassU PWA"
   git branch -M main
   git remote add origin git@github.com:jasienswords/CompassU.git
   git push -u origin main
   ```
3. **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.
4. The app appears at `https://jasienswords.github.io/CompassU/` within a minute or two.

All paths in the manifest, service worker and HTML are relative (`./`), so the app
works from a project subpath — no configuration needed for the `/CompassU/`
prefix that GitHub Pages adds.

## Install on iPhone

Open the Pages URL in **Safari** (not Chrome — only Safari can install to the Home
Screen on iOS), tap **Share → Add to Home Screen**, then **Add**. It launches full
screen with no browser chrome, and works offline after the first load.

On Android/Chrome, use **⋮ → Install app**.

## Updating the app

`index.html` is a compiled bundle. After replacing it:

1. Bump `CACHE_VERSION` in `sw.js` (e.g. `compassu-v2`) — otherwise returning
   visitors keep the cached copy.
2. Commit and push. The new service worker activates on the next visit.

## Data

Rates, ratings, walk times and deadlines come from the Fall 2027 housing and dining
comparison matrix (official 2026–27 figures; student ratings via Roomsurf, which is
unaffiliated with any of the three universities). Merit awards are modeled on a
3.25 GPA / 1240 SAT. Female-only halls are excluded from recommendations.

University names, logos and mascots are trademarks of their respective institutions
and are used here for personal, non-commercial reference.
