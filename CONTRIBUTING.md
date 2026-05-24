# Contributing to TrashMD Assets

This repository is the library that TrashMD's
in-app Remote Asset Browser reads from, so additions go through pull requests against
the `main` branch.

## Submitting an asset

1. **Create a folder** under `assets/` named after your asset id, e.g.
   `assets/my_asset/`.
2. **Add the bundle** - export your asset from TrashMD as a `.tmdasset` file and
   place it in that folder.
3. **Add a preview** - include a `preview.png` thumbnail in the same folder.
   Square images (e.g. 128×128 or 256×256) look best in the browser.
4. **Register it** - add an entry to [`registry.json`](registry.json) in the
   `assets` array.
5. **Open a pull request** against `main`.

### Example registry entry

```json
{
  "id": "my_asset",
  "name": "My Asset",
  "author": "your-name",
  "version": "1.0",
  "description": "A short, one-line description.",
  "tags": ["tag1", "tag2"],
  "image": "assets/my_asset/preview.png",
  "download_path": "assets/my_asset/my_asset.tmdasset",
  "file_type": ".tmdasset",
  "file_size": "12.3 KB"
}
```

See the [Registry format](README.md#registry-format) section of the README for
the full field reference.

## Checklist

Before opening your PR, confirm:

- [ ] `id` is unique, lowercase, and matches the folder name under `assets/`.
- [ ] All files (`.tmdasset` + preview) live inside the asset's own folder.
- [ ] `image` and `download_path` point to the correct repo-relative paths
      (forward slashes).
- [ ] `file_type` and `file_size` are accurate.
- [ ] `registry.json` is still valid JSON.
- [ ] The asset is yours to share, or appropriately licensed for redistribution.

## Reporting a problem

If an asset fails to download, has a broken preview, or otherwise misbehaves in
the browser, open an issue using the **Asset issue** template.
