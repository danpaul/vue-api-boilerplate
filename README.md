# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

This template comes with two essential libraries, Vue Router for routing and Vue Query for making API requests. [Pico CSS](https://picocss.com/docs) for basic semantic styling is also included.

It is strongly recommended that you read through this README thoroughly. It takes time but _will save you time in the longrun_!

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Vue - Official](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (previously Volar) and disable Vetur

## Getting Started

If you downloaded or cloned this repo, to get started you only need to:

- make sure you have npm installed on your computer
- open the directory in terminal
- run `npm install`
- run `npm run dev`

These are the steps that you can take if you want a setup like this with the most recent packages.

- have npm installed on your system
- init a vite project: npm create vite@latest
- select Vue as framework
- opt for plain JS, not TypeScript
- cd into the newly create project direction
- run `npm install`
- run `npm run dev`
- you should now be able to see the app running in your browser
- install `vue-router`
  - `npm install vue-router --save`
  - read the Vue Router guide: https://router.vuejs.org/guide/
- install `@tanstack/vue-query`
  - `npm install @tanstack/vue-query` --save
  - read the docs: https://tanstack.com/query/v4/docs/framework/vue/quick-start

## Main Files

- `main.js` - initializes the Vue app and mounts it to the DOM. This is also where Vue plugins (i.e. Vue Router, Vue Query) are added.
- `Router.js` - defines application routes
- `App.vue` - provides the main template for the app. Note how links to routes are contstructed using Vue Router in this file (they are not `<a>` elements).
- `src\components\containers\TransactionsContainer.vue` - demos how to use Vue Query to make requests to the API

## Component Organization

- `./src/components/pages`: Top level page components.
- `./src/components/containers`: Components that handle interaction with the API.
- `./src/components/common`: All other shared components that do not interact directly with the API.
