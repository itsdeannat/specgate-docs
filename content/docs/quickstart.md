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

### Step 2: Generate a config file

SpecGate's behavior is controlled by a `.specgate.yaml` file. To learn more about `.specgate.yaml`, see [Configuration](/docs/configuration).

To generate a config file, run `specgate init`. This creates the config file in the project root.

### Step 3: Run your first check

Run the `check` command against the sample spec:

```bash{filename="terminal"}
specgate check oas.json
```

You should see output like this:

```bash{filename="terminal"}
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

Errors must be resolved before the spec is considered production-ready. Warnings indicate documentation gaps that reduce spec quality but do not block the check.

### Step 4: Try strict mode

Run the check again with the `--strict` flag to treat warnings as errors:

```bash {filename="terminal"}
specgate check oas.json --strict
```

You should see all issues reported as errors:

```bash{filename="terminal"}
Loaded config from .specgate.yaml

STRICT MODE ENABLED

oas.json - 6 errors

error     Missing operation summary                   GET /menu/{itemId}
error     Missing error responses (4xx/5xx/default)   GET /menu
error     Missing error responses (4xx/5xx/default)   POST /orders
error     Missing parameter description               GET /menu/{itemId}
error     Missing parameter description               GET /orders/{orderId}
error     Missing operation description               GET /menu/{itemId}
```

### Step 5: Get LLM-powered suggestions

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