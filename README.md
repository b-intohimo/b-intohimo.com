# b-intohimo.com — Site Content (GitHub)

WordPress page content for [b-intohimo.com](https://b-intohimo.com).  
Gutenberg block HTML + brand CSS. Edit here, sync to WordPress via the **GitHub Sync** plugin.

## Repository layout

```
content/pages/     ← WordPress page content (one .html file per page)
assets/style.css   ← Brand styling (loaded by b-intohimo Site Content plugin)
forms/             ← WPForms import (contact-form.json)
manifest.json      ← Page mapping reference
```

## Contact form (WPForms)

1. Import **`forms/contact-form.json`** via **WPForms → Tools → Import**
2. Note the form ID under **WPForms → All Forms** (default embed uses ID `1`)
3. If ID differs, update `content/pages/contact.html` and `forms/config.json`
4. **Fetch from GitHub** on WordPress to refresh the Contact page (or rebuild pages)

See **`forms/README.md`** for details.

## Pages

| File | WordPress page | URL |
|------|----------------|-----|
| `home.html` | Home | `/` |
| `about.html` | About | `/about/` |
| `services.html` | Services | `/services/` |
| `software.html` | Custom Software | `/software/` |
| `testing-robots.html` | Testing Robots | `/testing-robots/` |
| `technology.html` | Technology | `/technology/` |
| `contact.html` | Contact | `/contact/` |

## Push this package to GitHub

### Option A — This folder is the repository root (recommended)

```bash
cd site-github
git init
git add .
git commit -m "Initial b-intohimo site content"
git branch -M main
git remote add origin git@github.com:YOUR-ORG/b-intohimo-site.git
git push -u origin main
```

### Option B — Add to an existing repository

Copy the contents of `site-github/` into your repo (e.g. as `site/` or repo root), commit, and push.

## WordPress GitHub Sync settings

In **Tools → GitHub Sync** (plugin v1.1.0+):

| Setting | Value |
|---------|--------|
| Content path prefix | `content/pages/` |
| Discover GitHub files | ✓ |
| Create missing pages | ✓ |

**All pages sync automatically** by slug: `{slug}.html`. Add a new page in WordPress or a new `.html` file in GitHub — both directions work.

## Sync workflow

### Git → WordPress (deploy content)

1. Edit files in `content/pages/` (and `assets/style.css` if needed)
2. Commit and push to `main` (or merge a PR)
3. In WordPress: **Tools → GitHub Sync → Fetch from GitHub**

### WordPress → Git (send changes for review)

1. Change content in WordPress (or rebuild from plugin files)
2. **Tools → GitHub Sync → Push to GitHub**
3. Review and merge the pull request on GitHub

## Editing content

Files use **WordPress block markup** (HTML comments + blocks). Example:

```html
<!-- wp:heading {"level":1} -->
<h1 class="wp-block-heading">Title</h1>
<!-- /wp:heading -->
```

After editing HTML locally, always **Fetch from GitHub** on WordPress (or copy updated files into the `b-intohimo-content` plugin and click Rebuild).

## CSS

`assets/style.css` contains brand colors and layout:

- Primary blue: `#5060a0`
- Navy: `#001080`
- Gray: `#a0a0a0`

Copy to `wp-content/plugins/b-intohimo-content/assets/style.css` when styles change, or keep in sync via your deployment process.

## Required WordPress plugins

1. **b-intohimo Site Content** — creates pages, loads CSS
2. **b-intohimo GitHub Sync** — Fetch / Push buttons

Both are in `wordpress/wp7/` in the main project.
