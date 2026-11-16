# cartwheel.fit

The landing page for [Cartwheel](https://cartwheel.fit): one static HTML page with its fonts and images. No build step and no dependencies.

## Preview

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Publish

Actions → **Publish** → Run workflow, on `main`. Pushing never publishes.

One-time setup: Settings → Pages → Source: **GitHub Actions**, then Custom domain `cartwheel.fit` with **Enforce HTTPS** on.

## The two links that change

Both live in the `window.CARTWHEEL` block at the top of `index.html`:

- `appOrigin`: where the web app lives (`https://app.cartwheel.fit`). Sign up, Sign in, Privacy and Support point at it. The page's own `href`s carry the same value so it works with scripts off, so update both.
- `appStoreUrl`: the App Store listing. Empty, the App Store links read "App Store, coming soon" and go nowhere; an `https://` URL turns them into links.

## Keeping it honest

- It stays short: seven sections, each a heading and a few lines. The app's screens do most of the explaining.
- It looks like the app: the same colour tokens in dark and light, the same type, radius and spacing (kata `src/app/globals.css`, `docs/design-system.md`). Dark is the default; a device set to light gets the app's light theme. The switch at the top right picks one theme for that browser and remembers it; without JavaScript it is hidden and the page follows the device.
- Prices match the app's (`src/lib/billing/prices.ts` in kata). Change both together.
- Every feature it shows is one the app has today.
- The cartwheel above the last call to sign up is the app's own (kata AND-1403: `ios/Kata/Domain/CartwheelTumble.swift` and `CartwheelTumbleView.swift`), ported to a canvas with the same keyframes and numbers. If the app's changes, port it again rather than tuning it here. It plays once when it scrolls into view; with reduced motion it shows the landed pose, and without JavaScript it is not shown.
- The screens in `img/` are real captures from the iOS app, signed in to a throwaway local test account, in both themes (`*-dark.webp`, `*-light.webp`, 720px wide). Retake them when the screens change.

## Licences

Geist, Geist Mono and Shippori Mincho are under the SIL Open Font License; see `fonts/`. The Cartwheel name, mark and screens are not licensed for reuse.
