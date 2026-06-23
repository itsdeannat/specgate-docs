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

The SpecGate GitHub repository includes a [sample OAS file](https://github.com/itsdeannat/specgate/blob/main/testdata/oas.json) with documentation gaps you can use to explore the CLI. 

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
Loaded config from .specgate.yaml ✅

testdata/oas.json - 9 errors, 3 warnings
```

Errors must be resolved before the spec is considered production-ready. Warnings indicate documentation gaps that reduce spec quality but do not block the check.

{{< callout type="important" >}}
  If there are any structural issues with your OAS file, SpecGate outputs the issues to a `.specgate.log` file. See [specgate check](/docs/cli-reference/check) for more information.
{{< /callout >}}

### Step 4: Try strict mode

Run the check again with the `--strict` flag to treat warnings as errors:

```bash {filename="terminal"}
specgate check oas.json --strict
```

You should see all issues reported as errors:

```bash{filename="terminal"}
Loaded config from .specgate.yaml ✅

testdata/oas.json - 12 errors
```

### Step 5: See a detailed SpecGate report

If you'd like to see which errors and warnings SpecGate found, you can run the check with the `--verbose` flag:

```bash {filename="terminal"}
specgate check oas.json --verbose

Loaded config from .specgate.yaml ✅

testdata/oas.json - 9 errors, 3 warnings

error     Missing operation summary                   GET /menu/{itemId}
error     Missing error responses (4xx/5xx/default)   POST /orders
error     Missing error responses (4xx/5xx/default)   GET /loyalty/{customerId}
error     Missing error responses (4xx/5xx/default)   POST /loyalty/{customerId}
error     Missing error responses (4xx/5xx/default)   GET /menu
error     Missing parameter description               GET /menu/{itemId}
error     Missing parameter description               GET /orders/{orderId}
error     Missing parameter description               GET /loyalty/{customerId}
error     Missing parameter description               POST /loyalty/{customerId}
warning   Missing operation description               GET /menu/{itemId}
warning   Missing operation description               GET /loyalty/{customerId}
warning   Missing operation description               POST /loyalty/{customerId}

Run with --strict to treat warnings as errors.
```

### Step 6: Get LLM-powered suggestions

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