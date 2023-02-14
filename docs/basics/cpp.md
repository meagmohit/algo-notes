---
layout: default
title: C++ Refresher
parent: Basics
nav_order: 5
---



# C++ Refresher



**Statistical vs Dynamic Type:** C++ is statistically types, and every variable is defined as some type (e.g., float or int).

### Vectors
```cpp
#include <vector>
vector<int> v;
```
**Methods:** `push_back()`, `pop_back()`, `reserve()`, `size()`, `capacity()`

### Queue
```cpp
#include <queue>
queue<int> newQueue;
```
**Methods:** `push(item)`, `pop()`, `front()`, `back()`, `size()`, `empty()`

### Stacks
```cpp
#include <stack> 
stack<int> newStack;
```
**Methods:** `push(item)`, `pop()`, `top()`, `size()`, `empty()`

### Unordered Map
```cpp
#include <unordered_map>
unordered_map<int, int> d;
d[2] = 3;
set<int>::iterator it;
```
**Methods:** `[idx]`, `count(key)`, `erase(key)`, `begin()`, `end()`

### Unordered Set
```cpp
#include <set>
set<int> s;
insert(item)
set<int>::iterator it;
```
Set automatically sorts its own items

**Methods:** `set_union()`, `set_intersection()`, `set_difference()`, `insert()`, `erase()`, `clear()`, `begin()`, `end()`


{: .note}
Classes/Structure: Struct -> public by default, and in classes it is private by default







