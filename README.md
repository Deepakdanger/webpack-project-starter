# webpack-project-starter


Welcome to my webpack starter for microverse

### Setup

clone repo and run

```bash
npm install
```

### Project structure
All files are in src folder. There is no need for dist folder. script tags and style tags for files in src in html are also not necessary. They will auto injected by webpack. You can put CDN links for bootstrap, font-awesome etc in the html file.

* Write your html in `src/index.html` file.
* Write your javascript in `src/`. 
* Write your styles in `src/index.scss` and import it in `index.js`
```js
import 'index.scss';
```
* The final project assets will be in `dist` folder after build command in production section below. This is useful for publishing to github and for the lighthouse linter in github.
###

## For development
You have live updates for javacript and scss in `localhost:3000`. Refresh after changes to html.

1. Run in your terminal and keep it running, the project will be available live with hot reloading at `localhost:3000`. Happy programming : )
```bash
npm run dev
```
2. Keep the import for scss in `index.js` if you want scss styles.
```js
import 'index.scss';
```

You can change localhost:port number in webpack/webpack.config.dev.js's port property
```js
  devServer: {
    contentBase: "./dist",
    hot: true,
    port: "3000", //change here to your port
  }
```
### Html in dist folder 
if you want html in dist folder instead of src folder
remove the plugin `HtmlWebpackPlugin`. You can also remove the `Dotenv` plugin if you are not using any `.env` file.

```js
  plugins: [
    new Dotenv(),
      filename: "index.html",       // remove this line
      template: "/src/index.html",  //remove this line
      inject: true,                 // remove this line
    }),                             // remove this line
  ],
```

### Env file for environment variables such as API_KEY
create an `.env` file for your variables
```.env
API_KEY=20r8304283yourkeyexample
```
and import it in js

```js
const { API_KEY } = process.env
```
if you arent using any environment, you can also safely remove the `new Dotenv()` plugin from the webpack config files.

## For linters
All commands have --fix appended internally already.

One command for all linters
```
npm run linters
```

### Standalone linters
* eslint
```bash
npm run eslint
```
* stylelint
```bash
npm run stylelint
```
* webhint
```bash
npm run hint
```

## For production
One command to create production code and publish live on github. After project completion. Helpful for lighthouse linter on github pull request.

```bash
npm run publish
```
or seperately run,

1. Build final production project build
```bash
npm run build
```
2. Run in terminal to push your created`dist` folder to github to get a live website on github
```bash
npm run live
```
