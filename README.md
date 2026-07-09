# html-share

free public hosting for quick HTML pages.

base URL:

```text
https://fletcherd3.github.io/html-share/
```

## add a page

from a file:

```sh
python3 scripts/share_html.py --title "my page" --file /tmp/page.html --deploy
```

from stdin:

```sh
printf '<h1>hello</h1>' | python3 scripts/share_html.py --title "hello" --deploy
```

replace a stable URL:

```sh
python3 scripts/share_html.py --title "status" --slug status --replace --file /tmp/status.html --deploy
```

without `--deploy`, the script only writes into `pages/` and prints the eventual URL.

## how it works

- pages live under `pages/<slug>/index.html`
- `pages/index.html` is regenerated as a simple listing
- pushes to `main` deploy through GitHub Pages using `.github/workflows/pages.yml`
- the GitHub Actions workflow uploads `pages/` as the Pages artifact and deploys it

## notes

- everything here is public
- do not put secrets, private data, tokens, or personal docs in generated pages
- GitHub Pages is static hosting only: HTML/CSS/JS/assets are fine; server-side code is not
