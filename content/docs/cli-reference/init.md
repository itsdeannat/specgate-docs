---
title: specgate init
weight: 1
tags:
  - Docs
  - Guide
next: /docs/guide
prev: /docs
---

The `specgate init` command creates a new `.specgate.yaml` file. This file allows you to configure SpecGate's behavior. To learn more about `.specgate.yaml`, see [Configuration](/docs/configuration).

After you run `specgate init`, a new configuration file is created:

```yaml bash {filename=".specgate.yaml"}
config:
    server_block_list:
        - http://www.example.com
```

## Usage 

```bash {filename="terminal"}
specgate init
```


## Unique options

These are options that only apply to the `specgate init` command:

### Force

Use the `--force` option to restore an existing configuration file to its default settings.

```bash {filename="terminal"}
specgate init --force
```