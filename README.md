Create the SvelteKit Template
=============================

Initial Setup
-------------

```bash
$ npm create svelte@latest template

create-svelte version 2.0.0-next.192

Welcome to SvelteKit!

This is release candidate software; expect bugs and missing features.

Problems? Open an issue on https://github.com/sveltejs/kit/issues if none exists already.

√ Which Svelte app template? » Skeleton project
√ Add type checking with TypeScript? » No
√ Add ESLint for code linting? ... No
√ Add Prettier for code formatting? ... No
√ Add Playwright for browser testing? ... No

Your project is ready!

$ cd template
$ npm install

added 44 packages, and audited 45 packages in 28s
```

Change the file `src/routes/+page.svelte` to:

```svelte
<h1>A SvelteKit Template</h1>
```

```bash
$ git init && git add -A && git commit -m "initial commit"
Initialized empty Git repository in C:/Users/johnd/sveltekit/blog/.git/

$ npm run dev -- --open

```

You should see your web page, displaying 'A SvelteKit Template'.

Deploy to the Internet
----------------------

Install the SvelteKit "static adapter":

```bash
$ npm install -D @sveltejs/adapter-static@next
```

In `svelte.config.js`, change 'adapter-auto' to 'adapter-static'

Create the file `routes/+layout.js`:

```js
export const prerender = true
```

```bash
$ npm run build
$ npm run preview -- --open
```

As before, you should see your web site. But this time, it's being served
from the file `index.html` which was placed inside a folder named `build`.
You can now deploy that to surge:

```bash
$ surge ./build
```

When surge suggests a domain name, you can edit that. Just make sure it ends
in `.surge.sh` and if you want to ensure that the name isn't already being
used, try starting with name with your initials followed by a '-' character.

You should now be able to access the site directly.

Next, add a new script in your `package.json` file:

```js
"deploy": "npm run build && surge ./build --domain https://<domain>"
```

Substituting your selected domain name for `<domain>`.

