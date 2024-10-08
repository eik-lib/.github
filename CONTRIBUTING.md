# Contributing

Thank you for showing an interest in contributing to Eik 🧡

Eik is divided in a collection of modules, each in their separate repositories. The contribution process is the same for all of them.

Below is a map of the dependencies between Eik modules. Development dependencies are not shown.

```mermaid
flowchart TD
    COMMON[@eik/common]
    CLI[@eik/cli]
    NODECLIENT[@eik/node-client]
    SINK[@eik/sink]
    SINKFS[@eik/sink-file-system]
    SINKGCS[@eik/sink-gcs]
    SINKMEM[@eik/sink-memory]
    CORE[@eik/core]
    SVC[@eik/service]

    CLI --> COMMON
    NODECLIENT --> COMMON

    SINK --> COMMON
    SINKFS --> COMMON
    SINKFS --> SINK
    SINKGCS --> COMMON
    SINKGCS --> SINK
    SINKMEM --> COMMON
    SINKMEM --> SINK

    CORE --> COMMON
    CORE --> SINK
    CORE --> SINKFS
    CORE --> SINKMEM

    SVC --> CORE
    SVC --> SINK
    SVC --> SINKFS
    SVC --> SINKMEM
```

A short description of the different modules.

| Name                                                                   | Description                                                                                                                                                                                                                                                     |
| ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`@eik/service`](https://github.com/eik-lib/service)                   | The [HTTP server](https://eik.dev/docs/server/) running the Eik service.                                                                                                                                                                                        |
| [`@eik/core`](https://github.com/eik-lib/core)                         | The implementation of the different [HTTP API](https://eik.dev/docs/server/http-api) endpoint handlers.                                                                                                                                                         |
| [`@eik/sink`](https://github.com/eik-lib/sink)                         | Interface implemented by the different [storage sinks](https://eik.dev/docs/server/storage).                                                                                                                                                                    |
| [`@eik/sink-file-system`](https://github.com/eik-lib/sink-file-system) | Storage sink using the local file system.                                                                                                                                                                                                                       |
| [`@eik/sink-gcs`](https://github.com/eik-lib/sink-gcs)                 | Storage sink for [Google Cloud Storage](https://cloud.google.com/storage/).                                                                                                                                                                                     |
| [`@eik/sink-memory`](https://github.com/eik-lib/sink-memory)           | In memory storage sink, useful for automated tests.                                                                                                                                                                                                             |
| [`@eik/node-client`](https://github.com/eik-lib/node-client)           | Utility for [linking to files on Eik](https://eik.dev/docs/introduction/workflow#linking-to-your-assets-from-html) or localhost based on environment, and to do [browser import mapping](https://eik.dev/docs/guides/browser-importmap#download-maps-from-eik). |
| [`@eik/cli`](https://github.com/eik-lib/cli)                           | Command line interface to [publish packages](https://eik.dev/docs/introduction/workflow#publish-your-application-to-eik) and import maps to Eik, and to [manage aliases](https://eik.dev/docs/dependencies/aliases).                                            |
| [`@eik/common`](https://github.com/eik-lib/common)                     | The [`eik.json` schema](https://eik.dev/docs/reference/eik-json) and a gathering of shared utilities.                                                                                                                                                           |

## Workflow

Fork the repo(s) you would like to contribute to and make a branch off of `main`.

Commits in your pull request should follow the [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/) format.

This repo uses [semantic release](https://github.com/semantic-release/semantic-release)
to release automatically whenever changes are merged to `main`.

## Documentation

We use JSDoc to generate type definitions. If you're new to that workflow,
[the TypeScript docs](https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html)
and [this blogpost by Alex Harri](https://alexharri.com/blog/jsdoc-as-an-alternative-typescript-syntax)
are good starting points.

Documentation for Eik as a whole is in [eik-lib/eik-lib.github.io](https://github.com/eik-lib/eik-lib.github.io).
If you make changes to an existing feature or add a new one, please also open a pull request with the relevant
documentation to that repo.

For user-facing modules API reference documentation should be on the documentation website, for example:

- `@eik/cli`
- `@eik/node-client`
- `@eik/service`
- `@eik/sink`

For other modules `README.md` in the repo is enough.
