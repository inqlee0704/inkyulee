# inqlee0704.github.io/inkyulee

Personal site for In Kyu Lee — one Markdown page rendered by GitHub Pages (Jekyll).
No theme, no framework, no web fonts.

## Layout of the repo

| Path | What it is |
| --- | --- |
| `index.md` | All page content. |
| `_layouts/default.html` | Page shell: `<head>`, analytics, footer. |
| `assets/css/main.css` | The only stylesheet. Light + dark via `prefers-color-scheme`. |
| `assets/` | CV, portrait, publication thumbnails. |

Push to `main` and GitHub Pages rebuilds.

## Local preview

The `github-pages` gem needs Ruby 3.x; macOS ships 2.6, so this repo uses
Homebrew's `ruby@3.3` (the version GitHub's Pages builder runs). It is keg-only,
so it has to be put on `PATH` first:

```sh
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"
bundle install          # once
bundle exec jekyll serve --livereload
```

Open <http://127.0.0.1:4000/>. Add that `export` line to `~/.zshrc` to skip it
next time.

Because the gem pins the same versions GitHub runs, a local build is the real
build — it catches `_config.yml` and Liquid errors that a browser preview cannot.
Edits to `index.md` and `assets/css/main.css` reload on save; `_config.yml`
changes need a restart.

Nothing is public until you `git push` to `main`.

## Editing conventions

**Dated entries** (experience, teaching, awards, talks, certifications) are plain
Markdown lists with a `{: .list}` attribute on the closing line. The year goes in a
leading `<span class="yr">`, which floats right on desktop and stacks on mobile.
A second, indented paragraph becomes the muted description line.

```markdown
- <span class="yr">2024 – Present</span>**Graduate Research Assistant** · UC San Diego

  One sentence about the work.
{: .list}
```

**Publications** are three-line blocks — title paragraph, then authors/venue:

```html
<div class="pub">
<div class="pub-thumb"><img src="assets/pub_x.png" alt="" width="" height="" loading="lazy" decoding="async"></div>
<div class="pub-body" markdown="1">
[Title](url)

**Lee IK,** Coauthor A — *Venue*, Year
</div>
</div>
```

Thumbnails are letterboxed with `object-fit: contain`, so any aspect ratio drops in
without being cropped. Keep the source images under ~1600 px wide.

## Colors

All colors are CSS custom properties at the top of `assets/css/main.css`, with a
dark-mode override block directly below. Change them in one place.
