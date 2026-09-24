# rextlfung.github.io

Personal academic website of Rex Fung, served at <https://rextlfung.github.io>.

Built with Jekyll on GitHub Pages, based on the [academicpages](https://github.com/academicpages/academicpages.github.io) template (itself a fork of [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/), MIT License — see `LICENSE`).

## Layout

- `_config.yml` — site settings and author sidebar
- `_data/navigation.yml` — top menu
- `_pages/` — Home (`about.md`), Resume, Publications, Teaching, Personal Projects
- `resume/` — LaTeX source for the resume; only `resume/build/resume.pdf` is committed
- `posters/`, `videos/`, `images/` — static assets

The Talks, Portfolio and Blog features from the template are kept but currently empty
(`_talks/`, `_portfolio/`, `_posts/`); add files there and re-enable the menu entries in
`_data/navigation.yml` to use them.

## Running locally

```sh
bundle install
bundle exec jekyll serve --config _config.yml,_config.dev.yml
```

Then open <http://localhost:4000>.
