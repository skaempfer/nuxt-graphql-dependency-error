# Nuxt GraphQL Depencency Error Reproduction

This project demonstrates the occurence of a runtime error when using GraphQL inside a Nuxt application.

## Setup

Run `npm ci` to install project dependencies.

## Code Points of Interest

The graphql dependency is imported and used inside the `app.vue` component.

## Error Reproduction

The error reproduction involves building and running the application in production mode on Windows and Linux. The following environments have been used to run the applications:

 - Windows 11 22H2
 - Linux 5.15.90.1-microsoft-standard-WSL2
 - Node 18.18.1

 Execute the following steps in both Linux and Windows environment:

 1. Run `npm run build` to build the app in production mode
 2. Run `npm run preview` to start application
 3. Open a browser and navigate to `http://localhost:3000` (default port used by the app)

 Expected behaviour in both environments:

 - On Linux you will be served the Nuxt example page
 - On Windows you will be served a server error page 500. Observing the console output you will see the following message
    ```
    [nuxt] [request error] [unhandled] [500] Cannot find package '<yourpath>\nuxt-graphql-dependency-error\.output\server\node_modules\graphql\' imported from <yourpath>\throwaway-projects\nuxt-graphql-dependency-error\.output\server\chunks\app\server.mjs
      at new NodeError (node:internal/errors:405:5)
      at legacyMainResolve (node:internal/modules/esm/resolve:234:9)
      at packageResolve (node:internal/modules/esm/resolve:877:14)
      at moduleResolve (node:internal/modules/esm/resolve:939:20)
      at defaultResolve (node:internal/modules/esm/resolve:1132:11)
      at nextResolve (node:internal/modules/esm/loader:163:28)
      at ESMLoader.resolve (node:internal/modules/esm/loader:835:30)
      at ESMLoader.getModuleJob (node:internal/modules/esm/loader:424:18)
      at ModuleWrap.<anonymous> (node:internal/modules/esm/module_job:77:40)
      at link (node:internal/modules/esm/module_job:76:36)
    ```
