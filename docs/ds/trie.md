---
layout: default
title: Trie
parent: Data Structures
nav_order: 4

---

# Trie

{: .warning}

SECTION INCOMPLETE: Review Content

Dictionary of dictionaries in a recursive fashion. Let us understand it with an example of adding and search a word.
Trick: Using `$` as a key to add the identifier that the word is present

```python
class WordDictionary:
    def __init__(self):
        self.trie = {}
    def addWord(self):
        node = self.trie
        for ch in word:
            if not ch in node: node[ch] = {}
            node = node[ch]
        node['$'] = True
    def searchWord(self):
        node = self.trie
        for ch in word:
            if not ch in node: return False
        node = node[ch]
        return node['$']
```

