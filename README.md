# React vs Svelte vs Vue
In this repo, I compare and contrast these three frameworks across a number of metrics, including **build size**, **performance**, integration with **Rollup**, integration with **TypeScript**, and more.

## Installation

### React

```sh
npm install react
```

#### Pros:

#### Cons:
Even with just the one install so far, we've created dependencies on several external packages, and our total package count is 6.

At 500kb after install, this folder is not the heaviest of the 3, but it's still **11 times the size of the Svelte install**.

### Svelte

```sh
npx degit sveltejs/template svelte
```

#### Pros
After running the install script, the folder size is just 45kb, making it the lightest install of the three.
#### Cons
The script is an opinionated approach that generates some amount of boilerplate. It's a minor complaint, but I'd ideally want to not generate any fluff when starting a project.

### Vue

```sh
npm install vue
```

#### Pros

#### Cons
After install, this folder is by far the heaviest, sitting at 3.6mb.