
# rinterface-shinylive

<!-- badges: start -->
<!-- badges: end -->

Customized version of [shinylive](https://github.com/posit-dev/shinylive) for [RinteRface](https://rinterface.com) packages. Hosted at https://shinylive.rinterface.com.

The purpose is to reuse it in multiple projects as a boilerplate. As an example, one can seamlessly create the app code via the editor, share the URL and insert an iframe in another location to embed the editor.

## Notes

Few things have been changed:

- `./shinylive/webr` points to `https://webr-cran.rinterface.com` in `./shinylive/webr/webR/config.d.ts` so we can use the RinteRface wasm CRAN for pulling specific packages like `{bs4Dash}`. Currently the issue is that `webR` is pulled from npm in the shinylive repository so we have no control over the sources.

- 2 functions for sharing code are modified. We removed `${shortEngine[engine]}` from `./shinylive/chunk-....js` (see `https://github.com/posit-dev/shinylive/blob/main/src/Components/share.ts`) since we don't need to switch between Python and R:

```js
function editorUrlPrefix(engine) {
  return `https://shinylive.rinterface.com/editor/`;
}
function appUrlPrefix(engine) {
  return `https://shinylive.rinterface.com/app/`;
}
```
- `app` and `editor` are necessary for the code __sharing__ feature. Don't remove them.

- We don't have an `example` folder showcasing multiple apps.

- The `test folder` contains a toy app which was prepared by the R `{shinylive}` [package](https://posit-dev.github.io/r-shinylive/#usage) so we can just copy the `app.json` to the website root.
