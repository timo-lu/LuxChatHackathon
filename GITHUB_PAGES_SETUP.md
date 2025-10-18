# GitHub Pages Setup Instructions

This repository is now configured for GitHub Pages hosting. Follow these steps to enable it:

## Enabling GitHub Pages

1. Go to your repository on GitHub: https://github.com/timo-lu/LuxChatHackathon
2. Click on **Settings** (gear icon)
3. In the left sidebar, click on **Pages**
4. Under **Source**, select the branch you want to use (typically `main` or `copilot/prepare-docs-for-github-io`)
5. Under **Folder**, select `/ (root)` since we have the `_config.yml` in the root
6. Click **Save**

## Accessing Your Documentation

Once enabled, your documentation will be available at:

**https://timo-lu.github.io/LuxChatHackathon/docs/**

The main documentation hub is at: `https://timo-lu.github.io/LuxChatHackathon/docs/index.html`

## What Was Configured

### Files Added/Modified:

1. **`_config.yml`** - Jekyll configuration file with:
   - Site title and description
   - Theme: `jekyll-theme-cayman`
   - Proper baseurl and url settings
   - Collections configuration for docs

2. **`docs/index.md`** (renamed from `INDEX.md`) - Main documentation hub with:
   - YAML front matter for Jekyll
   - Links to all documentation pages

3. **All documentation files** - Added YAML front matter to:
   - `docs/matrix-protocol.md`
   - `docs/luxchat-source.md`
   - `docs/development-setup.md`
   - `docs/api-references.md`
   - `docs/tools-and-utilities.md`
   - `docs/resources/external-links.md`
   - `docs/resources/TEMPLATE.md`
   - `docs/diagrams/README.md`

4. **`.gitignore`** - Added Jekyll build artifacts exclusions:
   - `_site/`
   - `.sass-cache/`
   - `.jekyll-cache/`
   - `.jekyll-metadata`
   - `Gemfile.lock`

5. **`README.md`** - Updated to:
   - Reference `docs/index.md` instead of `docs/INDEX.md`
   - Include GitHub Pages URL
   - Update structure documentation

## Theme

The site uses the **Cayman** theme, which provides a clean, professional look. You can change this in `_config.yml` by modifying the `theme` line to any of the [supported GitHub Pages themes](https://pages.github.com/themes/).

## Customization

### Changing the Theme

Edit `_config.yml` and change the `theme` value to one of:
- `jekyll-theme-cayman`
- `jekyll-theme-minimal`
- `jekyll-theme-architect`
- `jekyll-theme-slate`
- `jekyll-theme-dinky`
- `jekyll-theme-hacker`
- `jekyll-theme-leap-day`
- `jekyll-theme-merlot`
- `jekyll-theme-midnight`
- `jekyll-theme-minima`
- `jekyll-theme-modernist`
- `jekyll-theme-tactile`
- `jekyll-theme-time-machine`

### Adding New Pages

1. Create a new `.md` file in the `docs/` directory
2. Add YAML front matter at the top:
   ```yaml
   ---
   layout: default
   title: Your Page Title
   ---
   ```
3. Write your content in Markdown
4. Add a link to the new page in `docs/index.md`

## Testing Locally (Optional)

To test the site locally before deploying:

1. Install Ruby and Jekyll:
   ```bash
   gem install bundler jekyll
   ```

2. Create a `Gemfile` in the root:
   ```ruby
   source "https://rubygems.org"
   gem "github-pages", group: :jekyll_plugins
   ```

3. Install dependencies:
   ```bash
   bundle install
   ```

4. Run the local server:
   ```bash
   bundle exec jekyll serve
   ```

5. Visit `http://localhost:4000/LuxChatHackathon/` in your browser
   - Main documentation: `http://localhost:4000/LuxChatHackathon/docs/`

## Troubleshooting

### Pages not updating
- GitHub Pages can take a few minutes to build and deploy changes
- Check the Actions tab in your repository for build status

### 404 errors
- Make sure the branch and folder are correctly set in Settings > Pages
- Verify the `baseurl` in `_config.yml` matches your repository name

### Theme not applying
- GitHub Pages only supports certain themes
- Make sure the theme name in `_config.yml` is exact

## Additional Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Themes](https://pages.github.com/themes/)
- [Jekyll Front Matter](https://jekyllrb.com/docs/front-matter/)
