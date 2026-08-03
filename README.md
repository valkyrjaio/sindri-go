<p align="center"><a href="https://valkyrja.io" target="_blank">
    <img src="https://raw.githubusercontent.com/valkyrjaio/art/refs/heads/master/long-banner/orange/go.png" width="100%">
</a></p>

# Sindri

[Sindri][github sindri] is the code generator and application creator for the
[Valkyrja][Valkyrja url] Go framework.

Sindri generates the data structs that let your application skip discovery work
at runtime — parsing configuration and source into container, event, and routing
data ahead of time. Named after the dwarven smith in Norse mythology who forged
Mjölnir and other divine artifacts, Sindri does for your Valkyrja app what his
namesake did for the gods: crafts the tools and artifacts that make it all work
faster and better.

<p>
    <a href="https://pkg.go.dev/github.com/valkyrjaio/sindri-go/v26"><img src="https://pkg.go.dev/badge/github.com/valkyrjaio/sindri-go/v26.svg" alt="Go Reference"></a>
    <a href="https://github.com/valkyrjaio/sindri-go/releases"><img src="https://img.shields.io/github/v/release/valkyrjaio/sindri-go" alt="Latest Version"></a>
    <a href="https://github.com/valkyrjaio/sindri-go/blob/26.x/go.mod"><img src="https://img.shields.io/badge/Go-1.26-orange" alt="Go Version"></a>
    <a href="https://github.com/valkyrjaio/sindri-go/blob/26.x/LICENSE.md"><img src="https://img.shields.io/github/license/valkyrjaio/sindri-go.svg" alt="License"></a>
    <a href="https://github.com/valkyrjaio/sindri-go/actions/workflows/ci.yml?query=branch%3A26.x"><img src="https://github.com/valkyrjaio/sindri-go/actions/workflows/ci.yml/badge.svg?branch=26.x" alt="CI Status"></a>
    <a href="https://coveralls.io/github/valkyrjaio/sindri-go?branch=26.x"><img src="https://coveralls.io/repos/github/valkyrjaio/sindri-go/badge.svg?branch=26.x" alt="Coverage Status"></a>
    <a href="https://sonarcloud.io/summary/new_code?id=valkyrjaio_sindri-go"><img src="https://sonarcloud.io/api/project_badges/measure?project=valkyrjaio_sindri-go&metric=sqale_rating" alt="Maintainability Rating"></a>
</p>

Port Status
-----------

The Go port is in progress, and this repository holds the scaffolding for it.
PHP is the reference implementation, and the Go build tool follows the Go port
of the framework. Read [`PORTS.md`][ports url] for the state of each port.

The sections below describe the build tool that every port implements. A command
is not in this repository until its own package exists.

What Sindri Does
----------------

- **Generates the data structs** — parses configuration and source into
  container, event, and routing data so your app skips discovery at runtime
- **Reads source through the Go toolchain** — walks the provider tree with
  `go/packages`, `go/ast`, and `go/analysis` to produce accurate, typed data
  files
- **Builds artifacts** — prepares deployable outputs for production runtimes
- **Handles upgrades** — assists with migrations between major Valkyrja versions

Sindri is a development dependency. The framework runs without a generated
cache, so nothing Sindri produces is required to serve a request, and the
framework carries no dependency on the Go AST packages.

Installation
------------

Sindri runs through `go tool`, so its version is pinned in your project and its
dependency graph never mixes with your application's:

```bash
go get -tool github.com/valkyrjaio/sindri-go/v26/cmd/sindri
```

The `/v26` suffix is part of the module path. Go's semantic import versioning
encodes a major version above 1 in the path, and the path tracks the annual
major version.

Getting Started
---------------

### Generating Data Files

Sindri's primary job is generating the data structs Valkyrja loads at boot —
container, event, and routing data derived from your configuration:

```bash
go tool sindri generate
```

`generate` is the default command. It reads your application's configuration and
source, then writes the corresponding data structs.

### Listing Available Commands

```bash
go tool sindri list
```

Documentation
-------------

Valkyrja documentation is baked into the framework repository so you can browse
it offline. For framework-level questions about Valkyrja itself, see the
[Valkyrja framework repository][framework url].

Versioning and Release Process
------------------------------

Sindri follows [semantic versioning][semantic versioning url] with a major
release every year, and support for each major version for 2 years from the date
of release.

### Supported Versions

Bug fixes are provided until 3 months after the next major release. Security
fixes are provided for 2 years after the initial release.

| Version | Go   | Release | Bug Fixes Until | Security Fixes Until |
| :------ | :--- | :------ | :-------------- | :------------------- |
| 26      | 1.26 | Q3 2026 | Q2 2027         | Q1 2028              |
| 27      | 1.27 | Q1 2027 | Q2 2028         | Q1 2029              |
| 28      | 1.28 | Q1 2028 | Q2 2029         | Q1 2030              |

Contributing
------------

Sindri is an open-source, community-driven project. Thank you for your interest
in helping develop, maintain, and release it.

See [`CONTRIBUTING.md`][contributing url] for the submission process and
[`VOCABULARY.md`][vocabulary url] for the terminology used across Valkyrja.

Run the full gate before you open a pull request:

```bash
make ci
```

Security Issues
---------------

If you discover a security vulnerability within Sindri, please follow our
[disclosure procedure][security vulnerabilities url].

License
-------

Sindri is open-source software licensed under the [MIT license][MIT license url].
See [`LICENSE.md`](./LICENSE.md).

[Valkyrja url]: https://valkyrja.io
[github sindri]: https://github.com/valkyrjaio/sindri-go
[framework url]: https://github.com/valkyrjaio/valkyrja-go
[ports url]: https://github.com/valkyrjaio/architecture/blob/26.x/PORTS.md
[contributing url]: https://github.com/valkyrjaio/.github/blob/26.x/CONTRIBUTING.md
[vocabulary url]: https://github.com/valkyrjaio/.github/blob/26.x/VOCABULARY.md
[security vulnerabilities url]: https://github.com/valkyrjaio/.github/blob/26.x/SECURITY.md
[semantic versioning url]: https://semver.org/
[MIT license url]: https://opensource.org/licenses/MIT
