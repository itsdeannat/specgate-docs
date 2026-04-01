---
title: Configuration
weight: 3
tags:
  - Docs
  - Guide
next: /docs/guide
prev: /docs
---

To configure SpecGate's behavior, you need a `.specgate.yaml` configuration file. The file must live in the project root.

## Create a configuration file

To create a `.specgate.yaml` file, run the command `specgate init` from the command line. This command creates the `.specgate.yaml` file in the project root. 

If you forget to create a configuration file, the first time you run `specgate check`, a configuration file will be created for you:

```bash
No SpecGate config found in project root. Created .specgate.yaml
Edit the config, then rerun:
 specgate check
```

## Reset file settings

If you need to reset the file settings to their defaults, run `specgate init --force`. This command overwrites the configuration file.

## File settings

### `server_url_blocklist`

Use `server_block_list` to specify the URLs that SpecGate should flag as violations:

```yaml
config:
    server_block_list:
        - https://www.example.com
        - https://localhost
```
