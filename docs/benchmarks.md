---
title: Benchmarking Guide
description: Guide for benchmarking Gigaflow against various real-world workloads
---

# Gigaflow Benchmarking Guide

This guide explains how to evaluate Gigaflow against Megaflow cache using real-world [vSwitch pipelines and traffic traces](installation.md).

## Experiment Setup

If you haven't completed the last step of [installation](installation.md#gvs-and-tgen-installation), then you need to setup the experiment first.
Inside the Ansible container, run the following command to install the datasets (pipelines and traffic traces) on the GVS and TGEN machines.

```shell title="Ansible Container"
make setup-gvs-experiment
```

This command will also install [gvs](https://github.com/gigaflow-vswitch/gvs) and [tgen](https://github.com/gigaflow-vswitch/tgen) along with all their dependencies on the respective machines.

## Experiment Options

### Option 1. All

To run all experiments (end-to-end and microbenchmarks) and collect logs, run the following command:

```shell title="Ansible Container"
make run-gvs-experiment
```

### Option 2. End-to-End Evals

To setup and run only end-to-end experiments:

```shell title="Ansible Container"
make run-gvs-ee-experiment
```

### Option 3. Microbenchmarks
To setup and run only microbenchmark experiments:

```shell title="Ansible Container"
make run-gvs-bm-experiment
```

### Option 4. Custom Experiment

To setup and run a specific experiment (with a given locality, pipeline, and Gigaflow tables configuration), modify the following variables in `vars/main.yml`.

The locality (high/low) to generate the correct traffic load. 
Choose an option from `locality_static`:

```yaml title="vars/main.yml" linenums="68"
locality_dynamic:
  current:
    locality: "high-locality"
```

The pipeline to install and send traffic for.
Choose an option from `pipelines_static`:

```yaml title="vars/main.yml" linenums="77"
pipelines_dynamic: 
  current: 
    name: "cord-ofdpa"
    sub_path: "cord/ofdpa"
```

The number of Gigaflow tables and entries in each of them.
Choose an option from `gigaflow_static`:

```yaml title="vars/main.yml" linenums="95"
gigaflow_dynamic:
  experiment: "ee" # this is just the name for the logs directory
  options:
      gigaflow_tables_limit: 4
      gigaflow_max_entries: 8000
```

Once these variables are setup, run the following sequence of commands. 

```shell title="Ansible Container"
make resetup-tgen-scripts
make start-switch-gvs 
make install-rules
make start-tgen
make stop-tgen
make uninstall-rules 
make stop-switch-gvs
make collect-logs
```

## Experiment Teardown

To stop the experiment and remove all installed components, run the following command:

```shell title="Ansible Container"
make teardown-gvs-experiment
```

## Results

The following table compares the iteration time (**s/it**) for different communication strategies, lower is better:

### Analysis

* **OptiReduce consistently outperforms all other methods** across different models and environments.
* Performance gains are especially significant for **larger models** (GPT-2-large, Llama-3.2), where OptiReduce achieves **up to 40% faster iteration time** in low-tail environment.
* The benefits are **more pronounced in multi-node environments** (`Env=3`), where communication bottlenecks become more severe and speedups reach around **2x**.

## Documentation

* [Getting Started](getting-started.md)
* [Technical Details](technical-details.md)
* [Installation Instructions](installation.md)
* [Usage Instructions](usage.md)