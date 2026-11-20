# Contributing

## Prerequisites

- [uv](https://docs.astral.sh/uv/) for dependency management

Install dev dependencies:

```bash
uv sync --group dev
```

---

## Schema

The schema lives at `schemas/sact.yaml` as a LinkML YAML file.

### Linting the schema

```bash
uv run linkml lint --ignore-warnings schemas/
```

Warnings about empty `description` fields are expected — per-field documentation is added incrementally. CI uses `--ignore-warnings` so these do not block merges.

> **Note:** You may also see a warning that prefix `ICD` should be `ICF`. This is a false positive in the linter — ICD (International Classification of Diseases) and ICF (International Classification of Functioning) are different standards. Ignore it.

### Generating the data dictionary CSVs

```bash
uv run python scripts/gen_datadict.py
```

Writes `sact-datadict.csv` and `sact-metadataworks.csv` to `dist/` (gitignored).

### Previewing the docs

```bash
uv run gen-doc -d docs/schema schemas/sact.yaml
uv run mkdocs serve
```

---

## HDR UK Gateway metadata

`gateway/` holds what is published to the [HDR UK Health Data Research Gateway](https://healthdatagateway.org):

- `gateway/metadata.yaml`: the catalogue fields (title, abstract, coverage, access and so on), written by hand in the HDRUK 4.1.0 schema's shape. The tables and columns are generated from `schemas/sact.yaml`, so they aren't repeated there.
- `gateway/gateway.yaml`: the Gateway team, the status to publish with (`DRAFT` or `ACTIVE`), and the Gateway's dataset ID once the dataset has been created.

Everything in `gateway/metadata.yaml` is public once published, including as a draft.

---

## CI

One required check runs on every PR:

| Check       | Command                                  | Fails on                     |
| ----------- | ---------------------------------------- | ---------------------------- |
| Schema lint | `linkml lint --ignore-warnings schemas/` | Schema errors (not warnings) |
