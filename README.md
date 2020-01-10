# ts-node TS_NODE_COMPILER_OPTIONS Bug

This demo reproduces an issue where ts-node v8.6.0 no longer respects the TS_NODE_COMPILER_OPTIONS environment variable.

## Steps

1. `npm ci`
2. `npm test`

You should get an error related to ES Modules (the exact error message differs based on your Node version). This is because the included tsconfig.json specifies `"module": "esnext"`. TS_NODE_COMPILER_OPTIONS is set to override tsconfig.json with `"module": "commonjs"`.

You can confirm that v8.5.4 works by running the following:

1. `npm i ts-node@8.5.4`
2. `npm test`

You should see `3` in the output, indicating the code was correctly run.
