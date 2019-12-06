# WebComponentEnv
## What?:
A minimal setup for web development using [web components](https://www.webcomponents.org/introduction), [heresy](https://github.com/WebReflection/heresy) ,sass and [@pika/web](https://github.com/pikapkg/web)(simple and frameless and no transpilation and no bundling and no IE and yes ES modules)

Note: heresy and sass are my personal preferences, you can replace them with yours.

## Why?:
You might not really need webpack bundling or babel transpile or all those other steps. If you are on some traditional frontend stack/setup redo-ing all that stuff in React or Angular or Vue echo system might not be the right thing. It might be extremely costly and painful too. You may be already taking care of all those and more(like routing, session management) in your current django, spring/java(God forbid JCR/@EM), php and/or mvc framework. All that is production(i.e. battle) tested and you sure would move to Http2, be InternetExplorer-free and hopefully embrace ES-modules. You surely don't need two seperate dev-environments, constantly pluging some bundle.js or main.js into your current system.  So, Why not? 

## How?:
You will have to make changes to package.json based on your current project and frameworks directory structure and scaffolding 

Like in "django" you might changes this package.json->"scripts" to somthing like: 
```
"scripts": {
    "start": "npm run build-css & es-dev-server --watch --open --host 127.0.0.1 --port 3000",
    "postinstall": "npx @pika/web --dest ./com/static/webmodules",
    "lint": "eslint --ext. js --quiet",
    "format": "prettier \"./**/*.{js,scss,html}\" --write",
    "test": "echo \"Error: no test specified\" && exit 1",
    "build-css": "node-sass static -o static --output-style=expanded -i",
    "build-css-app": "node-sass $APP -o $APP --output-style=expanded -iw",
    .
    .
    "pyka-install": "npm install $pkg --save & npm run postinstall"
  }
  ```
You will need to change "scripts"->"postinstall" based on where you want to save webmodules(compiled yes-modules). You can then import those modules into your component's django templates, statitc js files or other js compomonents. 
Note: you really don't need to run or have "es-dev-server" unless for running some statics in isolation in development/test. Just doing "npm run build-css & npm run format ...." based on your project needs might suffice.   