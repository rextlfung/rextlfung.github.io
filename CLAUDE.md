# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Rex Fung's personal academic website, served by GitHub Pages at <https://rextlfung.github.io>. It is a Jekyll site based on the academicpages template (a fork of Minimal Mistakes). Pushing to `master` deploys; there is no CI, test suite or linter.

## Commands

Ruby 3.3.12 is pinned in `.ruby-version` and installed through rbenv, with the gems installed under it. A non-interactive shell picks up the macOS system Ruby (2.6) instead, where `jekyll` is not found, so run `eval "$(rbenv init - zsh)"` first.

```sh
bundle install
bundle exec jekyll serve --config _config.yml,_config.dev.yml   # http://localhost:4000
bundle exec jekyll build -d <some dir outside the repo>         # one-off build check
```

- `_config.yml` is not reloaded by `jekyll serve`; restart after editing it.
- `npm run build:js` regenerates `assets/js/main.min.js` from `assets/js/_main.js` and `assets/js/plugins/`. The site only loads `main.min.js`, so JavaScript edits have no effect until it is rebuilt and committed.
- The resume is built with latexmk/pdflatex from `resume/resume.tex` into `resume/build/` (the LaTeX Workshop extension in VS Code does this on save). Only `resume/build/resume.pdf` is committed; the other build files are gitignored.

## Structure

All visible content is hand-written Markdown in `_pages/`, each file with its own `permalink` and `layout: archive`. The template's collections (`_publications/`, `_talks/`, `_teaching/`, `_portfolio/`, `_posts/`) are empty and their menu entries are commented out, so the Publications and Teaching pages are plain lists in `_pages/publications.md` and `_pages/teaching.md`, not generated from collection items.

- **Top menu:** `_data/navigation.yml` drives `_includes/masthead.html`. An entry may have `children`, which render as a hover dropdown (styles in `_sass/_navigation.scss` under `.greedy-nav`). The greedy-navigation script moves top-level items into a hamburger menu on narrow screens, where children show as an indented list.
- **Personal projects:** each project is its own page in `_pages/projects/` with permalink `/projects/<name>/`. Adding one takes three edits: the new page, a summary entry in `_pages/projects.md` (the index), and a `children` entry under Personal Projects in `_data/navigation.yml`.
- **Resume:** `_pages/resume.md` embeds `resume/build/resume.pdf` in an iframe. The resume content in `resume/resume.tex` and the lists on the Publications page are kept in sync by hand, so a change to one usually needs the same change in the other.
- **Sidebar and site metadata:** the author profile shown on every page comes from the `author` block in `_config.yml`.
- **Static assets:** `images/`, `videos/` and `posters/` are served from the site root and referenced with absolute paths such as `/videos/volleybot_ball_tracking.mp4`.

`_sass/`, `_includes/` and `_layouts/` are mostly unmodified theme code; `_sass/vendor/` and `assets/js/vendor/` are third-party and should not be edited.
