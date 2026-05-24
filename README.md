<h1 align="center">TrashMD Assets</h1>
<p align="center"><strong>The community asset library for <a href="https://github.com/TrashBash/TrashMD">TrashMD</a>.</strong></p>
<p align="center">
  Ready-to-use <code>.tmdasset</code> bundles that show up in the in-app Remote Asset Browser.
</p>

<p align="center">
  <a href="#what-is-this">What is this?</a> -
  <a href="#how-trashmd-uses-this-repo">How TrashMD uses it</a> -
  <a href="#repository-layout">Layout</a> -
  <a href="#registry-format">Registry format</a> -
  <a href="#contributing">Contributing</a>
</p>

---

## What is this?

This repository is the remote asset library that TrashMD's **Remote Asset Browser**
reads from. Each entry is a self-contained `.tmdasset` bundle plus a preview image, indexed by a single [`registry.json`](registry.json)
at the repository root.

It currently contains a small set of primitive shapes (cube, sphere, plane,
cylinder) as working examples and starting points.

---

## How TrashMD uses this repo

TrashMD reads from this repository through the GitHub API at runtime:

- It fetches [`registry.json`](registry.json) from the **`main`** branch.
- For each asset, it loads the `image` for the browser thumbnail and downloads
  the `download_path` bundle when the user installs the asset.

Because the app reads the `main` branch, **only content merged into `main`
appears in the live Asset Browser.** Open changes as pull requests against
`main`.

---

## Repository layout

```
.
├── registry.json                 # Index of every published asset
└── assets/
    └── <asset_id>/
        ├── <asset>.tmdasset       # The downloadable asset bundle
        └── preview.png            # Thumbnail shown in the browser
```

One directory per asset, named after the asset `id`. Keep every file an asset
needs inside its own folder so entries stay self-contained.

---

## Registry format

`registry.json` is a single object with a `version` and an `assets` array.
Each asset entry looks like:

```json
{
  "id": "primitive_cube",
  "name": "Cube",
  "author": "TrashBash",
  "version": "1.0",
  "description": "Unit cube primitive with a default material.",
  "tags": ["primitive", "shape", "cube", "example"],
  "image": "assets/primitive_cube/preview.png",
  "download_path": "assets/primitive_cube/cube.tmdasset",
  "file_type": ".tmdasset",
  "file_size": "5.7 KB"
}
```

| Field | Required | Description |
|---|:---:|---|
| `id` | ✅ | Unique identifier. Also the folder name under `assets/`. |
| `name` | ✅ | Display name shown in the browser. |
| `author` | ✅ | Who made the asset. |
| `version` | ✅ | Asset version string. |
| `description` | ✅ | One-line summary shown in the browser. |
| `tags` |  | Search/filter keywords. |
| `image` |  | Repo-relative path to the preview image. |
| `download_path` | ✅ | Repo-relative path to the `.tmdasset` bundle. |
| `file_type` | ✅ | File extension of the bundle (`.tmdasset`). |
| `file_size` | ✅ | Human-readable size shown in the browser. |

---

## Contributing

Want to publish an asset? See [CONTRIBUTING.md](CONTRIBUTING.md) for the
submission checklist and a step-by-step walkthrough.

---

## License

Released under the [MIT License](LICENSE).
