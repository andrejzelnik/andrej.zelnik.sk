# site-content-andrej

Minimalist content generator for my personal [andrej.zelnik.sk](https://andrej.zelnik.sk) website.

Based on [Hugo](https://gohugo.io/).

## initialization

Go see https://gohugo.io/getting-started/quick-start/ or simply do following:

```bash
# install hugo
brew install hugo

# create a new site (within this folder)
hugo new site . --force
```

## customization

Customize the new site and add a theme (see https://themes.gohugo.io/), [Codex](https://themes.gohugo.io/hugo-theme-codex/) Hugo theme in this case:

```bash
git submodule add https://github.com/jakewies/hugo-theme-codex.git themes/hugo-theme-codex
```

Copy the contents of the [`exampleSite/config.toml`](https://github.com/jakewies/hugo-theme-codex/blob/master/exampleSite/config.toml) to your site's `config.toml`.

```bash
curl -o config.toml https://raw.githubusercontent.com/jakewies/hugo-theme-codex/master/exampleSite/config.toml
```

Modify `config.toml` and remove [this line](https://github.com/jakewies/hugo-theme-codex/blob/master/exampleSite/config.toml#L2)

```bash
sed '/themesDir/d' config.toml > temp && mv temp config.toml
```

Copy the source files:

```bash
cp -R ./themes/hugo-theme-codex/archetypes/ ./archetypes
cp -R ./themes/hugo-theme-codex/assets/ ./assets
cp -R ./themes/hugo-theme-codex/layouts/ ./layouts
cp -R ./themes/hugo-theme-codex/static/ ./static
```

Configure the homepage:

```bash
cat <<EOF > ./content/_index.md
---
heading: "Hi, I'm Andrej"
subheading: "• minimal site • maximal life •"
handle: "zelnik.sk"
---
EOF
```

```bash
mkdir -p ./assets/scss && cat <<EOF > ./assets/scss/custom.scss
// custom.scss
.main {
    height: 100%;
}

.splash {
    h2 {
        font-size: 1.5em;
    }
}

.social-icons {
    justify-content: center;
    align-items: center;
    margin: 0;
}

.social-icons__link {
    padding: 0.2rem 1rem;

    &:not(:last-child) {
        margin: 0;
    }

    .social-icons__icon {
        -webkit-filter: invert(100%); /* safari 6.0 - 9.0 */
        filter: invert(100%);
    }
}
EOF
```
```bash
mkdir -p ./assets/scss && cat <<EOF > ./assets/scss/overrides.scss
// overrides.scss
\$navWidth: 0;
\$meatWidth: 0;
\$meatHeight: 0;
\$burgerContainerHeight: 0;

\$black: #fff;
\$white: #111;
\$primary: #d4ff47;
//\$primary: #88b04b;
EOF
```

Favicon generator: https://favicon.io/favicon-generator/

```
text:               a
background:         rounded
font family:        Fugaz One
font size:          125
font color:         #fff
background color:   #000
```

Download and copy the content into `./static` folder.

Modify `config.toml` based on your needs and finally run:

```bash
hugo server -D
```

## github actions

see:
- https://github.com/marketplace/actions/hugo-setup
- https://github.com/marketplace/actions/deploy-to-azure-storage