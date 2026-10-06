# lfs_setup

Storage for large zip archives. The archives are **not** in the git tree; each
batch is published as a [GitHub Release](https://github.com/DeepAiml/lfs_setup/releases)
and its zips are attached as release assets.

## Layout

- One release per batch, tagged with the batch folder name (e.g. `DDMMYYYY`).
- Locally, a batch lives in a folder of the same name. Archives are gitignored.
- Release assets can be up to 2 GB each. Larger files must be split first.

## Workflow

Publish a batch:

```sh
gh release create <batch> <batch>/*.zip --title <batch> --notes "..."
```

Add files to an existing batch:

```sh
gh release upload <batch> path/to/file.zip
```

Remove a batch once it is no longer needed (frees the storage):

```sh
gh release delete <batch> --cleanup-tag --yes
```

GitHub replaces spaces in asset file names with dots, so `My File.zip`
downloads as `My.File.zip`.
