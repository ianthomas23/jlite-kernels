Example JupyterLite deployment with kernels.

To deploy locally:

```bash
micromamba create -f build-environment.yml
micromamba activate jlite-kernels
jupyter lite build --contents contents --output-dir dist
npx static-handler dist/
```
