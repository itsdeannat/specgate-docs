---
title: Installation
weight: 1
tags:
  - Docs
  - Guide
next: /docs/guide
prev: /docs
---

Follow these steps to install SpecGate on your system. 

### Prerequisites

* Go 1.25 or later must be installed. Download it at [go.dev](https://go.dev).
* `make` is required to build the binary. 

> **Note:** SpecGate currently requires building from source. Pre-built binaries are planned for a future release.

{{% steps %}}

### Step 1: Clone the repository

```bash
git clone https://github.com/itsdeannat/specgate-cli.git
cd specgate-cli
```

### Step 2: Build the binary 

```bash
make build
```

This command compiles the project and produces the `specgate` executable.

### Step 3: Verify installation

Run this command: 

```bash
./specgate -v
```

You should see output similar to:

```bash
specgate version 0.1.0
```

### Step 4: Move the binary to your PATH (recommended)

```bash
mv specgate /usr/local/bin/ 
```

This allows you to run `specgate` from any directory.

Depending on your system, this step may require `sudo`.

If you prefer not to modify your PATH, you can run the binary directly from the project directory:

```bash
./specgate -v
```

{{% /steps %}}