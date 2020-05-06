[setting up prettier on VS Code](https://travishorn.com/setting-up-prettier-on-vs-code-1fd5e5a43523)
https://www.robinwieruch.de/how-to-use-prettier-vscode
https://medium.com/alturasoluciones/eslint-basic-configuration-18b2109d98ec
https://itnext.io/how-eslint-makes-me-a-better-react-developer-237fb14c00ae


[ESLint with Prettier - Vue in VSCode](https://medium.com/@gogl.alex/how-to-properly-set-up-eslint-with-prettier-for-vue-or-nuxt-in-vscode-e42532099a9c)

ESLint + Prettier
- Prettier is opinionated code Formatter
- For the linting setup (one of the features of Prettier) I use ESLint
  - Prettier provides an ESLint config which everyone can use
- ESLint and Prettier are integrated directly into the VS Code
  - You need following ESLint + Prettier npm Packages:
    - eslint, prettier, eslint-config-prettier, eslint-plugin-prettier
    -  `npm i -D prettier eslint eslint eslint-config-prettier eslint-plugin-prettier`
  - Create **.eslintrc.js**
    - module.exports = { "extends" : "plugin:prettier/recommended"  }
    - or module.exports = { "extends": "airbnb-base" };
  - Create **.prettierrc**
    - { "semi": true, "trailingComma": "all", "singleQuote": true, "printWidth": 70, }
  - Install ESLint & Prettier Code Formatter VSCode Extensions
- Tip: save in settings
  - `"eslint.autoFixOnSave":true`
  - `"editor.codeActionsOnSave": { "source.fixAll.eslint": true }`
