## Broken biome ci

`biome ci` always fails the job in GHA when running the exact same command does not produce any error locally.

### Actual result

Running `biome ci` in GHA will always produce errors even when the formatter logs `Checked 2 files in 1572µs. No fixes needed.`. However, running `biome ci` locally does not see any errors.

```sh
> biome ci
 format ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✖ File content differs from formatting output
  
     3  3 │     "version": "0.0.1",
     4  4 │     "description": "Broken biome ci",
     5    │ - ··"keywords":·[
     6    │ - ····"biome",
     7    │ - ····"ci",
     8    │ - ····"biome-ci",
     9    │ - ····"broken-biome-ci"
    10    │ - ··],
        5 │ + ··"keywords":·["biome",·"ci",·"biome-ci",·"broken-biome-ci"],
    11  6 │     "homepage": "https://github.com/motss/broken-biome-ci",
    12  7 │     "bugs": {
    ····· │ 
    35 [30](https://github.com/ipohjs/broken-biome-ci/actions/runs/9438349120/job/25995224343#step:9:31) │     "module": "./index.js",
    36 [31](https://github.com/ipohjs/broken-biome-ci/actions/runs/9438349120/job/25995224343#step:9:32) │     "types": "./index.js",
    37    │ - ··"files":·[
    38    │ - ····"./index.d.ts",
    39    │ - ····"./index.js"
    40    │ - ··],
    41    │ - ··"workspaces":·[
    42    │ - ····"./packages/*"
    43    │ - ··],
       [32](https://github.com/ipohjs/broken-biome-ci/actions/runs/9438349120/job/25995224343#step:9:33) │ + ··"files":·["./index.d.ts",·"./index.js"],
       [33](https://github.com/ipohjs/broken-biome-ci/actions/runs/9438349120/job/25995224343#step:9:34) │ + ··"workspaces":·["./packages/*"],
    44 [34](https://github.com/ipohjs/broken-biome-ci/actions/runs/9438349120/job/25995224343#step:9:35) │     "scripts": {
    45 [35](https://github.com/ipohjs/broken-biome-ci/actions/runs/9438349120/job/25995224343#step:9:36) │       "biome.ci": "biome ci",
  

ci ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✖ Some errors were emitted while running checks.
  

Checked 2 files in 1572µs. No fixes needed.
Found 1 error.
 ELIFECYCLE  Command failed with exit code 1.
Error: Process completed with exit code 1.
```

### Expected result

Running `biome ci` locally and in GHA should always produce identical and consistent result.

```sh
> biome ci

Checked 2 files in 969µs. No fixes needed.
```
