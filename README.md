# React vs Svelte vs Vue
In this repo, I compare and contrast these three frameworks across a number of metrics, including **build size**, **performance**, integration with **Rollup**, integration with **TypeScript**, and more.

### Table of Contents
- [Main Package Installation](#main-package-installation)
- [Initial Entry File Setup](#initial-entry-file-setup)


## Main Package Installation

### React

```sh
npm install react
npm install react-dom
```

I need both `react` and `react-dom` to get up and running with React. So, the install process is relatively easy, though slightly more complicated than Vue, and the resulting folder size is slightly larger than Vue.

**Folder size so far: 3.8mb**

#### Pros:
- Relatively easy install
#### Cons:
- Starts off with a few external packages

### Svelte

```sh
npx degit sveltejs/template svelte-repo
cd svelte-repo
npm install
```
Svelte really only offers one recommended way to install, and it's an opinionated approach that generates some amount of boilerplate. It's a minor complaint, but I'd ideally want to have a more bare metal approach when initializing the repo.

Svelte's documentation suggests using the `degit` package to get set up. While it looks like this will save you time and space, the approach will be unfamiliar at first, and that might be initially off-putting.

Nonetheless, this approach will likely save time when getting through the next several steps for the repo, so it sets Svelte back a bit in this phase of development, but will likely earn it points in future steps.

**Folder size so far: 15mb**

#### Pros
- Opinionated and thorough install will probably save time getting later steps set up
#### Cons
- Opinionated install
- Unfamiliar install process might be a minor setback to start
- Will probably have to delete some boilerplate after the install
- Folder size is the heaviest after initial install
- Starts off with lots of external dependencies

### Vue

```sh
npm install vue
```

Vue's initial install is the easiest. No external dependencies are added in the process, and the resulting folder size is also the smallest.

**Folder size so far: 3.6mb**

#### Pros
- Easy install
- No external dependencies to start.
- Lightest main package install.

#### Cons
- N/A

<hr />

#### Points Awarded
- React: +1
- Svelte: 0
- Vue: +2

#### Total So Far
- React: 1
- Svelte: 0
- Vue: 2

<hr />

## Initial Entry File Setup

### React

### Svelte

### Vue