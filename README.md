# FullStaQD Reference Architecture
*⚠️ Warning: The architecture and its documentation are still an early draft.*

This repository contains the [arc42](https://arc42.org)-based documentation for
the FullStaQD reference architecture.
We use [Material for MKDocs](https://squidfunk.github.io/mkdocs-material/) to
host our markdown-based documentation as a website.
We would love your input on the architecture, please reach out via the
[Issue Tracker](https://github.com/FullStaQD/architecture/issues)!

## Local Development
```sh
source ./.venv/bin/activate
mkdocs serve --livereload
```

## Deployment
The deployment of this documentation site is automated with GitHub Actions.
You can find the deployment workflow in the
[`.github/workflows/deploy-pages.yml` file](./.github/workflows/deploy-pages.yml).
The documentation site can be build manually as follows to be deployed to any
web server capable of hosting HTML, CSS and JS files:

```sh
source ./.venv/bin/activate
mkdocs build
```
