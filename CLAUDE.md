# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a static site hosted via GitHub Pages (custom domain configured in `CNAME`). There is no build system, package manager, bundler, or test suite — it's plain HTML/CSS/JS served as-is. Changes are made directly to the HTML/CSS/JS files and take effect on push (no compilation step).

The site is based on the "Hidayah" Bootstrap template (BootstrapMade.com, v2.2.0) and has been customized for the "PGSA" corporate/professional-services site (content is in Portuguese).

## Development

There are no build, lint, or test commands — open the HTML files directly in a browser, or serve the directory with any static file server (e.g. `python3 -m http.server`) to preview changes.

## Structure

- `index.html` — the live homepage. `index0.html` and `index1.html` are older/alternate full-page snapshots kept around, not linked from the live site's nav — check before editing them, they may be stale copies rather than active pages.
- `inner-page.html`, `portfolio-details.html` — secondary template pages from the original Hidayah template.
- `assets/` — active site assets: `css/style.css` and `js/main.js` are the customized template files; `vendor/` holds third-party libraries (Bootstrap, icon sets, owl.carousel, venobox, etc.) — these are vendored, not installed via a package manager, so update by replacing files in place.
- `static/` — a parallel copy of `css`/`js`/`assets`/`img` under a `landpage` variant; be aware there are effectively two asset trees (`assets/` and `static/`) and confirm which one a given page actually references before editing styles/scripts.
- `forms/contact.php` — server-side contact form handler using the "PHP Email Form" library (the library itself is only included in the paid template tier and is not vendored here — `forms/contact.php` will fail with "Unable to load..." unless `assets/vendor/php-email-form/php-email-form.php` is added). Update `$receiving_email_address` when wiring up the contact form for real.
- `design/` — source design assets (fonts, logos, a Mosk design file) not served by the site.

## Notes

- Since pages share duplicated markup (header/nav/footer) rather than templating/includes, a navigation or branding change typically needs to be repeated across `index.html`, `inner-page.html`, and `portfolio-details.html` individually.
- `changelog.txt` documents the original Hidayah template's version history, not this repo's own changes.
