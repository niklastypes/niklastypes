# ⌨️ Dev Blog: Development

> This repo doubles as the GitHub profile repo, so the root `README.md` is the profile card. Site docs live here.

Static personal website using [Hugo](https://gohugo.io/) and the [Blowfish](https://github.com/nunocoracao/blowfish) theme.
Deployed via GitHub pages to my custom domain https://niklastypes.xyz.

## Requirements

To run the web server:
```bash
brew install hugo
```

## Setup

As this project is using Blowfish as a git submodule, run the following once:

```bash
git submodule update --init --recursive
```

Then, start up the web server locally via

```bash
hugo server
```

and view on http://localhost:1313/.

## Color scheme

The Blowfish theme has been customized to follow the [Congo](https://github.com/jpanther/Congo) theme color scheme.
The respective `img/backgrounds/*.svg` assets have been adapted as follows:

```
#5e6fa3 -> #6d40d9
#689cc5 -> #b99af4
#93dbe9 -> #e2d4ff
```

The respective `img/featured/*.svg` assets have been adapted as well:

```
#48cae4 → #6d40d9
#03045e -> #5a2fc7
#023e8a -> #6d40d9
#0077b6 -> #8b5de8
#0096c7 -> #b99af4
#00b4d8 -> #b99af4
#90e0ef -> #d1b9f8
#ade8f4 -> #e2d4ff
#caf0f8 -> #f0e8ff
```

## Comments

Article comments are powered by [Giscus](https://giscus.app/), which uses this repo's GitHub Discussions as the backend.
Comments are enabled globally via `article.showComments` in `config/_default/params.toml`, and the Giscus widget is configured in `layouts/partials/comments.html`.

## About page

The About page (`content/about.md`) renders this repo's root `README.md`, the GitHub profile card, through the `profile` shortcode (`layouts/shortcodes/profile.html`), called as `{{% profile %}}` so its headings show up in the table of contents. Editing the README updates both GitHub and the site on the next deploy. Anything after the `<!-- about:end -->` marker in the README stays GitHub-only; site-only sections live below the shortcode in `about.md`. `hugo server` doesn't watch the README, so restart it to see local README edits.
