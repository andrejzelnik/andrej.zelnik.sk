# andrej-site-content

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
.splash {
    h2 {
        font-size: 1.5em;
    }
}

.social-icons__link {
    padding: 1.33rem;
}

.main {
    height: 100%;
}
EOF
```
```bash
mkdir -p ./assets/scss && cat <<EOF > ./assets/scss/overrides.scss
// overrides.scss
\$navWidth: 1px;
\$primary: #88b04b;
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