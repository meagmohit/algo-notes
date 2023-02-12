---
layout: default
title: Hash Maps
parent: Data Structures
nav_order: 2

---

# Hash Maps

Data structure is **Hash Table,** where all elements are stored using a **hash function**.

**Load factor:** # of items/ Table Size

**Collisions** occur if the hash function point to the occupied slot in hash table. **Perfect hash function** maps each item to a unique element to make sure that collisions do not occur. Given an arbitrary collection of items, there is no systematic way to construct a perfect hash function.

Commonly used hash functions:

- Folding method: Dividing the items into equal size pieces and adding them together. The added sum is modulo with the size of hash table to find the right slot.
- Mid-square method: Square the item and extract some portion of the resultant digitis. The result is modulo with the hash table size to find the right slot.

**Collision resolution:**

- Linear Probing: Start at the original hash value position and move in a sequential manner until we encounter the first slot that is empty.
- Rehashing: We skip some 'k' slots instead of moving it in a sequential manner. With linear probing the rehash function is, `𝑛𝑒𝑤ℎ𝑎𝑠ℎ𝑣𝑎𝑙𝑢𝑒=𝑟𝑒ℎ𝑎𝑠ℎ(𝑜𝑙𝑑ℎ𝑎𝑠ℎ𝑣𝑎𝑙𝑢𝑒).`In general, for 'k' skips the rehash function is `𝑟𝑒ℎ𝑎𝑠ℎ(𝑝𝑜𝑠)=(𝑝𝑜𝑠+𝑠𝑘𝑖𝑝)%𝑠𝑖𝑧𝑒𝑜𝑓𝑡𝑎𝑏𝑙𝑒`
- Quadratic probing: We use a hash function that increments the skip values by 1,3,5,7,9 etc. `𝑟𝑒ℎ𝑎𝑠ℎ(𝑝𝑜𝑠)=(ℎ+𝑖*i)`
- Chaining: Allowing many items to exist at the same location in the hash table.

**Computation Complexity:**

The best case hashing would provide a 𝑂(1). In collision following would hold for average number of comparisons,

- Open Addressing with Linear probing: `0.5*(1+ 1/(1-L))` for successful and `0.5*(1+ 1/(1-L)*(1-L))` for unsuccessful
- Chaining: `1+0.5*L` for successful and `L` if unsuccessful



## References

- [Runstone Academy PythonDS Book Chapter 6.5: Hashing](https://runestone.academy/ns/books/published/pythonds/SortSearch/toctree.htmls)
