---
title: Getting Started
description: A guide to help you get started with OptiReduce
---

# Getting Started

This guide will help you get started with Gigaflow Virtual Switch (GvS).

## System Requirements

### Hardware Requirements

* **Network Interface Card (NIC)**:
    * Recommended: Mellanox ConnectX NICs (supports flow bifurcation)
    * Alternative: Two NICs (one for TCP-based communication, one DPDK-compatible NIC)
* **CPU**: At least 4 dedicated cores for OptiReduce
* **Memory**: 16GB of hugepages

### Recommended Software Requirements

* Ubuntu 22.04 LTS 
* Python 3.9.19
* CUDA 11.7 and cuDNN 8.5 (optional, for GPU training)

## Installation Options

You can install OptiReduce in two ways:

### 1. Using Ansible (Recommended)

For automated deployment across multiple nodes:

```bash
git clone https://github.com/OptiReduce/ansible.git
cd ansible
make optireduce-full
```

### 2. Manual Installation

Clone and install the core repository on all nodes manually:

```bash
git clone https://github.com/OptiReduce/setup.git
cd setup
make install
```

For detailed installation instructions, see our [Installation Guide](installation.md).

## Quick Start

### 1. Setup Testbed

To set up a testbed for Gigaflow and do all necessary installations, follow the steps provided in the [Installation Guide](installation.md).
We also provide ready-made workloads (vSwitch pipelines, rulesets, and traffic traces) for benchmarking Gigaflow which will be installed automatically.

### 2. Benchmark Gigaflow



See our [benchmarking guide](benchmarks.md) for running these scripts.

## What's Next?

### Understanding Gigaflow

* Check [Usage Guide](usage.md) for detailed configuration options
* Read [Technical Details](technical-details.md) to learn about Gigaflow's architecture

### Optimizing Performance

* Follow our [Benchmarking Guide](benchmarks.md) to evaluate performance
* Learn how to emulate high/low locality environments
* Comprehensively evaluate Gigaflow against traditional Megaflow cache

## Getting Help

If you encounter issues:

1. Check the documentation pages linked above
2. Review existing GitHub issues
3. Open a new issue with a minimal example

## Contributing

We welcome contributions to Gigaflow! Whether it's improving documentation, fixing bugs, optimizing performance, or adding new features, your help is appreciated. Please check our [Contributing Guide](contributing.md) for guidelines on how to get started.