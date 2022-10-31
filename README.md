<p align="center">
  <a href="https://www.bigcommerce.com/apps/stand-with-ukraine/">
    <picture aria-label="Stand with Ukraine App logo">
      <img src="https://s3.amazonaws.com/integrated-apps/nbxgitdu/mvcrlqjk.png" height="128">
    </picture>
    <h1 align="center">Stand with Ukraine App</h1>
    <h3 align="center">Frontend Components</h3>
  </a>
</p>

<p align="center">
  <a aria-label="Coverage" href="https://coveralls.io/github/bigcommerce/stand-with-ukraine-frontend?branch=main">
    <img src="https://img.shields.io/coveralls/github/bigcommerce/stand-with-ukraine-frontend/main?style=for-the-badge&labelColor=005BBB">
  </a>
  <a aria-label="Maintainability" href="https://codeclimate.com/github/bigcommerce/stand-with-ukraine-frontend/maintainability">
    <img alt="" src="https://img.shields.io/codeclimate/maintainability/bigcommerce/stand-with-ukraine-frontend?style=for-the-badge&labelColor=005BBB">
  </a>
  <a aria-label="Build Status" href="https://github.com/bigcommerce/stand-with-ukraine-frontend/actions/workflows/main.yml">
    <img alt="" src="https://img.shields.io/github/workflow/status/bigcommerce/stand-with-ukraine-frontend/NodeJS?style=for-the-badge&labelColor=005BBB&logo=nodedotjs&logoColor=white">
  </a>
  <a aria-label="License" href="https://github.com/bigcommerce/stand-with-ukraine-frontend/blob/main/LICENSE.md">
    <img alt="" src="https://img.shields.io/github/license/bigcommerce/stand-with-ukraine-frontend?style=for-the-badge&labelColor=005BBB">
  </a>
  <hr/>
</p>

## Overview

[Stand With Ukraine is a BigCommerce application][app_store_link]. It allows merchants to easily add a widget to their storefront with a customized message and list of Charities that the merchant would like their shoppers to visit and support.

## Repositories

- [Frontend Components][frontend_repo]
- [Backend Components][backend_repo]

## Usage

If you have a BigCommerce store and would like to use the widget - please install it via the [BigCommerce app store][app_store_link].
If you have a website on any other platform - you can use the following html to embed the widget. Feel free to edit the title and body text shown in the modal. You can configure some of the variables by reading the allowed values in [`/packages/config/types.ts`](/packages/config/types.ts).

```html
<script>
  window.SWU_CONFIG = {
    style: 'black',
    placement: 'bottom-right',
    charity_selections: ['razom', 'mira-action', 'new-ukraine'],
    modal_title: 'Help the people of Ukraine!',
    modal_body:
      'With each day, the war in Ukraine worsens at an alarming pace. Millions of civilians have lost their homes and many more are without basic necessities like food, water, and health care. Consider donating to one of the charities below and join us in showing support for Ukraine. All charities are trusted, non-profit organizations dedicated to Ukrainian relief efforts. It takes less than a minute.',
  };
</script>
<script defer src="https://stand-with-ukraine-bc-app.web.app/widget/index.js"></script>
```

## Project Structure

1. Application Dashboard - `apps/dashboard`
   This is the configuration dashboard served to the merchant when they open the app from within the BigCommerce store apps.
   It is responsible for allowing the merchant to install/update/remove the widget from the store.

2. Storefront Widget - `apps/widget`
   The widget that is injected on the storefront. For local development the configuration is fetched from the mock api and stored in `window.SWU_CONFIG`. In production the storefront script will have `SWU_CONFIG` defined directly.

3. Mock Server - `apps/mocks`
   It uses local file system to store state for easy development without needing to run the backend project and database

The shared packages are stored in the `packages` folder.

## Start Local Development

1. Install NodeJS & Yarn - Recommended version NodeJS ~v16 & Yarn ~v1
2. Install Dependencies `yarn install`
3. Start local servers `yarn dev`
   - dashboard available at `http://localhost:3001/dashboard/`
   - widget available at `http://localhost:3002/widget/`
   - api requests are proxied from `/api` routes on widget and dashboard servers to mock api server running at port `9000`

## Helpful Commands:

1. `yarn build` builds all the projects
2. `yarn lint` checks all the projects using tslint
3. `yarn format` auto formats all the project files
4. `yarn clean` clears local dependencies and cache files

## License

Copyright (c) 2017-present, BigCommerce Pty. Ltd. All rights reserved

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated
documentation files (the "Software"), to deal in the Software without restriction, including without limitation the
rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit
persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the
Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE
WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR
OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

[app_store_link]: https://www.bigcommerce.com/apps/stand-with-ukraine/ 'BigCommerce App Store - Stand with Ukraine'
[frontend_repo]: https://github.com/bigcommerce/stand-with-ukraine-frontend
[backend_repo]: https://github.com/bigcommerce/stand-with-ukraine-backend
