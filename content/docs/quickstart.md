---
title: Quickstart
weight: 2
tags:
  - Docs
  - Guide
next: /docs/cli-reference
prev: /docs/installation
---

In this guide, you'll learn how to run your first SpecGate check using a sample OpenAPI specification (OAS) file.


## Before you begin

Make sure you have completed the [installation steps](/docs/installation).

{{% steps %}}

### Step 1: Download the sample OAS file

The SpecGate GitHub repository includes a [sample OAS file](https://github.com/itsdeannat/specgate-cli/blob/main/testdata/oas.json) with documentation gaps you can use to explore the CLI. 

### Step 2: Run your first check

Run the `check` command against the sample spec:

```bash{filename="terminal"}
specgate check oas.json
```

You should see output like this:
```
ERRORS
------

Missing operation summaries for 1 operation(s):

- GET /menu/{itemId}

Missing error responses (4xx/5xx/default) for 4 operation(s):

- POST /orders
- GET /loyalty/{customerId}
- POST /loyalty/{customerId}
- GET /menu

WARNINGS
--------

Missing operation descriptions for 3 operation(s):

- GET /menu/{itemId}
- GET /loyalty/{customerId}
- POST /loyalty/{customerId}
```

Errors must be resolved before the spec is considered production-ready. Warnings indicate documentation gaps that reduce spec quality but do not block the check.

### Step 3: Try strict mode

Run the check again with the `--strict` flag to treat warnings as errors:

```bash {filename="terminal"}
specgate check oas.json --strict
```

You should see all issues reported as errors:

```
STRICT MODE ENABLED

ERRORS
------

Missing operation summaries for 1 operation(s):

- GET /menu/{itemId}

Missing error responses (4xx/5xx/default) for 4 operation(s):

- POST /orders
- GET /loyalty/{customerId}
- POST /loyalty/{customerId}
- GET /menu

Missing operation descriptions for 3 operation(s):

- GET /menu/{itemId}
- GET /loyalty/{customerId}
- POST /loyalty/{customerId}
```

### Step 4: Get LLM-powered suggestions

Run the `advise` command to generate suggested summaries and descriptions for operations that are missing them.

{{< callout type="info" >}}
  The `advise` command requires an OpenAI API key. Set the `OPENAI_API_KEY` environment variable before running this command. See [specgate advise](/docs/cli-reference/advise.md) for more information.
{{< /callout >}}

```bash {filename="terminal"}
specgate advise oas.json
```

{{% /steps %}}

## Next steps

- Review the [CLI reference](/docs/cli-reference) for full command documentation
- Run `specgate rules` to see the full list of rules SpecGate enforces