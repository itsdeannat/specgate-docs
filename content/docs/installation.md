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

{{% steps %}}

### Step 1: Download the latest release
Download the latest pre-built binary for your system from the [SpecGate releases page](https://github.com/itsdeannat/specgate/releases).

Alternatively, if you prefer to build from source:
```bash
git clone https://github.com/itsdeannat/specgate.git
cd specgate
make build 
```

### Step 2: Verify installation
Run this command:
```bash
./specgate -v
```
You should see output similar to:
```bash
specgate version 1.1.1
```

### Step 3: Move the binary to your PATH (recommended)
```bash
mv specgate /usr/local/bin/
```
This allows you to run `specgate` from any directory.

Depending on your system, this step may require `sudo`.

If you prefer not to modify your PATH, you can run the binary directly from its current location to verify installation:
```bash
./specgate -v
```

{{% /steps %}}