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

## CI

One required check runs on every PR:

| Check       | Command                                  | Fails on                     |
| ----------- | ---------------------------------------- | ---------------------------- |
| Schema lint | `linkml lint --ignore-warnings schemas/` | Schema errors (not warnings) |
