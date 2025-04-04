---
title: Usage Guide
description: Guide for using Gigaflow as a caching sub-system for OVS
---

# Using Gigaflow

This guide explains how to use Gigaflow as a new caching sub-system integrated in the Open vSwitch (GvS).

## Prerequisites

Before using Gigaflow, ensure you have:

<!-- <figure markdown="span" id="workflow-figure">
  ![Image title](assets/artifact.png){ width="700" }
  <figcaption>The high-level workflow to evaluate Gigaflow (GvS)</figcaption>
</figure> -->

<figure id="workflow-figure-test">
  <img src="/assets/artifact-light.png" class="only-light" width="700">
  <img src="/assets/artifact-dark.png" class="only-dark" width="700">
  <figcaption>The high-level workflow to evaluate Gigaflow (GvS)</figcaption>
</figure>

## Running Gigaflow and Performance Evaluation

To evaluate performance:

1. Follow our [benchmarking guide](benchmarks.md)
2. Use provided workloads and scripts to emulate high/low locality environments
3. Benchmark Gigaflow against Megaflow cache using real-world vSwitch pipelines and traffic traces

## Next Steps

* See [Installation Instructions](installation.md) for setup details
* Review [Technical Details](technical-details.md) for architecture information
* Check [Benchmarks](benchmarks.md) for performance evaluation guide