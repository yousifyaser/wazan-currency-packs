# Wazan currency packs

Banknote recognition models downloaded by the **Wazan** app (currency reader for blind and low-vision users). The app ships without currencies; users download the ones they need from here.

- `catalog.json` lists every published currency, its settings and its files (size and SHA-256).
- `catalog.json.sig` is an Ed25519 signature of `catalog.json`. The app only accepts a catalog signed with the publisher's private key, and only files whose SHA-256 matches the catalog.
- `packs/` holds the model files. Paths include the version, so a published file never changes.

Files are served to the app through [jsDelivr](https://www.jsdelivr.com/) (`cdn.jsdelivr.net/gh/yousifyaser/wazan-currency-packs@main/...`), with GitHub as a fallback.

## Publishing a currency or an update

1. Put the model files under `packs/<currency>/<version>/`.
2. Add or update its entry in `source_catalog.json` (in the app project).
3. Run `python3 build_catalog.py` to rebuild and sign `catalog.json`.
4. Upload the new files, `catalog.json` and `catalog.json.sig` here.

The app shows new currencies and updates the next time its download page is opened; no app update is needed.
