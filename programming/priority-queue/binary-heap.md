# Binary Heap

a [heap](https://en.wikipedia.org/wiki/Heap\_\(data\_structure\)) [data structure](https://en.wikipedia.org/wiki/Data\_structure) that takes the form of a [binary tree](https://en.wikipedia.org/wiki/Binary\_tree). Binary heaps are a common way of implementing [priority queues](https://en.wikipedia.org/wiki/Priority\_queue).



## Implementation

#### up-heap operation

<mark style="color:green;">also known as</mark> <mark style="color:green;"></mark>_<mark style="color:green;">bubble-up</mark>_<mark style="color:green;">,</mark> <mark style="color:green;"></mark>_<mark style="color:green;">percolate-up</mark>_<mark style="color:green;">,</mark> <mark style="color:green;"></mark>_<mark style="color:green;">sift-up</mark>_<mark style="color:green;">,</mark> <mark style="color:green;"></mark>_<mark style="color:green;">trickle-up</mark>_<mark style="color:green;">,</mark> <mark style="color:green;"></mark>_<mark style="color:green;">swim-up</mark>_<mark style="color:green;">,</mark> <mark style="color:green;"></mark>_<mark style="color:green;">heapify-up</mark>_<mark style="color:green;">, or</mark> <mark style="color:green;"></mark>_<mark style="color:green;">cascade-up</mark>_

the process of creating a heap data structure from a binary tree. It is used to create a Min-Heap or a Max-Heap.

```python
# binary max heap implementation without recursion
class binaryMaxHeap:
    def __init__(self, arr=[]):
        self.heap = arr
        if len(self.heap) > 0:
            self.heafify(0)
    
    def __parent(self, i : int) -> int:
        return (i - 1) // 2
    
    def __lchild(self, p : int) -> int:
        return p * 2 + 1
        
    def __rchild(self, p : int) -> int:
        return p * 2 + 2
    
    def __up_heap(self, i : int):
        while i > 0:
            p = self.__parent(i)
            if self.heap[i] > self.heap(p):
                self.heap[i], self.heap[p] = self.heap[p], self.heap[i]
            else:
                break
    def __largest_swap(self, i : int) -> int:
            largest = i
            left = self.__lchild(i)
            right = self.__rchild(i)
            if left < len(self.heap):
                if self.heap[left] > self.heap[i]:
                    largest = left
    
            if right < len(self.heap):
                if self.heap[right] > self.heap[i]:
                    largest = right
            
            self.heap[largest], self.heap[i] = self.heap[i], self.heap[largest]
            return largest
    
    def __down_heap(self, i : int):
        curr = i
        while True:
            next = self.__largest_swap(curr)
            if next == curr:
                break
            else:
                curr = next
            
    
    def __heafify(self, i : int):
        stack = [i]
        while len(stack) > 0:
            parent = stack.pop()
            self.__largest_swap(parent)
            
            left = self.__lchild(parent)
            if left < len(self.heap):
                stack.append(left)

            right = self.__rchild(parent)
            if right < len(self.heap):
                stack.append(right)
                            
    def insert(elem):
        self.heap.append(elem)
        self.__up_heap(len(self.heap)-1)
    
    def pull():
        self.heap[0], self.heap[-1] = self.heap[-1], self.heap[0]
        value = self.heap.pop()
        self.__down_heap(0)
```

###

####

peek insert delete
