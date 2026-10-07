# SpecGate documentation

This repository contains the documentation website for [SpecGate](https://github.com/itsdeannat/specgate), a command-line tool for checking OpenAPI Specification (OAS) files for readiness issues before release.

## What is SpecGate?

SpecGate checks OAS 3.x files against readiness rules and reports errors and warnings. It focuses on API completeness and usefulness rather than style.

For example, SpecGate can flag:

- Missing operation summaries
- Undocumented responses
- Placeholder server URLs

Errors can be used as a CI quality gate, and strict mode promotes warnings to errors. The `specgate advise` command can also generate suggested summaries and descriptions for operations.

See the [SpecGate repository](https://github.com/itsdeannat/specgate) for the CLI source, releases, and examples.

**This repository is dedicated to the documentation website and its content. It does not contain the CLI source code.**

## How this site is built

The documentation site is built with [Hugo](https://gohugo.io/) and the [Hextra](https://github.com/imfing/hextra) theme.

The documentation is maintained as a standalone Git-based content repository.