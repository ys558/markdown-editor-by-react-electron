this project use the boilerplate [vite electron builder](https://github.com/cawa-93/vite-electron-builder), but the template use the vue to build it, I try to integrate it by react 

## copy and the template from my own repo

you may click here to copy the repo:

![]()

## remove packages from the template

uninstall the vue:

```bash
yarn remove vue vue-router vue-tsc @vitejs/plugin-vue eslint-plugin-vue
```


install react instead of :

react core module
```bash
yarn add react react-dom
```

for typescript and code formmater plugins: 
```bash
yarn add -D @types/react @types/react-dom @typescript-eslint/parser eslint-config-prettier @typescript-eslint/eslint-plugin @typescript-eslint/parser
```

## add some config for code formmater

`rm packages/renderer/.eslintrc.json` to remove the default renderer thread's `.eslintrc.json` config

```json
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
++  "prettier"
  ],
```

```json
{
  "extends": "../../tsconfig.json",
  "compilerOptions": {
    "baseUrl": ".",
++  "jsx": "react",
++  "allowSyntheticDefaultImports": true,
    "paths": {
      "/@/*": [
        "./src/*"
      ]
    },
    "lib": ["ESNext", "dom", "dom.iterable"]
  },

  "include": [
--  "src/**/*.vue",
    "src/**/*.ts",
    "src/**/*.tsx",
    "types/**/*.d.ts",
    "../../types/**/*.d.ts",
    "../preload/types/electron-api.d.ts"
  ]
}
```

`touch prettier.config.js`
```js
const options = {
  arrowParens: 'avoid',
  singleQuote: true,
  bracketSpacing: true,
  endOfLine: 'lf',
  semi: false,
  tabWidth: 2,
  trallingComma: 'none'
}

module.exports = options
```

## remove all the `vue` configs in project:

`packages/renderer/vite.config.js`
```js
-- import vue from '@vitejs/plugin-vue';

...

-- plugins: [vue()],
++ plugins: [],

...
```

`rm packages/renderer/types/shims-vue.d.ts`

delete all the `.vue` files:
```bash
find packages -type f | grep vue | xargs rm
```

rename `index.ts` to `index.tsx`
```bash
cd packages/renderer/src
mv index.ts index.tsx
```