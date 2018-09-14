Installing dependencies of a project with a relative dependency fails when that dependency has a dependency on `@babel/preset-env`.

To reproduce:

1. Clone this repository
1. `cd project-b`
1. `npm i`

```
npm ERR! path ***/npm-test/project-b/node_modules/.staging/project-a-4f96b5b4/node_modules/@babel/core
npm ERR! code ENOENT
npm ERR! errno -2
npm ERR! syscall rename
npm ERR! enoent ENOENT: no such file or directory, rename '***/npm-test/project-b/node_modules/.staging/project-a-4f96b5b4/node_modules/@babel/core' -> '***/npm-test/project-b/node_modules/.staging/@babel/core-a61c6f88'
npm ERR! enoent This is related to npm not being able to find a file.

```

Deleting `project-b/package-lock.json` allows `npm i` to succeed.
Deleting `project-b/node_modules` makes `npm i` fail again.
