# React vs Svelte vs Vue
In this repo, I compare and contrast these three frameworks across a number of metrics, including **build size**, **performance**, integration with **Rollup**, integration with **TypeScript**, and more.

## Main Package Installation

### React

```sh
npm install react
```
Even with just the one install so far, we've created dependencies on several external packages, and our total package count is 6.

Nonetheless, the folder size is actually pretty light with just the main package so far, making the React repo the only one of the three that's under a megabyte in size.

**Folder size so far: 500kb**

#### Pros:
- Easy install
- Small folder size to start
#### Cons:
- Starts off with lots of external packages
### Svelte

```sh
npx degit sveltejs/template svelte-repo
cd svelte-repo
npm install
```
The script is an opinionated approach that generates some amount of boilerplate. It's a minor complaint, but I'd ideally want to not generate any fluff when starting a project.

Svelte's documentation suggests using the `degit` package to get set up. While it looks like this will save you time and space, the approach will be unfamiliar at first, and that might be initially off-putting.

**Folder size so far: 15mb**

#### Pros
- Opinionated and thorough install will probably save us time getting later steps set up
#### Cons
- Opinionated install
- Unfamiliar install process might be a minor setback to start
- Will probably have to delete some boilerplate after the install
- Folder size is the heaviest after initial install
### Vue

```sh
npm install vue
```

**Folder size so far: 3.6mb**

#### Pros
- Easy install
- No external dependencies to start.

#### Cons
- Not the lightest main package install.

<hr />

#### Points Awarded
- React: +1 / 1 total
- Svelte: 0 / 0 total
- Vue: +1   / 1 total