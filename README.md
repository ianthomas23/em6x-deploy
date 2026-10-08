JupyterLite deployment with `emscripten-wasm32` and `emscripten-wasm64` kernels.

To build locally:

```bash
micromamba create -f build-environment.yml
micromamba activate em6x-deploy

micromamba create -f environment.yml --platform=emscripten-wasm32 -p ./wasm32 --yes
micromamba create -f environment.yml --platform=emscripten-wasm64 -p ./wasm64 --yes
jupyter lite build --contents contents --output-dir dist \
    --XeusAddon.prefix=./wasm32 \
    --XeusAddon.prefix=./wasm64 \
    --XeusAddon.default_channels=https://prefix.dev/emscripten-forge-bot/emscripten-forge-6x,https://repo.prefix.dev/conda-forge
```

To serve locally:

```bash
npx static-handler dist
```
