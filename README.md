TailwindCSS Boilerplate Theme
=============================

### This is not a theme, it's much more!

TailwindCSS Boilerplate theme **is not a theme**, it's a boilerplate to create some awesome themes with all the developper's tools includes: TailwindCSS, Webpack, BrowserSync already configured to build with the OctoberCMS's directory structure, PostCSS with some the majors plugins, PurgeCSS, and all of this managed with NPM.

**Have fun!**

### TailwindCSS/Webpack/PostCSS ready

TailwindCSS, Webpack and PostCSS is already installed and pre-configured to work together. Each configuration file is pre-built but customizable.

This boilerplate comes with webpack and fully customised `webpack.config.js` file for OctoberCMS to manage all your assets: css, javascript, images, fonts and also all your template files: **Webpack will walk through all your directories and subdirectories** present in your theme folder to compile the .htm, .html and .txt files to catch all the assets dependencies you may have added in them!

PostCSS is the prepocessor of this boilerplate with the most used plugins. Feel free to add the plugins you want into the `postcss.config.js`

### PurgeCSS & Minification

To ensure the optimization of your final theme, all unused CSS will be removed with PurgeCSS, and all the JS and CSS files will be minified

### Auto-injection of CSS/JS

**All the files presents in the layouts directory** will **receive the CSS/JS** due to the Webpack auto-injection and a special rule for this directory.

### Auto-clean of previous build

This boilerplate uses `clean-webpack-plugin` to ensure you don't have any useless files in your theme folder. Your files is cleaned on every build webpack makes.

How to use
==========

### .env file needed

First of all: if it's not already the case, be sure to run `php artisan october:env`. This toolkit uses `APP_URL` inside of it to serve local server with BrowserSync and to correctly sets the paths of the assets. Be sure that it's correctly defined.

### NPM

Again, this theme is not a theme, it's a toolkit, based on NPM. To use it, be sure to have [node](https://github.com/nodejs/node) and [npm](https://github.com/npm/cli) installed on your machine.

Then, follow this quick steps:

1.  After installation of this toolkit (with git clone or from the OctoberCMS themes marketplace): rename the folder to what you want your theme's name to be.
2.  Modify the theme.yaml from sourcecode or OctoberCMS's administration with the theme's name, description, author, and so on...
3.  Run `npm install` from the theme directory to install dependencies.
4.  Run `npm run watch` to run the the development server with hot reload.
5.  Have fun!

Be aware of the fact that every times you create a new file, it can't be detected by the devServer, you need to reload `npm run watch` command.

### Folder structure, where to put your code.

Due to the pre-built configuration, you need to ensure all the modifications you make stay in the `src` directory. All directories, subdirectories and files will be cleaned and recreated by webpack on the root of the the theme'sroot folder. Think of the `src` directory as your **`root`** directory

The default directories and files structure of this boilerplate are:
```
/
/node_modules/ (after npm install)
/src/
    /assets/
        /css/
            entry.css (loads TailwindCSS and inserts your custom css at the right place)
            themes.css (your actual custom css)
        /fonts/
        /images/
            october.png
        /javascript/
            app.js (your custom javascript, copied from October's demo theme)
    /content/
    /layouts/
        /default.htm
    /pages/
        404.htm
        error.htm
        home.htm
    /partials/
        /site/
            footer.htm
            header.htm
    index.js
/package.json
/postcss.config.js
/README.md
/tailwindcss.config.js
/theme.yaml
/webpack.config.js
```


After webpack build, all the files in the src will be parsed and placed on the same structure from the root folder.

### How to handle images from HTML and CSS (and fonts)

##### From HTML:

Due to some webpack limitation, when you need to load file from the assets folder from the layouts, pages or partials, you will need to inserts them with special syntax:

```HTML
<img src=<%=require("./../images/october.png")%> />
```

Will render the following tag.

```HTML
<img src="https://your-domain.test/themes/your-theme-name/images/october.png" />
```

Be careful to call the relative path from the current compiled file: if you were in the `/partials/site/header.htm` file, this should have been `./../../assets/october.png`

##### From CSS:

From the CSS files, just use the url() as you usually do, for fonts, or images:

```CSS
.demo_url_in_css {
    background-image: url(../images/october.png);
}
```


Will render just as it is. The same rules apply for CSS and HTML insert: use relative path from the current CSS file to the images directory.