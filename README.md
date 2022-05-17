# vite-project

This demonstrates an issue when using vite with yarn pnp.

To reproduce, run `yarn` and then `yarn storybook`. In the console of the browser tab that opens, you should see an error like:

```
Uncaught TypeError: Cannot read properties of undefined (reading 'custom')
    at .yarn/cache/object-inspect-npm-1.12.0-d064fa559a-2b36d4001a.zip/node_modules/object-inspect/index.js (index.js:68:21)
    at __require2 (chunk-3XETP6YP.js?v=42383cef:47:50)
    at .yarn/cache/side-channel-npm-1.0.4-e1f38b9e06-351e41b947.zip/node_modules/side-channel/index.js (index.js:5:15)
    at __require2 (chunk-3XETP6YP.js?v=42383cef:47:50)
    at .yarn/cache/qs-npm-6.10.3-172e1a3fb7-0fac5e6c71.zip/node_modules/qs/lib/stringify.js (stringify.js:3:22)
    at __require2 (chunk-3XETP6YP.js?v=42383cef:47:50)
    at .yarn/cache/qs-npm-6.10.3-172e1a3fb7-0fac5e6c71.zip/node_modules/qs/lib/index.js (index.js:3:17)
    at __require2 (chunk-3XETP6YP.js?v=42383cef:47:50)
    at UrlStore.js:30:16
```

This is similar to https://github.com/vitejs/vite/issues/2598.

Note that when using `nodeLinker: node-modules` or `pnpMode: loose` in `.yarnrc.yml`, the error does not appear (be sure to delete `.pnp.cjs` and run `yarn install` after changing the option).
