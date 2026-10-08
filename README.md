# vincentfung13.github.io

Source for [vincentfung13.github.io](https://vincentfung13.github.io), Zijian Feng's personal website. Built with
[Jekyll](https://jekyllrb.com/) and the [al-folio](https://github.com/alshedivat/al-folio) theme (v1.x), and deployed
to GitHub Pages by `.github/workflows/deploy.yml` on every push to `master`.

## Local preview

Requires Ruby 3.x (on macOS: `brew install ruby`) and Node.

```bash
export PATH=/opt/homebrew/opt/ruby/bin:$PATH
bundle install
npm ci
bundle exec jekyll serve --config _config.yml,_config.dev.yml --livereload
```

Then open http://localhost:4000. `_config.dev.yml` turns off ImageMagick and Jupyter locally; CI installs both. Add
`--drafts` to preview posts in `_drafts/`. Restart the server after editing `_config.yml`, and run
`bundle exec jekyll clean` if a change doesn't show up.

## Where things live

| Content                        | File                                                                                         |
| ------------------------------ | -------------------------------------------------------------------------------------------- |
| Homepage bio, featured project | `_pages/about.md`                                                                            |
| News                           | `_news/` (one file per item)                                                                 |
| Publications                   | `_bibliography/papers.bib` (`selected = {true}` puts a paper on the homepage)                |
| CV                             | `_data/cv.yml`, PDF in `assets/pdf/cv_zijian_feng.pdf`                                       |
| Blog posts                     | `_posts/YYYY-MM-DD-slug.md`; drafts in `_drafts/`; styling examples in `docs/post-examples/` |
| Projects (mew)                 | `_projects/mew.md`                                                                           |
| Photography                    | `_data/photos.yml`, images in `assets/img/photos/`                                           |
| Social links                   | `_data/socials.yml`                                                                          |
| Repositories page              | `_data/repositories.yml`                                                                     |
| Site settings                  | `_config.yml`                                                                                |

## Adding photos

```bash
bin/prepare-photos ~/path/to/exported-photos   # resizes to 2048px, strips GPS, writes to assets/img/photos/
```

Then add an entry per photo to `_data/photos.yml`. Requires `exiftool` (`brew install exiftool`).

## Site-specific tweaks

- `_layouts/cv-site.liquid`: the theme's CV layout plus fixes for location wrapping, location font size and stray
  list markers.
- `projects/mine/`, `projects/nemi/`: legacy hand-written project pages, served as-is.
- `assets/js/theme.js`: copy of `al_folio_core`'s theme script with the default changed from `system` to `light`
  (the only edit is in `determineThemeSetting`). Tracked in `.al-folio-overrides.yml`; after upgrading
  `al_folio_core`, run `bundle exec al-folio upgrade overrides audit` and re-apply the one-line change to the new
  upstream file if it changed.
