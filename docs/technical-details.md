---
title: Technical Details
description: Technical architecture and implementation details of Gigaflow
---

# Technical Details

This document describes the technical architecture and implementation details of Gigaflow.

## Gigaflow Architecture

Gigaflow is built as a caching sub-system in the Open vSwitch.

<!-- <figure markdown="span">
  ![Image title](assets/gigaflow-transparent.png){ width="500" }
  <figcaption>Figure 1: Gigaflow cache in the Open vSwitch (OVS)</figcaption>
</figure> -->

<figure id="gigaflow-figure">
  <img src="/assets/gigaflow-light.png" class="only-light" width="500">
  <img src="/assets/gigaflow-dark.png" class="only-dark" width="500">
  <figcaption>Gigaflow cache in the Open vSwitch (OVS)</figcaption>
</figure>

## Pipeline-Aware Locality

<figure id="gigaflow-figure">
  <img src="/assets/gigaflow-example.gif" width="900">
  <figcaption>An example of Gigaflow cache in action with three packets</figcaption>
</figure>

## Disjointedness Property

<figure id="disjointedness-figure">
  <img src="/assets/disjointedness-example.gif" width="900">
  <figcaption>Gigaflow captures pipeline-aware locality by capitalizing on field-level disjointedness in traversals</figcaption>
</figure>
