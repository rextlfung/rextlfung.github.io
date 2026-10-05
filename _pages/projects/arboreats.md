---
layout: archive
title: "ArborEats"
permalink: /projects/arboreats/
author_profile: true
---

[github.com/rextlfung/ArborEats](https://github.com/rextlfung/ArborEats)

An interactive map of food and drink deals in Ann Arbor, scraped from restaurants' own websites and refreshed automatically every day.

[Try the live map](https://rextlfung.github.io/ArborEats/){: .btn .btn--large}

- Lists food businesses inside the M-14 / US-23 / I-94 ring from OpenStreetMap, enriched with Overture Maps, and finds each one's website, social media, and the pages likely to carry deals
- Scrapes those pages with Playwright, reads text out of deal images using Tesseract OCR, and extracts deals with a rule-based parser that only publishes the ones it is confident about
- Runs entirely locally and for free, with no API keys or accounts; a scheduled GitHub Actions workflow reruns the pipeline nightly, commits the new data, and redeploys to GitHub Pages
