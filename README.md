# Hello Wagi for the Grain Language

[Grain](https://grain-lang.org) is a new programming language that targets WebAssembly.

This repository provides a simple module that works with [Wagi](https://github.com/deislabs/wagi).
It illustrates how easy it is to write HTTP responders with Grain and Wagi.

This version is built on Grain 0.3, and relies on Grain 0.3's static compiler.
Grain is a rapidly evolving language, and this code may not work on other versions of Grain.

## Building

There is already a `hello.gr.wasm` binary checked in.
To build from source, [install Grain]()
and then use this command to compile:

```console
$ grain compile hello.gr
```

You can test your program with `grain` or `wasmtime`:

```console
$ wasmtime hello.gr.wasm --env USER=mbutcher hello
==== Environment: ====
USER=mbutcher
==== Args: ====
hello.gr.wasm
hello
```

When deploying to Wagi, you will want to add an entry like this in WAGI's route TOML:

```toml
[[module]]
route = "/hello-grain"
module = "/path/to/hello-wagi-grain/hello.gr.wasm"

```

After reloading or restarting Wagi, you can execute this module:

```
$ curl http://localhost:3000/hello-grain
```
