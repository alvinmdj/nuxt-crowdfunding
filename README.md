# Nuxt Crowdfunding

Front-end for crowdfunding app (Nuxt.js)

Back-end repository: [Go Crowdfunding](https://github.com/alvinmdj/go-crowdfunding)

## Links

- [Vue](https://vuejs.org/)
- [Nuxt](https://nuxtjs.org/)
- [Tailwind - Nuxt](https://tailwindcss.nuxtjs.org/)
- [Tailwind Nuxt Configuration](https://tailwindcss.com/docs/guides/nuxtjs)
- [ESLint Plugin Vue](https://eslint.vuejs.org/)
- [Auth - Nuxt](https://auth.nuxtjs.org/)
- [Auth - Nuxt (Local Scheme)](https://auth.nuxtjs.org/schemes/local)
- [Auth - Nuxt (API)](https://auth.nuxtjs.org/api/auth/)
- [Auth - Nuxt (Middleware)](https://auth.nuxtjs.org/guide/middleware)
- [Axios - Nuxt](https://axios.nuxtjs.org/)
- [Vue Router Object Props](https://v3.router.vuejs.org/api/#the-route-object)
- [Vue Toasted](https://github.com/shakee93/vue-toasted)
- [Nuxt Toast](https://www.npmjs.com/package/@nuxtjs/toast)
- [Nuxt Contexts Universal Keys](https://nuxtjs.org/docs/internals-glossary/context/#universal-keys)
- [Midtrans Sandbox Test](https://docs.midtrans.com/en/technical-reference/sandbox-test)
- [Setup Midtrans Redirection URL](https://dashboard.sandbox.midtrans.com/settings/snap_preference)
- [Setup Midtrans Redirection URL 2](https://dashboard.sandbox.midtrans.com/settings/vtweb_configuration)

## Requirements

- [Node.js v16+](https://nodejs.org/en/)
- [NPM v5+](https://www.npmjs.com/)

## Installation

- Clone this repository:

```sh
git clone https://github.com/alvinmdj/nuxt-crowdfunding.git
```

- Go to the root directory:

```sh
cd nuxt-crowdfunding
```

- Install dependencies:

```sh
npm install
```

- Run (development):

```sh
npm run dev
```

## Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out the [documentation](https://nuxtjs.org).

## Special Directories

You can create the following extra directories, some of which have special behaviors. Only `pages` is required; you can delete them if you don't want to use their functionality.

### `assets`

The assets directory contains your uncompiled assets such as Stylus or Sass files, images, or fonts.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/assets).

### `components`

The components directory contains your Vue.js components. Components make up the different parts of your page and can be reused and imported into your pages, layouts and even other components.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/components).

### `layouts`

Layouts are a great help when you want to change the look and feel of your Nuxt app, whether you want to include a sidebar or have distinct layouts for mobile and desktop.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/layouts).

### `pages`

This directory contains your application views and routes. Nuxt will read all the `*.vue` files inside this directory and setup Vue Router automatically.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/get-started/routing).

### `plugins`

The plugins directory contains JavaScript plugins that you want to run before instantiating the root Vue.js Application. This is the place to add Vue plugins and to inject functions or constants. Every time you need to use `Vue.use()`, you should create a file in `plugins/` and add its path to plugins in `nuxt.config.js`.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/plugins).

### `static`

This directory contains your static files. Each file inside this directory is mapped to `/`.

Example: `/static/robots.txt` is mapped as `/robots.txt`.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/static).

### `store`

This directory contains your Vuex store files. Creating a file in this directory automatically activates Vuex.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/store).
