# Richard Turpin — Hugo Profile demo

Naked [Hugo Profile](https://github.com/gurusabarish/hugo-profile) site for **Richard Turpin** (Dick Turpin), assembled as a Turpinverse persona demo for [Hugo Matters](https://github.com/markheydon/hugo-matters) CMS testing.

This is not a production personal site. It maps generic Turpinverse domain data into Hugo Profile `params` and content. No Frontmatter CMS, GitHub Actions, Dev Container, or Cursor scaffolding is included, so the CMS can be layered on a clean tree.

## Run locally

Theme is a **Hugo Module** (`module.imports` in `hugo.yml`, pin in `go.mod` / `go.sum`). Hugo fetches it at build time; there is no `themes/` folder or git submodule.

### Local Hugo

Install [Hugo Extended](https://gohugo.io/installation/) (0.87+ recommended; this pin matches markheydon.github.io tooling around 0.165), then:

```bash
hugo server
```

Open the URL Hugo prints (typically `http://localhost:1313`).

Production-style build:

```bash
hugo --minify
```

Output is `public/`.

### Docker / Podman (`invoke` script)

From the repo root (no local Hugo required):

```bash
./scripts/invoke-hugo-site.sh serve     # live reload at http://localhost:1313
./scripts/invoke-hugo-site.sh build     # minify build to public/
./scripts/invoke-hugo-site.sh preview   # build + nginx at http://localhost:8080
```

Pass `--runtime docker` or `--runtime podman` if you need to pick a runtime. `--help` lists all options.

## Data provenance

| Source | Role |
|--------|------|
| [turpinverse](https://github.com/markheydon/turpinverse) / [turpinverse.uk](https://turpinverse.uk/personas/dick-turpin/) | Canon persona, career, articles, gallery, and images |
| `site/data/profile/dick-turpin.json` | Hero, about, skills, contact, socials |
| `site/data/career/dick-turpin.json` | Experience, education, projects, achievements |
| `site/data/articles.json` | Blog posts authored by `dick-turpin` |
| `site/data/galleries.json` | Gallery images (`te-workplace-gallery`) |
| [markheydon.github.io](https://github.com/markheydon/markheydon.github.io) | Layout pattern only: Hugo module wiring, `hugo.yml` chrome, invoke script, archetypes, `.gitignore` |

Relative Turpinverse organisation paths are rewritten to `https://turpinverse.uk/...` so links work off that site. Biography text is Turpinverse canon; empty Profile fields are omitted rather than invented.

Images under `static/images/` are copied from the Turpinverse Hugo site (persona portraits, project/achievement SVGs). Gallery workplace photos use the Unsplash URLs already stored in Turpinverse canon.

## License

Site configuration follows the same MIT approach as the github.io skeleton. Turpinverse content and copied assets remain under the [Turpinverse MIT license](https://github.com/markheydon/turpinverse/blob/main/LICENSE). This demo does not include Mark Heydon’s personal github.io content.
