# React vs Svelte vs Vue

In this repo, I compare and contrast these three frameworks across a number of metrics, including **build size**, **performance**, integration with **Rollup**, integration with **TypeScript**, and more.

### Table of Contents

1. [Main Package Installation](#main-package-installation)
2. [Initial Entry File Setup](#initial-entry-file-setup)

## Main Package Installation

### React

```sh
npm install react
npm install react-dom
```

Both `react` and `react-dom` are needed to get up and running with an independent React project. The install process is relatively easy, though (negligibly) more complicated than Vue. 

All in all, a little less than ten individual dependencies are installed. This puts React square in the middle between the approaches of Svelte and Vue, where Svelte's opinionated install creates dozens of dependencies to start, and Vue's install only adds a `vue` folder to node_modules.

Once these are installed, React's node_modules folder is 3.8mb.

#### Pros:

- Easy install is about on par with Vue, and arguably more simple than Svelte's install process.

#### Cons:

- Project folder starts off with slightly more dependencies than Vue, but the resulting node_modules folders are 3.8mb and 3.6mb in size, respectively. Not that much difference, but Vue has a tiny advantage here.

### Svelte

The Svelte docs recommend these commands to set up a Svelte project:

```sh
npx degit sveltejs/template svelte-repo
cd svelte-repo
npm install
```

Svelte's approach is opinionated and generates some amount of boilerplate. It's similar to setting up a project with `create-react-app` wherein the project is bootstrapped in no time for the developer. A lot of decisions are handled on the fly, and if we want to alter these previously made decisions, we'll likely have to refactor or completely gut some auto-generated code.

Svelte's documentation suggests using the `degit` package to get set up. While it looks like this will save you time and space, the approach will be unfamiliar at first, and that might be initially off-putting.

Nonetheless, this approach will likely save time for a newcomer to Svelte, and once certain concepts are picked up with this process, some might prefer it over React and Vue.

After install, Svelte's node_modules is 15mb, which is almost five times the size of both React and Vue's dependency weight at this point. This of course is because the Svelte install has already handled build setup and other conveniences for us that we have yet to set up in the React and Vue projects.

Given our lack of choices in setup, and given that our install is pretty weighty to start, Svelte is at a disadvantage to React and Vue here. Svelte has put their money on providing maximum convenience for the developer at the expense of options upfront.

#### Pros

- Opinionated and thorough install will save time getting later steps set up.

#### Cons

- Opinionated install doesn't leave many options, and the user will probably have to delete some boilerplate after the install.
- Unfamiliar install process might be a minor setback to start.
- node_modules is five times the size of React's or Vue's to start.

### Vue

To install Vue:

```sh
npm install vue
```

Vue's initial install is the easiest, the React is pretty much neck-and-neck in this regard. With Vue's install, no external dependencies are added in the process, and the resulting folder size is also the smallest at 3.6mb.

#### Pros

- Easy install.
- No external dependencies to start.
- Lightest main package install.

#### Cons

- N/A

<hr />

#### Points Awarded

- React: +1
- Svelte: 0
- Vue: +2

<hr />

## Initial Entry File Setup

### React

For our folder structure, let's assume a few things:
- that our bundled code will be put into a separate folder called `dist`.

```
- dist
  - index.html
- src
  - index.js
  - components
    - App.js
```

The `index.js` entry point will look like this:

```jsx
import React from 'react';
import { render } from 'react-dom';
imort App from './components/App';

render(<App />, document.getElementById('root'));
```

This will import the top-level `App` component:

```jsx
import React from "react";

const App = () => <div>Hello, World!</div>;

export default App;
```

Once this entry file is compiled, it will be loaded in from an `index.html` file that looks like this:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />

    <title>React Proof of Concept</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="index.js"></script>
  </body>
</html>
```

#### Pros

- Easy to scaffold up a basic, agnostic setup and introduce CSS and build opinions later on.
- JSX is an incredibly powerfully HTML-in-JS syntax.

#### Cons

- slightly more code to get up and running.
- JSX, though powerful, might be a little more challenging for a newcomer to grasp.

### Svelte

I'll set up my entry file inside this folder structure:

```
- public
  - index.html
- src
  - main.js
  - components
    - App.svelte
```

At its simplest, `main.js` entry point for Svelte looks like this:

```js
import App from "./components/App.svelte";

const app = new App({ target: document.body });

export default app;
```

Like the React example, we are loading in our component from a separate file. In Svelte, we will keep the component in a `.svelte` file:

```svelte
<main><h1>Hello, World!</h1></main>
```

After we build our source code, we will load it into an index.html file.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />

    <title>Svelte Proof of Concept</title>

    <script defer src="/build/bundle.js"></script>
  </head>

  <body></body>
</html>
```

#### Pros

- .svelte component files are arguably the easiest for newcomers to read and understand since they look like HTML template files.
- Slightly less code to get up and running.

#### Cons

- Requires build and css modification to the Svelte template to achieve the stripped-down, unopinionated setup above.

### Vue
