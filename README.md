# Ayush Thakur — Personal Website

Source for my personal website and blog, live at [ayusht.dev](https://ayusht.dev).

Built with [Quarto](https://quarto.org/) and published to GitHub Pages via the
workflow in `.github/workflows/publish.yml` on every push to `main`.

## Project structure

```
.
├── index.qmd            # Home page (intro, news, about)
├── blog/                # Writing (index + posts)
├── styles.css           # Site-wide theme
├── index.css            # Home page styles
├── _quarto.yml          # Quarto site config
├── scripts/             # Local scraping tooling (git-ignored)
└── data/scrape/         # Scraped CSV outputs (git-ignored)
```

`scripts/` and `data/scrape/` are local-only helpers used to gather the report,
notebook, and post links that populate `blog/index.qmd`. They are intentionally
git-ignored and not part of the published site.

## Local development

1. Install [Quarto](https://quarto.org/docs/get-started/).
2. Clone this repository.
3. Run `quarto preview` in the root directory and open the URL it prints.

## Refreshing the content lists (optional)

The links in `blog/index.qmd` are curated from scraped data. To regenerate the
underlying CSVs:

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r scripts/requirements.txt
playwright install chromium

python scripts/scrape_reports.py   # -> data/scrape/blogs.csv
python scripts/scrape_kaggle.py    # -> data/scrape/kaggle.csv
python scripts/scrape_medium.py    # -> data/scrape/medium.csv
```

## License

Website content is licensed under the
[Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/);
the source code that formats and displays it is licensed under the [MIT License](LICENSE).

## Contact

Questions or feedback? Reach out on [Twitter](https://x.com/ayushthakur0).
