# Vuepress typescript plugin test

Example repo to test [`vuepress-plugin-typescript`](https://vuepress.github.io/en/plugins/typescript/)

## Before starting
```sh
# INSTALL DEPs
npm i
# START DEV SERVER
npm run dev
```

## Commits as `steps`

### 🔥 [Initial commit](https://github.com/salazarr-js/vuepress-ts/commit/cd5be2edecff6a09b6bfbd973100d69eb939d75b)

1. Create this `readme.md`
2. Add scripts to `package.json`
```json
"scripts": {
  "dev": "vuepress dev",
  "build": "vuepress build"
}
```
3. Add basic info to `.vuepress/config.js`
```javascript
module.exports = {
  title: 'Vuepress Typescript',
  description: 'Vuepress typescript plugin tests'
}
```

### 👨‍💻 [Typescript plugin](https://github.com/salazarr-js/vuepress-ts/commit/2ef25e9285cf86df68c5e6c1cbd0f5d47bd73a93)

Following the [vuepress-plugin-typescript](https://vuepress.github.io/en/plugins/typescript/#installation) docs.

1. Installation
```sh
npm install -D vuepress-plugin-typescript typescript
```

2. Add to plugins array in `.vuepress/config.js`
```javascript
module.exports = {
  plugins: [
    ['vuepress-plugin-typescript'],
  ]
}
```

3. Add some `typescript` script in `readme.md`

```html
{{ msg }}

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data: () => ({
    msg: 'Hello, TypeScript in Markdown!',
  }),
})
</script>
```

4. Wild error appears 🤯

![error screenshot](./screenshot.png)

> Same error if there is a `<script lang="ts">` in a `.vue`


### 🔨 [Workaround](https://github.com/salazarr-js/vuepress-ts/commit/2687d1d0722c8e54adab78919597178db1b89c69)

To make it works just:

1. Add any `.ts` file in folder
  > For example `.vuepress/enhanceApp.ts`
2. Add a `tsconfig.json` with at least `include` file paths
```json
{
  "include": [
    ".vuepress/**/*.ts",
    ".vuepress/**/*.vue"
  ],
  "exclude": [
    "node_modules"
  ]
}
```

---

### {{ msg }} 🎉🍻

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data: () => ({
    msg: 'Hello, TypeScript in Markdown!',
  }),
})
</script>
