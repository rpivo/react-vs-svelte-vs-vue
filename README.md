# React vs Svelte vs Vue
In this repo, I compare and contrast these three frameworks across a number of metrics, including **build size**, **performance**, integration with **Rollup**, integration with **TypeScript**, and more.

## Installation

### React

```sh
npm install react
```
Even with just the one install so far, we've created dependencies on several external packages, and our total package count is 6.

At 500kb after install, this folder is not the heaviest of the 3, but it's still **11 times the size of the Svelte install**.

#### Pros:
- Easy install

#### Cons:
- 11 times the size of the Svelte install

### Svelte

```sh
npx degit sveltejs/template svelte-repo
cd svelte-repo
npm install
```
After running the install script, the folder size is just 45kb, making it the lightest install of the three.

The script is an opinionated approach that generates some amount of boilerplate. It's a minor complaint, but I'd ideally want to not generate any fluff when starting a project.

Svelte's documentation suggests using the `degit` package to get set up. While it looks like this will save you time and space, the approach will be unfamiliar at first, and that might be initially off-putting. 

#### Pros
- Incredibly light install size
- No external dependencies
- 
#### Cons
- Opinionated install
- Unfamiliar install process might be a minor setback to start

### Vue

```sh
npm install vue
```
After install, this folder is by far the heaviest, sitting at 3.6mb.

#### Pros
- Easy install
- No external dependencies to start.

#### Cons