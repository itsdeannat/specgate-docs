---
linkTitle: "Documentation"
title: Introduction
---

👋 Hello! Welcome to the SpecGate documentation!

## What is SpecGate?

SpecGate is a fast, lightweight CLI tool for enforcing OpenAPI specification (OAS) readiness. Designed for technical writers and developers who care about API documentation quality, it evaluates OAS files against a set of quality rules and surfaces errors and warnings before they reach production.

## Features

* **Error and warning rules**: Evaluate OAS files against a set of error and warning rules, surfacing issues before they reach production
* **Strict mode**: Promote warnings to errors for teams that want zero tolerance on documentation gaps
* **AI-powered suggestions**: Generate suggested summaries and descriptions for operations that are missing them using an LLM
* **CI-ready**: Exits with a non-zero status code when errors are found, allowing for integration with GitHub Actions or GitLab CI
* **Rule transparency**: Run `specgate rules` to see which rules are being enforced and how they're categorized

## Example output

```bash
Loaded config from .specgate.yaml

oas.json - 5 errors, 1 warning

error     Missing operation summary                   GET /menu/{itemId}
error     Missing error responses (4xx/5xx/default)   GET /menu
error     Missing error responses (4xx/5xx/default)   POST /orders
error     Missing parameter description               GET /menu/{itemId}
error     Missing parameter description               GET /orders/{orderId}
warning   Missing operation description               GET /menu/{itemId}

Run with --strict to treat warnings as errors.
```

## Next steps

Head over to the [Installation guide](/docs/installation) to get started!
