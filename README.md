## Vue Leaflet

Hello nice people! This is a Vue Leaflet project.

What you will see is a map with OSM layers, markers, popup and data visualization at the click of markers ( lat, long, city, images ).
In order to implement this project in Vue + Vite environment, I had to install the npm dependencies and import the links to the CDN (each step will be described below).
By installing only the npm dependencies some bugs surfaced during the creation of the project.
This was my personal resolution.

⚠️Please Note:
Below I report precious information, I thank all the community that works for an open source world🍀:

https://www.npmjs.com/package/@vue-leaflet/vue-leaflet?activeTab=readme

https://vue2-leaflet.netlify.app/

## Inizialize a Vue3 + Vite project
(commit: setting Vue3 + vite project)

⚠️ The Essential Vue project extensions:

Vue Language Features (Volar) [Visual Studio Code]
Vue.js devtools [ Chrome ] https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd

- after cloning the repo open the terminal from VSC and type: npm create vite@latest . -- --template vue

- to view always from the terminal: npm i && npm run dev

- delete the style.css file

- edit the main.js file: FROM import './style.css' TO import './assets/scss/app.scss'

- in the 'src' folder --> create 'assets' folder --> create app.scss file

- Install the SASS package from the terminal: npm add -D sass

- install Bootstrap: npm i bootstrap @popperjs/core (@popperjs/core these are two libraries that allow you to use Bootstrap 100%)

## Inizialize Vue Leaflet project
(commit: install vue leaflet)

- Installations:
npm install @vue-leaflet/vue-leaflet && npm install leaflet

- CDN
Import the CDN dependencies into the index.html file: 
<!-- CDN link Leaflet -->
<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>


# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).
