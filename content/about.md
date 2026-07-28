---
title: About
type: about
---

## What is SpecGate?

SpecGate is a command-line tool for enforcing OpenAPI specification (OAS) readiness. It evaluates OAS files against a set of quality rules and surfaces errors and warnings before they reach production. SpecGate catches missing operation summaries, undocumented responses, placeholder server URLs, and other issues that make APIs harder to use.

## Project goals

* Give developers and technical writers a fast, lightweight way to catch documentation gaps in OpenAPI specs before release
* Integrate into CI pipelines as a quality gate
* Provide AI-powered suggestions that gives teams a starting point for improving specs
* Give teams flexibility through configuration

## FAQ

**Do I need an OpenAI API key to use SpecGate?** Only for the `specgate advise` command, which uses OpenAI's GPT-5-mini model to generate suggestions for missing summaries and descriptions. The `specgate check` and `specgate rules` commands work without one. 

**Is SpecGate a linter?** Not exactly! SpecGate enforces readiness rules. It checks whether a spec is complete enough to be used, documented, and integrated with. It's less concerned with style and more concerned with completeness.

**Can I disable rules I don't need?** Not yet, but configurable rules are planned for a future release. 

**Does SpecGate modify my spec?** No, SpecGate only reads your spec and reports issues. The `specgate advise` command generates suggestions but does not apply them. 

**What versions of the OpenAPI Specification does SpecGate support?** SpecGate currently supports OAS 3.x. 

## How is SpecGate implemented?

SpecGate is a binary written in Go. It uses the [kin-openapi](https://github.com/getkin/kin-openapi) library to parse and load OAS files and the OpenAI API for the `specgate advise` command.

**Requirements**:
* Go 1.25 or later (required to build from source)
* An OpenAI API key

## Current status

SpecGate is at v1.1.1 and is actively maintained. 

Planned for future releases:

* Additional validation rules
* Configurable rule sets
* Homebrew support for easier installation

## Who is behind this project?

SpecGate is built and maintained by Deanna Thompson, a senior technical writer specializing in API documentation, docs as code, and developer experiences. The project grew out of firsthand experience working with OpenAPI specs and noticing how often small documentation gaps caused real problems downstream.