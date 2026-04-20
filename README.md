# mkdocs-catalog-test-fixture

Test fixture repository for [mkdocs-product-catalog](https://github.com/tomasz-krakowski-asml/mkdocs-product-catalog) multirepo integration tests.

## Contents

- `docs/catalog.md` — A page with a `<!-- product-catalog: ./services -->` tag
- `docs/services/` — Three sample service YAML files (Alpha API, Alpha Worker, Alpha Cache)
- `mkdocs.yml` — Minimal MkDocs config

## Usage in multirepo tests

```yaml
# In root mkdocs.yml:
plugins:
  - product-catalog
  - multirepo:
      cleanup: true
nav:
  - Home: index.md
  - Team Alpha: '!import https://github.com/tomasz-krakowski-asml/mkdocs-catalog-test-fixture'
```

The `!import` statement uses `mkdocs-multirepo-plugin` syntax.
The catalog tag uses a **relative path** (`./services`) so it resolves correctly inside the imported repo's temp clone directory.
