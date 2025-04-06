---
title: Gigaflow
description: A pipeline-aware sub-traversal cache for the Open vSwitch
---

<div style="text-align: center; padding: 0px 0px 50px 0px;">
  <img src="assets/gf-icon-transparent-small.png" style="width: 200px;"/>
</div>

# Gigaflow Virtual Switch (GvS)
Gigaflow is a multi-table cache architecture for the Open vSwitch (OVS) that captures pipeline-aware locality from the vSwitch pipelines to deliver significantly higher hit rate and lower end-to-end per-packet latency.
Unlike traditional caches (e.g, Megaflow) that capture entire traversals as cache entries, Gigaflow caches sub-traversals that are shared among many flows to capture a cross-product rule space in the SmartNIC.

## Why Gigaflow?

### 🚀 Minimizes Traffic Latency

* Captures a cross-product rule space—up to 450x bigger than Megaflow!
* Delivers up to 51% higher cache hit rate than traditional Megaflow cache
* Reduces cache misses by up to 90% while using 18% lesser cache entries

### 💡 Key Features

* **Pipeline-Aware Locality**: Captures locality from the vSwitch pipelines using disjointedness
* **Longest Traversal Matching (LTM)**: Handles correctness in a multi-table lookup cache architecture 
* **Open vSwitch (OVS) Integration**: Integrated in OVS as a new caching sub-system

### 🔧 Technical Highlights

* Multi-table cache architecture enabling efficient matching across a significantly expanded rule space
* Effeciently captures pipeline-aware locality by maximizing sub-traversal level disjointedness
* SmartNIC offload available for Xilinx Alveo U250 Data Center Accelerator (coming soon!)

## Next Steps with Gigaflow

### 👉 Quick Start

* [Getting Started](getting-started.md)
* [Installation Guide](installation.md)
* [Usage Guide](usage.md)

### 📚 Learn More

* [Technical Details](technical-deepdive.md)
* [Benchmarking Guide](benchmarks.md)

## Research

Gigaflow was presented at ASPLOS'25. Read our paper:

📄 [Gigaflow: Pipeline-Aware Sub-Traversal Caching for Modern SmartNICs](https://dl.acm.org/doi/10.1145/3676641.3716000)

## Support

Need help? Here are your options:

* Review all the [documentation](https://gigaflow-vswitch.github.io/)
* Open an [issue](https://github.com/gigaflow-vswitch/gigaflow-orchestrator/issues)
* Review [installation guide](installation.md) for setup help