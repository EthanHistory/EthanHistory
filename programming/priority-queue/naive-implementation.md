---
description: Let's try out a simple implementation of priority queue for understanding!
---

# Naive implementation

```python
# Ignoring empty check
# Max heap : keep the maximum element at the highest priority
class simple_priority_queue:
    def __init__(self):
        self.queue = []
    def insert(elem):
        self.queue.append(elem)
    def pull():
        max_index = 0
        max_heap = self.queue[0]
        for i in range(1, len(self.queue)):
            if max_heap < self.queue[i]:
                max_index = i
                max_heap = self.queue[i]
        self.queue.pop(max_index)
        return max_heap
            
```
