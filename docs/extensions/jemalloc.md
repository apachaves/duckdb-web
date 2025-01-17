---
layout: docu
title: jemalloc Extension
github_directory: https://github.com/duckdb/duckdb/tree/main/extension/jemalloc
---

The `jemalloc` extension replaces the system's memory allocator with [jemalloc](https://jemalloc.net/).
Unlike other DuckDB extensions, the `jemalloc` extension is statically linked and cannot be installed or loaded during runtime.

## Operating System Support

The availability of the `jemalloc` extension depends on the operating system.

### Linux

On Linux, the AMD64 (x86_64) distribution of DuckDB ships with the `jemalloc` extension.
To disable the `jemalloc` extension, [build DuckDB from source]({% link docs/dev/building/build_instructions.md %}) and set the `SKIP_EXTENSIONS` flag as follows:

```bash
GEN=ninja SKIP_EXTENSIONS="jemalloc" make
```

The ARM64 (AArch64) DuckDB distribution on Linux does not ship with the `jemalloc` extension.
To include it, build it as follows;

```bash
GEN=ninja BUILD_JEMALLOC=1 make
```

### macOS

The macOS version of DuckDB does not ship with the `jemalloc` extension but can be [built from source]({% link docs/dev/building/build_instructions.md %}) to include it:

```bash
GEN=ninja BUILD_JEMALLOC=1 make
```

### Windows

On Windows, this extension is not available.

## Configuration Flags

By default, jemalloc's background threads are disabled. To enable them, use the following configuration option:

```sql
SET allocator_background_threads = true;
```
