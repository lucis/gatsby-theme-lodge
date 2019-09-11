# gatsby-theme-lodge

Gatsby theme for building beautiful and customisable landing pages for **Freemasons's Lodges.** (about [Freemasonry](https://en.wikipedia.org/wiki/Freemasonry))

_Built with :heart: for Brazilian Lodge "Acácia da Borborema" nº 41._

It uses [gatsby-transformer-pages-json](https://github.com/luciannojunior/gatsby-transformer-pages-json) for building the site with full customization.

**WIP ALERT:** I'm still building this architecture and it **will** change overtime. The page creation is stil being done in the theme side but we will probably overcome this issue and move it to the plugin.

## Install

`yarn add @luciannojunior/gatsby-theme-lodge`

## How to use

In your `gatsby-config.js`:

```javascript
module.exports = {
  plugins: [
    `@luciannojunior/gatsby-theme-lodge`,
  ],
}
```

## Configuring

Most of this theme's customization happens in `pages.json` file, that is created automatically on your site's `data` folder (you can change this with `contentPath` option). This file must follow this pattern:

```javascript
{
  "pages": {
    "home": {
      "homepage": true,
      "component": "Home",
      "props": {
        "landing": {
          "landingText": {
            "lodgeName": "Regeneração Campinense nº 02",
        ...
    },
   "o-que-e-maconaria": {
      "component": "Maconaria"
    },
    ...
  },
  "menu": [
    {
      "page": "home",
      "value": "Início"
    },
    ...
  ],
}
```

### Pages

The `pages` objects declares which pages will be created in the Gatsbys site.

- A simple _slugify_ heuristic is used using the page's _name_, which is described by the key provided (i.e: `"o-que-e-maconaria"` will create a page in the `/o-que-e-maconaria` path).
- The `component` provided will be resolved from `gatsby-theme-lodge/src/components` and rendered within the created page. We will provide default components to be used and you can also providing your own components using [Component Shadowing](https://www.gatsbyjs.org/blog/2019-04-29-component-shadowing/).
- You should provide a `homepage` boolean attribute as `true` to the home page of you site, so we will build this page's path in `/` (or in the `basePath` provided to themes's settings)

### Menu

- The `menu` array describes how the `Menu` component will show the items. It must reference `pages` by its name, or provide a `path` to a external URL.

## Components

### Landing

- Wraps a video background (or image background for mobile users) and displays a couple of information about the Lodge.

Configuration:

|Prop name|Type                          |Description                         |
|----------------|-------------------------------|-----------------------------|
|`landingText`|`Object`            |Describes the informations displayed in the Landing component (see [LandingText](#landing-text))|

### LandingText

- Displays an animated set of texts to describe the Lodge

Configuration:

|Prop name|Type                          |Description                    | Example |
|----------------|-------------------------------|-----------------------------| -----|
|`location`|`String`            | Textual address of the Lodge| `Situada na Rua Siqueira Campos, Campina Grande - PB` |
|`lodgeName`|`String`            |Name of the Lodge|`Regeneração Campinense nº 02`|
|`meetings`|`String`            |When do the Lodge's meetings happen?|`quartas-feiras às 19:00hrs`|

**WIP**
