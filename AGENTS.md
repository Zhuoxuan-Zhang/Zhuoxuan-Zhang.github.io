# Repository Guidelines

## Project Structure & Module Organization

This repository is a Jekyll-based academic homepage. Site-wide settings and author metadata live in `_config.yml`; the homepage content is maintained in `_pages/about.md`. Reusable page fragments are under `_includes/`, layouts under `_layouts/`, and navigation data under `_data/`. SCSS partials belong in `_sass/` and are assembled through `assets/css/main.scss`. JavaScript and fonts live under `assets/`, while publication images and favicons live in `images/`. The optional citation updater is isolated in `google_scholar_crawler/`, and its scheduled workflow is in `.github/workflows/`.

## Build, Test, and Development Commands

- `bundle install` installs the Ruby dependencies pinned by `Gemfile.lock`.
- `bash run_server.sh` starts the Jekyll live-reload server; preview at `http://127.0.0.1:4000`.
- `bundle exec jekyll build` performs a production-style build and writes generated output to `_site/`.
- `cd google_scholar_crawler && pip install -r requirements.txt` installs crawler dependencies. Run `python3 main.py` only with `GOOGLE_SCHOLAR_ID` set; it makes external Scholar requests and writes `results/` data.

## Coding Style & Naming Conventions

Preserve the existing conventions in each file type: two-space indentation for YAML, four spaces for Python and SCSS blocks, and lowercase kebab-case for new asset filenames. Name Jekyll partials descriptively, for example `_includes/author-profile.html`. Keep content changes in `_pages/about.md` and reusable presentation rules in `_sass/` rather than adding inline styles. Retain YAML front matter at the top of rendered Markdown and SCSS entry files. No repository-wide formatter or linter is configured, so keep diffs focused and follow nearby style.

## Testing Guidelines

There is no automated test suite or coverage requirement. Before submitting changes, run `bundle exec jekyll build` and treat warnings or Liquid errors as failures. Preview locally and check navigation, external links, publication cards, images, and responsive behavior at desktop and mobile widths. For crawler changes, use a valid Scholar ID and inspect both generated JSON files without committing secrets.

## Commit & Pull Request Guidelines

Recent history uses short, lowercase summaries such as `update` and `fix pub error`. Follow that concise style, but make the scope explicit, for example `update EMNLP publication` or `fix mobile paper layout`. Keep commits narrowly focused. Pull requests should explain the visible or configuration change, list local validation performed, link relevant issues, and include before/after screenshots for layout or styling work. Never commit API tokens, Scholar credentials, `_site/`, or local dependency caches.
