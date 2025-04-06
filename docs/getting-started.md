---
title: Getting Started
description: A guide to help you get started with OptiReduce
---

<!-- <div style="text-align: center; padding: 0px 0px 50px 0px;">
  <img src="/assets/gf-icon-transparent-small.png" style="width: 200px;"/>
</div> -->

<!-- # Gigaflow Virtual Switch (GvS) -->
# Getting Started

Gigaflow is a multi-table cache architecture for the Open vSwitch (OVS) that captures pipeline-aware locality from the vSwitch pipelines to deliver significantly higher hit rate and lower end-to-end per-packet latency.
Unlike traditional caches (e.g, Megaflow) that capture entire traversals as cache entries, Gigaflow caches sub-traversals that are shared among many flows to capture a cross-product rule space in the SmartNIC.

## Why Gigaflow?

### 🏆 Minimizes Traffic Latency

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

## 🚀 Quick Start

### 🏗️ Testbed Setup

To set up a testbed for Gigaflow and do all necessary installations, follow the steps provided in the [Installation Guide](installation.md).
We also provide ready-made workloads (vSwitch pipelines, rulesets, and traffic traces) for benchmarking Gigaflow which will be installed automatically.

### 🏁 Bootstrap Gigaflow

If you haven't completed the last step of [installation](installation.md#gvs-and-tgen-installation), then you need to setup the experiment first.
Inside the Ansible container, run the following command to install the datasets (pipelines and traffic traces) on the GVS and TGEN machines.

```shell title="Ansible Container"
make setup-gvs-experiment
```

This command will also install [gvs](https://github.com/gigaflow-vswitch/gvs) and [tgen](https://github.com/gigaflow-vswitch/tgen) along with all their dependencies on the respective machines.

<!-- ## Experiment Options -->

### 📈 Run All Benchmarks

To run all experiments, including end-to-end and microbenchmarks, and collect performance logs, run the following command:

```shell title="Ansible Container"
make run-gvs-experiment
```
See our [benchmarking guide](benchmarks.md) for various options to evaluate Gigaflow against Megaflow cache using real-world workloads.

## 🧩 Next Steps with Gigaflow

### 📚 Learn More

* Check [Usage Guide](usage.md) for detailed configuration options
* Checkout the [Benchmarking Guide](benchmarks.md) for in-depth performance evaluation
* Read [Technical Details](technical-deepdive.md) to learn about Gigaflow's architecture

### 🛠️ Optimizing Performance

* Follow our [Benchmarking Guide](benchmarks.md) for in-depth performance evaluation
* Learn how to emulate high/low locality environments
* Comprehensively evaluate Gigaflow against traditional Megaflow cache

## 🛟 Getting Help

If you encounter issues:

1. Check the documentation pages linked above
2. Review existing GitHub issues
3. Open a new issue with a minimal example

## 🧑‍💻 Contributing

We welcome contributions to Gigaflow! Whether it's improving documentation, fixing bugs, optimizing performance, or adding new features, your help is appreciated. Please check our [Contributing Guide](contributing.md) for guidelines on how to get started.

## 📄 Research

Gigaflow was presented at ASPLOS'25. 

📄 [Gigaflow: Pipeline-Aware Sub-Traversal Caching for Modern SmartNICs](https://dl.acm.org/doi/10.1145/3676641.3716000)

&nbsp;

More details on our [Publications page](publications.md).

## 🧑‍💼 Support

Need help? Here are your options:

* Review all the [documentation](https://gigaflow-vswitch.github.io/)
* Open an [issue](https://github.com/gigaflow-vswitch/gigaflow-orchestrator/issues)
* Review [installation guide](installation.md) for setup help