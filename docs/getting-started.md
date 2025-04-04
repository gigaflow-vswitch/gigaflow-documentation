---
title: Getting Started
description: A guide to help you get started with OptiReduce
---

# Getting Started

This guide will help you get started with Gigaflow Virtual Switch (GvS).

## Quick Start

### Testbed Setup

To set up a testbed for Gigaflow and do all necessary installations, follow the steps provided in the [Installation Guide](installation.md).
We also provide ready-made workloads (vSwitch pipelines, rulesets, and traffic traces) for benchmarking Gigaflow which will be installed automatically.

### Bootstrap Gigaflow

If you haven't completed the last step of [installation](installation.md#gvs-and-tgen-installation), then you need to setup the experiment first.
Inside the Ansible container, run the following command to install the datasets (pipelines and traffic traces) on the GVS and TGEN machines.

```shell title="Ansible Container"
make setup-gvs-experiment
```

This command will also install [gvs](https://github.com/gigaflow-vswitch/gvs) and [tgen](https://github.com/gigaflow-vswitch/tgen) along with all their dependencies on the respective machines.

<!-- ## Experiment Options -->

### Run All Benchmarks

To run all experiments, including end-to-end and microbenchmarks, and collect performance logs, run the following command:

```shell title="Ansible Container"
make run-gvs-experiment
```
See our [benchmarking guide](benchmarks.md) for various options to evaluate Gigaflow against Megaflow cache using real-world workloads.

## What's Next?

### Understanding Gigaflow

* Check [Usage Guide](usage.md) for detailed configuration options
* Read [Technical Details](technical-details.md) to learn about Gigaflow's architecture

### Optimizing Performance

* Follow our [Benchmarking Guide](benchmarks.md) for in-depth performance evaluation
* Learn how to emulate high/low locality environments
* Comprehensively evaluate Gigaflow against traditional Megaflow cache

## Getting Help

If you encounter issues:

1. Check the documentation pages linked above
2. Review existing GitHub issues
3. Open a new issue with a minimal example

## Contributing

We welcome contributions to Gigaflow! Whether it's improving documentation, fixing bugs, optimizing performance, or adding new features, your help is appreciated. Please check our [Contributing Guide](contributing.md) for guidelines on how to get started.