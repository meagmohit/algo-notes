---
layout: default
title: Balanced BSTs
parent: Trees
nav_order: 4

---



# Balanced BSTs

{: .warning}

SECTION INCOMPLETE: Review Content and Add

**Balance Factor:** `𝑏𝑎𝑙𝑎𝑛𝑐𝑒𝐹𝑎𝑐𝑡𝑜𝑟=ℎ𝑒𝑖𝑔ℎ𝑡(𝑙𝑒𝑓𝑡𝑆𝑢𝑏𝑇𝑟𝑒𝑒)−ℎ𝑒𝑖𝑔ℎ𝑡(𝑟𝑖𝑔ℎ𝑡𝑆𝑢𝑏𝑇𝑟𝑒𝑒)`

All operations are O(logN)

Important methods and functions:

- `def put(self, key)`: Calling the updatebalance method after adding the node
- `def updateBalance(self, node)`: rebalances and updates the balancing factors of the node
- `def rotateLeft(self, rotRoot):` rotates left
- `def rebalance(self, node):` rebalances the tree by rotleft or rotright