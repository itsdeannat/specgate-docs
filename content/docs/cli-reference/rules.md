---
title: specgate rules
weight: 3
tags:
  - Docs
  - Guide
next: /docs/guide
prev: /docs
---

`specgate rules` displays all of the rules that SpecGate enforces. Errors fail the check and return a non-zero exit code. Warnings are reported but do not fail the check unless you pass the `--strict` option. 

## Errors

| Rule | Reason | 
| :---- | :--------- |
| Operations must have a summary| Summaries are the first thing API users see in documentation and tooling like Swagger UI. Without them, the API is difficult to navigate. |
| Operations must include at least one 2xx response | A missing success response means the specification doesn't describe what a successful call returns, leaving API users to guess. | 
| Operations must include at least one error response | Without error responses, users won't know how to handle failures. |
| No placeholder server URLs | Consumers cannot use the API if the base URL does not point to a real environment. |
| Servers object must be defined | Without a `servers` object, consumers have no base URL to call the API. |
| Success responses must include descriptions | Without a description, consumers don't know what a successful response means or what to expect from the returned data.|
| Error responses must include descriptions | Without a description, consumers have no guidance on what caused the error or how to resolve it, making the API difficult to debug and integrate with. |

## Warnings

| Rule | Reason | 
| :--- | :-------- |
| Operations should have a description | Descriptions provide additional context beyond the summary, such as behavior and edge cases. | 
| Operations should have an `operationId`| Missing `operationIds` make SDK method and function names unpredictable and hard to read. | 
| Operations should have a meaningful `tag` | Using tags can help enhance readability in your API documentation, as it groups related requests together. | 
