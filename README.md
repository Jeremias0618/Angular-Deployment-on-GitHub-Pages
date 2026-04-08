# Angular deployment on GitHub Pages

[![Angular](https://img.shields.io/badge/Angular-21-DD0031?logo=angular&logoColor=white)](https://angular.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![RxJS](https://img.shields.io/badge/RxJS-7.8-B7178C?logo=reactivex&logoColor=white)](https://rxjs.dev/)
[![Vitest](https://img.shields.io/badge/Vitest-4-6E9F18?logo=vitest&logoColor=white)](https://vitest.dev/)
[![Prettier](https://img.shields.io/badge/Prettier-3-1A2C34?logo=prettier&logoColor=white)](https://prettier.io/)
[![npm](https://img.shields.io/badge/npm-10-CB3837?logo=npm&logoColor=white)](https://www.npmjs.com/)

![Visitors](https://visitor-badge.laobi.icu/badge?page_id=Jeremias0618.Angular-Deployment-on-GitHub-Pages)

Sample [Angular](https://angular.dev/) application set up for **static hosting on [GitHub Pages](https://pages.github.com/)**, with the correct `base-href` for project sites (for example `https://username.github.io/repository-name/`).

| Resource    | Link |
| ----------- | ---- |
| **Repository** | [github.com/Jeremias0618/Angular-Deployment-on-GitHub-Pages](https://github.com/Jeremias0618/Angular-Deployment-on-GitHub-Pages) |
| **Live site**  | [jeremias0618.github.io/Angular-Deployment-on-GitHub-Pages](https://jeremias0618.github.io/Angular-Deployment-on-GitHub-Pages/) |

> [!NOTE]
> The npm package name is `cybercodelabs` (Angular project id). The GitHub repository name is `Angular-Deployment-on-GitHub-Pages`, which defines the Pages URL path and the production `base-href`.

> [!IMPORTANT]
> GitHub Pages serves **static files only**. This repo includes Angular **SSR** tooling for local or Node hosting; for Pages you deploy the **browser** bundle under `dist/cybercodelabs/browser` (see [Deployment](#deployment)).

## Tech stack

| Area | Technology | Role |
| ---- | ---------- | ---- |
| Framework | **Angular 21** | SPA, routing, forms |
| Language | **TypeScript ~5.9** | Application code |
| Styling | **SCSS** | Component and global styles |
| Reactive streams | **RxJS ~7.8** | Async/event handling |
| SSR (optional) | **@angular/ssr**, **Express 5** | Server-side rendering when not using static Pages |
| Build / CLI | **Angular CLI**, **@angular/build** | `ng serve`, `ng build`, unit tests |
| Unit tests | **Vitest** (via `ng test`) | Component and unit tests |
| Tooling | **Prettier** | Code formatting |
| Deploy | **gh-pages** | Publishes static output to the `gh-pages` branch |

## Prerequisites

- [Node.js](https://nodejs.org/) (LTS recommended; aligns with `@types/node` in the project)
- [npm](https://www.npmjs.com/) 10.x (see `packageManager` in `package.json`)

## Getting started

```bash
git clone https://github.com/Jeremias0618/Angular-Deployment-on-GitHub-Pages.git
cd Angular-Deployment-on-GitHub-Pages
npm install
```

### Development server

```bash
npm start
# or: ng serve
```

Open [http://localhost:4200/](http://localhost:4200/). The app reloads when you change source files.

### Production build

```bash
npm run build
# or: ng build
```

Artifacts are written to `dist/cybercodelabs/` (browser assets under `dist/cybercodelabs/browser/`).

### Tests

```bash
npm test
# or: ng test
```

## Deployment

### 1. `base-href`

For a **project site** at `https://jeremias0618.github.io/Angular-Deployment-on-GitHub-Pages/`, the base href must be:

`/Angular-Deployment-on-GitHub-Pages/`

The `deploy` script passes this to `ng build`.

### 2. Publish with `gh-pages`

```bash
npm run deploy
```

This runs a production build and pushes the **browser** folder to the `gh-pages` branch (via [gh-pages](https://github.com/tschaub/gh-pages)).

### 3. Enable GitHub Pages

In the repository on GitHub: **Settings → Pages → Build and deployment** — set the source to the **`gh-pages`** branch (root).

> [!TIP]
> If you rename the repository, update both the **`base-href`** in the deploy command and the **live site** / **visitor badge** `page_id` in this README.

## Project layout (high level)

| Path | Purpose |
| ---- | ------- |
| `src/` | Application source (components, routes, styles) |
| `public/` | Static assets copied into the build |
| `angular.json` | Workspace and build configuration |
| `tsconfig*.json` | TypeScript compiler options |

## Scripts (`package.json`)

| Script | Description |
| ------ | ----------- |
| `start` | Dev server (`ng serve`) |
| `build` | Production build |
| `watch` | Development build in watch mode |
| `test` | Unit tests (`ng test`) |
| `deploy` | Production build with GitHub Pages `base-href` + `gh-pages` publish |

## Additional resources

- [Angular documentation](https://angular.dev/)
- [Angular CLI reference](https://angular.dev/tools/cli)
- [GitHub Pages documentation](https://docs.github.com/pages)
