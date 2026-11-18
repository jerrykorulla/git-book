# Git Book

A personal quick reference for everyday git commands, published with GitHub
Pages at <https://jerrykorulla.github.io/git-book/>.

## Local preview

Install [mdBook](https://rust-lang.github.io/mdBook/guide/installation.html)
(`cargo install mdbook`, or download a release binary), then:

```sh
mdbook serve --open
```

## Editing

- Chapters live in [`src/`](src/); the table of contents is
  [`src/SUMMARY.md`](src/SUMMARY.md).
- Add a page by creating a Markdown file in `src/` and linking it from
  `SUMMARY.md`.

## Publishing

[`.github/workflows/deploy.yml`](.github/workflows/deploy.yml) builds the book
and deploys it to GitHub Pages on every push to `main`.

One-time setup: in the GitHub repository, go to **Settings > Pages** and set
**Source** to **GitHub Actions**.
