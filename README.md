# Group Betweenness Centrality

This project implements **Group Betweenness Centrality (GBC)** using shortest paths for two network datasets:

- Karate Club Network
- Airline Reachability Network

## Overview

Group Betweenness Centrality measures the extent to which a group of nodes lies on shortest paths between nodes outside the group.

When multiple shortest paths exist between a source-target pair, the contribution is distributed equally among those shortest paths.

## Networks Used

### 1. Karate Club Network

The Karate Club Network represents social connections between members of a karate club.

- Individual Betweenness Centrality is first calculated.
- The top 15 nodes are selected as candidate nodes.
- Groups of 3 nodes are formed from these candidates.
- The group with the highest GBC is identified.
- Normalized GBC is also calculated.

### 2. Airline Reachability Network

The Airline Reachability Network is a directed network constructed from `airline.csv`.

- `source` and `target` columns are used to construct the directed graph.
- A strongly connected subnetwork of 25 nodes is selected.
- All shortest paths between ordered node pairs are calculated.
- Groups of 3 nodes are evaluated.
- The group with the highest GBC is identified.
- Normalized GBC is calculated using the directed-network normalization.

## Method

For each group:

1. Source and target nodes must be outside the group.
2. All shortest paths between the source and target are considered.
3. If a group member appears as an internal node on a shortest path, the group receives a fractional contribution.
4. The contributions are summed to obtain the group's GBC.
5. The group with the maximum GBC is selected.

## Normalization

For the Karate Club Network (undirected):

$$
Normalized\ GBC = \frac{GBC}{(n-k)(n-k-1)/2}
$$

For the Airline Reachability Network (directed):

$$
Normalized\ GBC = \frac{GBC}{(n-k)(n-k-1)}
$$

where:

- `n` = number of nodes
- `k` = size of the group

## Requirements

Install the required Python libraries:

```bash
pip install pandas networkx matplotlib
