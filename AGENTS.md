# Repository Guidelines

## Project Structure & Module Organization

This repository contains the MkDocs Material documentation site for AXBot. Source pages live in `docs/`, with top-level pages such as `docs/index.md`, `docs/sponsor.md`, `docs/report.md`, and `docs/roadmap.md`. Topic sections are grouped under `docs/user-guide/`, `docs/command-list/`, and `docs/data-intro/`. Images and static assets live in `docs/images/`, `docs/assets/`, and section-specific `images/` folders. Theme overrides are in `overrides/`, and site navigation, theme settings, and Markdown extensions are configured in `mkdocs.yml`.

## Build, Test, and Development Commands

- `uv sync`: install the Python dependencies from `pyproject.toml` and `uv.lock`.
- `make dev`: run `mkdocs serve --livereload` for local preview.
- `make build`: run `mkdocs build`; use this as the primary validation before submitting changes.
- `make build-image`: build the Docker image tagged `axbot-qq-docs:latest`.

CI deploys the site with MkDocs and then builds/pushes a Docker image, so local `make build` should pass cleanly.

## Writing Style & Naming Conventions

Write concise Markdown with clear headings, short paragraphs, and examples where helpful. Keep existing Chinese-language content and terminology consistent with nearby pages. Use relative links within `docs/` and place new images near the page that uses them unless they are shared assets. Name Markdown files in lowercase kebab-case, such as `new-feature-guide.md`, and add new pages to `mkdocs.yml` navigation when they should appear in the site menu.

## Testing Guidelines

There is no separate unit test suite for this docs repo. Treat `make build` as the required test because it catches broken MkDocs configuration, invalid navigation entries, and Markdown extension issues. For visual or navigation changes, also run `make dev` and inspect the affected pages in a browser.

## Commit & Pull Request Guidelines

Recent history uses short messages such as `docs: update sponsor and group privilege details`, `update docs`, and dependency bump messages. Write new commit messages in Chinese, preferably with a concise conventional prefix, such as `docs: 更新赞助说明`. Pull requests should describe the changed pages, link related issues when available, and include screenshots for layout, image, or theme changes. Confirm `make build` results in the PR description.

## Security & Configuration Tips

Do not commit credentials, deployment keys, or local environment files. GitHub Actions uses repository secrets for Docker registry login and self-hosted deployment. Keep generated outputs such as `site/` and local diagnostic logs out of commits unless explicitly requested.
