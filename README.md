# Gridsome Feed Plugin 

[![npm](https://img.shields.io/npm/v/@microflash/gridsome-plugin-feed)](https://www.npmjs.com/package/@microflash/gridsome-plugin-feed)
[![license](https://img.shields.io/npm/l/@microflash/gridsome-plugin-feed)](./LICENSE.md)

A Gridsome plugin to generate RSS, Atom and JSON feeds

## Install

```sh
yarn add @microflash/gridsome-plugin-feed
npm install @microflash/gridsome-plugin-feed
```

## Usage

```js
// gridsome.config.js

module.exports = {
  plugins: [
    {
      use: '@microflash/gridsome-plugin-feed',
      options: {

        // (required) Provide GraphQL collection types
        contentTypes: ['BlogPost'],

        // (optional) Properties used by feed API
        // See https://github.com/jpmonette/feed#example for all options
        feedOptions: {
          title: 'My blog',
          description: 'My Personal blog on books, cookies and kittens'
        },

        // Available options with their default values

        // (optional) Options for feed formats
        // RSS is enabled by default
        rss: {
          enabled: true,
          output: '/feed.xml'
        },
        atom: {
          enabled: false,
          output: '/feed.atom'
        },
        json: {
          enabled: false,
          output: '/feed.json'
        },

        // (optional) number of items to include in a feed
        maxItems: 25,

        // (optional) an array of properties to be parsed as HTML
        // Converts relative URLs to absolute URLs
        // You can disable this by omitting the option
        htmlFields: ['content'],

        // (optional) appends a trailing slash to the URLs
        enforceTrailingSlashes: false,

        // (optional) a function to filter out the nodes
        // e.g., filter out all outdated posts, filterNodes: (node) => !!node.outdated
        filterNodes: (node) => true,

        // (optional) sets the properties on each feed item
        // See https://github.com/jpmonette/feed#example for all options
        nodeToFeedItem: (node) => ({
          title: node.title,
          date: node.date,
          content: node.content
        })
      }
    }
  ]
}
```

## Contribute

Feel free to contribute to the project. Take a look at the [contribution guidelines](./CONTRIBUTING.md) to get started.

## Credits

[@onecrayon](https://github.com/onecrayon/gridsome-plugin-feed) for implementing the [original plugin](https://github.com/onecrayon/gridsome-plugin-feed)
