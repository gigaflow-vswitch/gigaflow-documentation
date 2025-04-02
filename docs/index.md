---
title: Gigaflow
description: A pipeline-aware sub-traversal cache for the Open vSwitch
---

<div style="text-align: center; padding: 0px 0px 50px 0px;">
  <img src="assets/gf-icon-transparent-small.png" style="width: 200px;"/>
</div>

<!-- ![Alt text](figures/gigaflow.png) -->

# Gigaflow Virtual Switch (GvS)
Gigaflow is a multi-table cache architecture for the Open vSwitch (OVS) that captures pipeline-aware locality from the vSwitch pipelines to deliver significantly higher hit rate and lower end-to-end per-packet latency.
Unlike traditional caches (e.g, Megaflow) that capture entire traversals as cache entries, Gigaflow caches sub-traversals that are shared among many flows to capture a cross-product rule space in the SmartNIC.

## Why Gigaflow?

### 🚀 Lower End-to-End Traffic Latency

* Captures a cross-product rule space in a multi-table cache, up to 450x bigger than Megaflow!
* Delivers significantly cache higher hit rate than traditional Megaflow cache
* Reduces up to 90% cache misses while using 18% lesser cache entries

### 💡 Key Features

* **Pipeline-Aware Locality**: Captures locality from the vSwitch pipelines using disjointedness
* **Longest Traversal Matching (LTM)**: Handles correctness in a multi-table lookup cache architecture 
* **Open vSwitch (OVS) Integration**: Integrated in the OVS as a new caching sub-system

### 🔧 Technical Highlights

* Efficient memory pool management (TODO: fix)
* Zero-copy operations for maximum performance (TODO: fix)
* SmartNIC offload available for Xilinx Alveo U250 Data Center Accelerator (coming soon!)

## Choose your path with Gigaflow

### 👉 Quick Start

* [Getting Started](getting-started.md)
* [Installation Guide](installation.md)
* [Usage Guide](usage.md)

### 📚 Learn More

* [Technical Details](technical-details.md)
* [Benchmarking Guide](benchmarks.md)

## Research

Gigaflow was presented at ASPLOS'25. Read our paper:

📄 [Gigaflow: Pipeline-Aware Sub-Traversal Caching for Modern SmartNICs](https://dl.acm.org/doi/10.1145/3676641.3716000)

## Support

Need help? Here are your options:

* Review all the [documentation](https://gigaflow-vswitch.github.io/)
* Open an [issue](https://github.com/gigaflow-vswitch/Gigaflow-Artifact-ASPLOS2025/issues)
* Review [installation guide](installation.md) for setup help