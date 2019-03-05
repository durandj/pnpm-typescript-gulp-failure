# Minimum Reproduction

This is a minimum reproduction of an issue that pops up when using
`pnpm` with a project that uses `gulp` and `Typescript`. If you use
`Typescript` to write your `gulpfile` and use certain features from
`gulp` 4.x (such as `series` and `parallel`), `ts-node` throws
exceptions about missing type definitions.

```
> pnpm-typescript-gulp-failure@1.0.0 tasks $HOME/workspace/pnpm-typescript-gulp-failure
> gulp

[06:12:58] Requiring external module ts-node/register

$HOME/workspace/pnpm-typescript-gulp-failure/node_modules/.registry.npmjs.org/ts-node/8.0.2/node_modules/ts-node/src/index.ts:228
    return new TSError(diagnosticText, diagnosticCodes)
           ^
TSError: ⨯ Unable to compile TypeScript:
gulpfile.ts/index.ts(1,10): error TS2305: Module '"../node_modules/@types/gulp"' has no exported member 'series'.

    at createTSError ($HOME/workspace/pnpm-typescript-gulp-failure/node_modules/.registry.npmjs.org/ts-node/8.0.2/node_modules/ts-node/src/index.ts:228:12)
    at getOutput ($HOME/workspace/pnpm-typescript-gulp-failure/node_modules/.registry.npmjs.org/ts-node/8.0.2/node_modules/ts-node/src/index.ts:334:40)
    at Object.compile ($HOME/workspace/pnpm-typescript-gulp-failure/node_modules/.registry.npmjs.org/ts-node/8.0.2/node_modules/ts-node/src/index.ts:367:11)
    at Module.m._compile ($HOME/workspace/pnpm-typescript-gulp-failure/node_modules/.registry.npmjs.org/ts-node/8.0.2/node_modules/ts-node/src/index.ts:413:43)
    at Module._extensions..js (internal/modules/cjs/loader.js:745:10)
    at Object.require.extensions.(anonymous function) [as .ts] ($HOME/workspace/pnpm-typescript-gulp-failure/node_modules/.registry.npmjs.org/ts-node/8.0.2/node_modules/ts-node/src/index.ts:416:12)
    at Module.load (internal/modules/cjs/loader.js:626:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:566:12)
    at Function.Module._load (internal/modules/cjs/loader.js:558:3)
    at Module.require (internal/modules/cjs/loader.js:663:17)
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! pnpm-typescript-gulp-failure@1.0.0 tasks: `gulp`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the pnpm-typescript-gulp-failure@1.0.0 tasks script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.

npm ERR! A complete log of this run can be found in:
npm ERR!     $HOME/.npm/_logs/2019-03-05T12_12_59_337Z-debug.log
```
