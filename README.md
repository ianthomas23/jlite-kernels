Example JupyterLite deployment with `pyodide` and `xeus-cpp`, `xeus-python` and `xeus-r` kernels.

Deployment available on github pages at https://ianthomas23.github.io/jlite-kernels.

To deploy locally:

```bash
micromamba create -f build-environment.yml
micromamba activate jlite-kernels
jupyter lite build --contents contents --output-dir dist
npx static-handler dist/
```

Running without cross-origin headers (using `npx static-handler dist/`) will use the
service worker for `stdin` requests. This can be confirmed from the Network tab in the
browser's dev tools which will show an `xhr` request to `/api/stdin/kernel` for each
`stdin` request.

Alternatively use SharedArrayBuffer for `stdin` requests by serving with
```bash
npx static-handler --cors --coop --coep --corp dist/
```
and there will be no `xhr` requests in the Network tab.
