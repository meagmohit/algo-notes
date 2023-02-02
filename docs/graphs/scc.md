---
layout: default
title: Strongly Connected Components
parent: Graphs
nav_order: 4
---

# Strongly Connected Components

- Strongly connected component, 𝐶, of a graph 𝐺, as the largest subset of vertices 𝐶⊂𝑉 such that for every pair of vertices 𝑣,𝑤∈𝐶 we have a path from 𝑣 to 𝑤 and a path from 𝑤 to 𝑣.
- Algorithm:
  1. Call `dfs` for the graph 𝐺 to compute the finish times for each vertex.
  2. Compute 𝐺 transpose.
  3. Call `dfs` for the graph 𝐺 transpose but in the main loop of DFS explore each vertex in decreasing order of finish time.
  4. Each tree in the forest computed in step 3 is a strongly connected component. Output the vertex ids for each vertex in each tree in the forest to identify the component.