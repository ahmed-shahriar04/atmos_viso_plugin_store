# Atmos Viso - Official Plugin Store CDN

This repository is the remote package registry and CDN for Atmos Viso desktop
widgets.

### Structure

- [`repository.json`](../repository.json): Master registry consumed by the
  desktop application.
- `avplugins/`: Published `.atmvis` package archives. Packages must be placed
  directly in this folder.

Every archive listed in `repository.json` must remain under `avplugins/`, and
its `download_url` must point to the corresponding raw GitHub URL.

### Building and publishing the catalog

From the repository root, run:

```sh
python build_catalog.py
```

The script reads each `avplugins/*.atmvis` archive, extracts
`widget.manifest.json`, calculates the archive size, validates the generated
JSON, and writes `repository.json`. To stage, commit, and push the catalog to
the `main` branch in one step, run:

```sh
python build_catalog.py --sync
```
