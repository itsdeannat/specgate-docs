---
title: specgate check
weight: 1
tags:
  - Docs
  - Guide
next: /docs/guide
prev: /docs
---

The `specgate check` command allows you to evaluate an OpenAPI specification against several readiness rules. If errors are detected, the command exits with a non-zero status code, allowing it to be used as a quality gate in CI. 

`specgate check` reports two types of issues: errors and warnings.

## Errors 

**Errors** are rules the spec *must* pass to be considered production-ready. A spec with errors is missing information that API users need to understand or use the API effectively. 

Additionally, incorrect specs can cause SDK generators to produce broken or incomplete client libraries, affecting every developer who depends on your API.


## Warnings

Warnings are rules the spec *should* pass to be production-ready. A spec with warnings is functional but has documentation gaps that could reduce clarity and usability for API users or affect SDK documentation quality.


## Usage

```bash {filename="terminal"}
specgate check [file]
```

## Unique options 

These are options that only apply to the `specgate check` command:

### Format

Use the `--format` option to output results in `json` format. 

```bash {filename="terminal"}
specgate check [file] --format json
```

### Strict

Use the `--strict` option to treat all warnings as errors. 

```bash {filename="terminal"}
specgate check [file] --strict
```

