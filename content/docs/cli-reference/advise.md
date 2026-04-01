---
title: specgate advise
weight: 3
tags:
  - Docs
  - Guide
next: /docs/guide
prev: /docs
---

The `specgate advise` command allows you to use a large language model (LLM) to generate concise summaries and descriptions for operations that are missing them. The suggestions are advisory, human-readable, and do not affect pass/fail status. 

Suggestions are not applied automatically. You will need to review the suggestions and apply changes manually.

{{< callout type="warning" >}}
  LLMs do not retain memories of previous interactions. If you run `specgate advise` multiple times on the same OAS file, you may receive different results each time. However, the core issues identified should remain consistent across runs. Consider saving the output to maintain a consistent reference.
{{< /callout >}}

## Why use an LLM?

OAS files are often auto-generated from code, but the quality of the output depends on how well the code is documented. Summaries, descriptions, and other human-readable fields are easy to skip, especially in larger codebases. 

`specgate advise` is designed for these gaps. When `specgate check` flags missing summaries or descriptions, `specgate advise` gives users a starting point for filling them in. 

The command passes the raw OAS file and the SpecGate error report to the model, so suggestions are based on what the spec actually does and what is missing rather than generic placeholder text. This also helps to minimize hallucinations. 

Suggestions are advisory. Always review before applying.

## Configuration 

`specgate advise` uses OpenAI's GPT-5-mini model to generate missing content. To use this command, you must have an OpenAI API key. You can sign up for a developer account on [OpenAI's website](https://openai.com/api/).

After you create an API key, add it to an `.env` file in your repository:

```bash {filename=".env"}
OPENAI_API_KEY=your_key_here
```

## Usage 


```bash {filename="terminal"}
specgate advise [file]
```

## Example output

```bash {filename="terminal"}
Suggested documentation
-----------------------
Suggestions are advistory. Review before applying.

GET /menu/{itemId}
  Summary: Get details of a specific menu item

GET /loyalty/{customerId}
  Description: Retrieves the loyalty points balance for a specific customer.
  
POST /loyalty/{customerId}
  Description: Redeems loyalty points for the specified customer.
```

