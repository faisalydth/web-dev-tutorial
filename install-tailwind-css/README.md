# Install Tailwind CSS

## Documentation
https://tailwindcss.com/docs/installation

## Preparation
- VSCode Extension
  - Tailwind CSS IntelliSense
  - Live Preview
  - PostCSS Language Support
- Package Manager
  - NPM (node.js)

## Installation via CDN

```html
<head>
  <!-- CDN script -->
  <script src="https://cdn.tailwindcss.com"></script>
  
  <!-- Customizing configuration -->
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            clifford: '#da373d',
          }
        }
      }
    }
  </script>
  
  <!-- Adding custom CSS -->
  <style type="text/tailwindcss">
    @layer utilities {
      .content-auto {
        content-visibility: auto;
      }
    }
  </style>
</head>
```

## Installation via CLI

Initialize the application to create `./package.json`.

```ps
$ npm init -y
```

Install Tailwind, PostCSS, and Autoprefixer to create `./node_modules` folder and assign `devDependecies` value in `./package.json`.
```ps
$ npm install -D tailwindcss postcss autoprefixer
```

Initialize Tailwind to create `./tailwind.config.js` for configuration.
```ps
$ npx tailwindcss init
```

Configure paths in `./tailwind.config.js`.
```js
module.exports = {
  content: ["./*.html", "./main/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Create `./input.css` which contains Tailwind directives to main CSS file.

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Execute Tailwind where the input is `./input.css` and the output is `./main/css/main.css`.
```ps
$ npx tailwindcss -i ./input.css -o ./main/css/main.css --watch
```

Add compiled CSS file to the `<head>` of HTML file.
```html
<head>
  <link href="./main/css/main.css" rel="stylesheet">
</head>
```

To reduce size of main CSS file, execute this code in CLI.
```ps
$ npx tailwindcss -o ./main/css/minify.css --minify
```

Change the reference of compiled CSS file to minify CSS file in HTML file.
```html
<head>
  <link href="./main/css/minify.css" rel="stylesheet">
</head>
```

Save the above code in the `script` key in `./package.json` for shortcut.
```json
{
    "scripts": {
    "watch": "npx tailwindcss -i ./input.css -o ./main/css/main.css --watch",
    "minify": "npx tailwindcss -o ./main/css/minify.css --minify"
  }
}
```

Run the script in CLI.
```ps
$ npm run watch
$ npm run minify
```
