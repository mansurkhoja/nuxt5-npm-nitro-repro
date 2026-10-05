# Nuxt 5 build fails with npm because of nitro@3.0.0

An empty Nuxt 5 project (`nuxt-nightly@5x`). Tested with `nuxt-nightly` 5.0.0-29852495.9beb9427, `@nuxt/devtools` 4.0.0-beta.3, npm 11.13.0, Node 24.16.0.

```sh
npm install
npm run build
```

The build fails:

```
"./app" is not exported under the conditions ["production", "wasm", "unwasm", "node", "import"] from package node_modules/nitro
```

(The missing subpath is sometimes `./storage`.)

`npm explain nitro` shows `nitro@3.0.0` at the top of `node_modules`, linked only to the optional peer `nitro@"^3.0.0-0"` of `@nuxt/devtools` and `@nuxt/devtools-kit`. The version that `@nuxt/nitro-server` needs (`^3.0.260903-beta`) is nested under `node_modules/@nuxt/nitro-server`.

With pnpm the same project builds.
