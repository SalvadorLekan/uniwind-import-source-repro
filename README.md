# Uniwind: `@import "tailwindcss" source(...)` fails the build

Based on [`apps/vite-example`](https://github.com/uni-stack/uniwind/tree/main/apps/vite-example). The only change is the first line of `src/App.css`:

```css
@import 'tailwindcss' source('./');
```

## Steps

```sh
bun install
bun run build
```

## Result

```
[plugin uniwind]
SyntaxError: Unexpected token Function("source")
    at findVariantsRec (node_modules/uniwind/dist/shared/uniwind.DwDkVVSf.mjs:255:30)
    at generateCSSForThemes (node_modules/uniwind/dist/shared/uniwind.DwDkVVSf.mjs:303:9)
    at buildCSS (node_modules/uniwind/dist/shared/uniwind.DwDkVVSf.mjs:363:27)
```

`prefix(tw)` and `theme(static)` fail the same way. Removing `uniwind()` from `vite.config.ts` and `@import 'uniwind'` from `src/App.css` makes the same `@import` build.
