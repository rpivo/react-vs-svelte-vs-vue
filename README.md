# React vs Svelte vs Vue

In this repo, I compare and contrast these three frameworks across a number of metrics, including **build size**, **performance**, integration with **Rollup**, integration with **TypeScript**, and more.

### Table of Contents

1. [Main Package Installation](#main-package-installation)
2. [Initial Entry File Setup](#initial-entry-file-setup)

## Main Package Installation

In this section, I look at the minimum necessary steps to install each framework's main proprietary packages. The framework will mostly be unusable at this point until more build tools are introduced.

### React

```sh
npm install react
npm install react-dom
```

Both `react` and `react-dom` are needed to get up and running with an independent React project. The install process is relatively easy, though slightly more complicated than Svelte and Vue in that two packages have to be installed rather than one (not much to complain about, but worth mentioning).

In a way, though, the separation of `react` and `react-dom` shows one of the strong suits of the React ecosystem -- every piece of the toolchain is opt-in and not mandatory. React really has tried to build something that decouples all the pieces, allowing you to control how opinionated it is.

Three non-React dependencies are also installed in the process. React's approach differs from Svelte and Vue -- Svelte's install adds a single `svelte` folder to node_modules, and Vue's install adds a single `vue` folder to node_modules.

React, on the other hand, has these three external dependencies: **js-tokens**, **loose-envify**, and **object-assign**.
  - js-tokens is a tokenizer. [nearley.js'](https://nearley.js.org/docs/tokenizers#:~:text=A%20tokenizer%20splits%20the%20input,of%20larger%20units%20called%20tokens.&text=For%20example%2C%20a%20tokenizer%20can,line%20numbers%20for%20each%20token.) documentation explains what a tokenizer does:

    > A tokenizer splits the input into a stream of larger units called tokens. This happens in a separate stage before parsing. For example, a tokenizer might convert 512 + 10 into ["512", "+", "10"]: notice how it removed the whitespace, and combined multi-digit numbers into a single number.

    js-tokens is a dependency of loose-envify.
  - loose-envify helps convert Node environment variables to strings.
  - object-assign is a polyfill for `Object.assign()`.

The footprint of these external dependencies is relatively small, totalling 78kb out of the full 3.8mb after installing `react` and `react-dom`, so their inclusion doesn't negatively affect the weight of the node_modules folder.

You could argue that React's use of these packages makes it less "monolothic" and more community-driven than the other two frameworks. None of these frameworks would be here without their communities, but it's a small detail that could be meaningful to you, especially given that React is in part backed by a company like Facebook.

On the other hand, you could also say that the "monolothic" installs of Vue and Svelte contain only proprietary code that was written specifically for their respective ecosystems. I've decided to leave these details out of the pros and cons because it really is subjective.

The biggest item of all installed packages is `react-dom`, coming out to 3.1mb, or roughly 82% of the total size of the node_modules folder.

#### Pros:

- node_modules is slightly smaller than Svelte's: 3.8mb vs 3.9mb.
- Separation of `react` and `react-dom` illustrates React's commitment to an opt-in, unopinionated ecosystem.

#### Cons:

- node_modules is slightly bigger than Vue's: 3.8mb vs 3.6mb.
- You need to install two packages rather than one.

### Svelte

To install svelte, we need the `svelte` package.

```sh
npm install svelte
```

Svelte's node_modules install size is the largest out of the three frameworks, sitting at 3.9mb. Svelte is similar to Vue in that all installed dependencies are proprietary Svelte packages.

#### Pros

- Easier to install than React.

#### Cons

- Slightly larger node_modules than both React and Vue: 3.9mb vs React's 3.8mb and Vue's 3.6mb.

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

For each of these framework POCs, let's assume a few things:
- that our bundled code will be put into a separate folder called `dist`.
- that our bundled code will be pulled in with a single `<script>` tag from a standard **index.html** file.
- that we'll keep our source code in a folder called `src`.
- that our source code will have a standard entry file (`index` or `main`).
- that our source code will have a main `App` component through which all other components are children.

### React

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
