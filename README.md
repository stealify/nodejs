# nodejs
Stealify NodeJS - Tools and Modules that will help you to create software that uses the NodeJS Ecosystem.

## What is NodeJS?
It is a c++ RUNTIME Environment for ECMAScript and WASM code using user i/o as main loop (libuv)

## Why use it?
It has a big collection of prebuild functionality and enables fast prototyping.
It has a hugh collection of Modules (ecosystem)

## Alternatives
- deno (rust written) runtime using c++ v8
- chromium headless (got a nodejs api pupeteer it also ships the correct chromium version for the api)
- v8 embedder framework (just-js)
- graaljs and graal-node
- teavm https://blogs.oracle.com/javamagazine/post/java-in-the-browser-with-teavm


## How to build a custom NodeJS Version

### Modify the Source 
This method is not worth the effort as the goal of nodejs is prototyping anyway there are less scenarios where you would want to create a own nodejs
version via source code modification and forking but valid cases are there for example engine implementers

### Create a custom binary
This will build NodeJS with all changes to globalThis Persistet in a single binary use cases are mocking for core api's for example adding 
ECMAScript features or standard tools as also shiming core modules like fs for security reasons.

```shell
$ cd /path/to/node/source

# Specifying an entry point of the snapshot, for example,
# a UMD module like the marked markdown renderer which in
# this case should initialize the renderer and stores in
# globalThis.
$ ./configure --node-snapshot-main=marked.js

# Build the binary
$ make node
```

this binary needs packaging. to get a single binary see: https://nodejs.org/en/blog/announcements/v18-release-announce/#build-time-user-land-snapshot-experimental

for methods to package the  binary use the 7zip executer merge the file with the resulted node binary google about the topic i have at present no time to write that kind of tutorials.
