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
        self.heap = []
        for elem in arr:
            self.insert(elem)
    
    def __parent(self, i : int) -> int:
        return (i - 1) // 2
    
    def __lchild(self, p : int) -> int:
        return p * 2 + 1
        
    def __rchild(self, p : int) -> int:
        return p * 2 + 2
    
    def __up_heap(self, i : int):
        while i > 0:
            p = self.__parent(i)
            if self.heap[i] > self.heap[p]:
                self.heap[i], self.heap[p] = self.heap[p], self.heap[i]
                i = p
            else:
                break
    
    def __down_heap(self, i : int):
        while True:
            largest = i
            left = self.__lchild(i)
            right = self.__rchild(i)
            if left < len(self.heap):
                if self.heap[left] > self.heap[largest]:
                    largest = left
    
            if right < len(self.heap):
                if self.heap[right] > self.heap[largest]:
                    largest = right
            
            self.heap[largest], self.heap[i] = self.heap[i], self.heap[largest]
            
            if largest == i:
                break
            else:
                i = largest
                
    def insert(self, elem):
        self.heap.append(elem)
        self.__up_heap(len(self.heap)-1)
    
    def pull(self):
        self.heap[0], self.heap[-1] = self.heap[-1], self.heap[0]
        value = self.heap.pop()
        self.__down_heap(0)
        return value

```

###

####

peek insert delete
