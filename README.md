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