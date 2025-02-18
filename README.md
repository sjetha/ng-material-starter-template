# ng-material-starter-template

[![Build and Deploy](https://github.com/sardapv/ng-material-starter-template/actions/workflows/build-deploy.yml/badge.svg?branch=main)](https://github.com/sardapv/ng-material-starter-template/actions/workflows/build-deploy.yml) ![GitHub](https://img.shields.io/github/license/sardapv/ng-material-starter-template) ![GitHub release (latest by date)](https://img.shields.io/github/v/release/sardapv/ng-material-starter-template) ![Angular](https://img.shields.io/badge/Angular-12.0.0-red) ![TailwindCSS](https://img.shields.io/badge/tailwindcss-2.1.2-%2306B6D4) ![Cypress](https://img.shields.io/badge/cypress-7.5.0-%23012) ![Jest](https://img.shields.io/badge/jest-27.0.4-%2316C213)

This repo is starter template with must have features/dependencies so that you don't need to write from scratch.

<img src="https://user-images.githubusercontent.com/14892874/119226913-1e386e00-bb29-11eb-8d54-d64ce453f5f6.png" width="200" height="200">

This project is generated using latest Angular CLI 12.0.0

If you like this, do give it a 🌟 ! 😊

# [Sample Demo 🚀](https://sardapv.github.io/ng-material-starter-template/)

To start with open this project and replace '**project-name**' with _your_project_name_ across all files.

# This project is starter kit with below features

- Project Structure inspired form [Rik De Vos's blog](https://medium.com/dev-jam/5-tips-best-practices-to-organize-your-angular-project-e900db08702e)

  - prod configuration setup and env with baseURL field injected in app.module
  - 3 main modules (extended notes to be added soon) -

    - common annotations like @shared, @feature, @core added in tsconfig.json
    - CoreModule - only to be imported in Appmodule

      - Auth Guard
      - A broadcaster service included which listens to your key:value pair of events anywhere in app. Here is how to use

        - ```ts
          constructor(private _broadcatser: BroadcasterService) {}
          ```
        - to broadcast and listen anywhere

          ```ts
          this._broadcatser.broadcast('mykey', 'myvalue');

          // to listen inside any component inject service there and do simply below

          /* use this service with takeUntil from rxJS and local Subject &
           * destroy in OnDestroy to prevent memory leaks
           */

          this._broadcatser.listen('mykey').subscribe({
              next:(data) => console.log(data) // your broadcasted value
            })
          }
          ```

    - FeatureModule - all lazyloaded pages/modules goes here

      - before-login modules
      - after-login modules

    - SharedModule - only to be shared and imported in feature modules

      - Can have custom components as SCAM
        (sample scam component as independent module included: recommended (rather than creating big shared module))
      - Custom Pipes, Directives, Components, Models, Validators folders to organise
      - index.ts provided for shared.module.ts (to organise imports)

- Basic Auth service like (Refer model in model folder & change accordingly)

  - login
  - refreshtoken
  - storetoken
  - getTokens
  - logout

- HTTP Request Interceptor extended to and inspired from [Rich Franzmeier's blog](https://www.intertech.com/author/rich-franzmeier/ 'Posts by Rich Franzmeier')

  - just provide base url in environment.ts and api paths in service.ts use for e.g '/action/endpoint'
  - request cloner
  - header modifier
  - success and error handler
  - refresh token handler

- Tailwind and Custom Configuration

  - sample tailwind configuration with font, theme and other properties (tailwind.config.js)

- Angular Material Component & CDK integrated

  - Material theme starter pack included, just change colors inside `_mat_\*.scss` files

- Icons and Typography (CDN links - index.html)

  - Angular Material Icons added
  - Default Poppins, OpenSans font integrated

- pollyfills (for safari) '_web-animations-js_' added for animations support inside _@Component_ decorator
- Styles folder with subfolder added inside stylePreprocessorOption (angular.json)
- local prod-build host and run (run `npm run prod-test`)
- PurgeCSS post-build script for tiny css in kbs (`npm run purgecss`)

  - Run `npm run final-build` which takes care of prod build and purge script together

- webpack-bundle-analyzer and source-map-explorerc configured (run `npm run source` or `npm run webpack-analyze` , you choose 😉)
