# Hello World! Express API 

## Overview

This is a simple "Hello World!" API, build with Node.js, Typescript and Express. The steps below are used to create this API, if you just want to run the app, clone the repository and skip to the [Usage](##Usage) chapter.

1. In your project folder, create a `src` folder with an empty `index.ts` file

2. Create a node project with default configutations `-y`
    ```
    npm init -Y 
    ```
3. Install Express
    ```
    npm i express
    ```
4. Install Typescript and others devDependecies `-D`
    ```
    npm i -D typescript ts-node-dev @types/express
    ```
    [ts-node-dev](https://www.npmjs.com/package/ts-node-dev): It restarts target node process when any of required files changes (as standard node-dev) but shares Typescript compilation process between restarts. This significantly increases speed of restarting comparing to node-dev -r ts-node/register ..., <b>nodemon</b> -x ts-node ... variations because there is no need to instantiate ts-node compilation each time.
    
    [@types/express](https://www.npmjs.com/package/@types/express) This package contains type definitions for Express
5. Create a `tsconfig.json` file with default compiler options
    ```
    npx tsc --init
    ```
    Open the file created in your root directory, and add the lines below
    ```json
    "rootDir": "src",
    "outDir": "dist"
    ```
    This will tell the typescript compiler where the source (`"rootDir": "src"`) of the `.ts` files are, and where to generated the compiled `.js` files (`"outDir": "dist"`).
6. Add a start script in `package.json `
    ```
    "start": "tsnd --respawn --transpile-only src/index.ts",
    ```
    This command is executed by the `ts-node-dev` package, it will start the server and restarts node process, if any `.ts` files are changed.
7. Paste de code below in your `index.ts` file
    ```typescript
    import express from 'express';

    const app = express();
    const port = 3000

    app.get('/', (req, res) => {
        res.send('Hello World!')
    })

    app.listen(port, () => {
        console.log(`Example app listening at http://localhost:${port}`)
    })
    ```

## Usage
Install the dependencies in the `package.json` file
```
npm i
```
Start the app
```
npm start
```
App is running in [localhost:3000](http://localhost:3000)
