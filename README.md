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

- It stays short: under four phone screens, and less than a paragraph of words. The app's screens do the explaining.
- Every feature it shows is one the app has today.
- The screens in `img/` are drawn from the app's design. Swap in real iPhone screenshots when the App Store build is final.

## Licences

Geist, Geist Mono and Shippori Mincho are under the SIL Open Font License; see `fonts/`. The Cartwheel name, mark and screens are not licensed for reuse.
