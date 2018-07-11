# typescript-duplicate-amd-module-name-issue
Minimal repo for reproducing issue with duplicate amd-module name declarations being emitted. See https://github.com/Microsoft/TypeScript/issues/25588

### Reproduction Steps:
1. npm install
2. tsc -p tsconifg.json

### Issue:
build/index.d.ts file is generated and has the below in the first two lines
```
/// <amd-module name="mynamespace::SomeModule" />
/// <amd-module name="mynamespace::SomeModule" />
```
along with the error
> an AMD module cannot have multiple name assignments

### Workaround:
We can manually delete the duplicate line

### Expected Behavior:
The duplicate line shouldn't be generated in the first place
