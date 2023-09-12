# Queue Data Structure

A **queue** is an important data structure in computer science that manages data according to the principle of **First-In-First-Out (FIFO)**. A queue is similar to the concept of waiting in line, where new data is added at the rear end, and data is removed from the front end. Due to this characteristic, queues find applications in various domains.

>#### An example picture of a FIFO process:
>
><img width="500" src = "https://upload.wikimedia.org/wikipedia/commons/d/d3/Fifo_queue.png"/>

## Queue Concept

1. **Enqueue**: Enqueue is the operation of adding data to the queue, which occurs at the rear end of the queue.
2. **Dequeue**: Dequeue is the operation of removing data from the queue, which takes place at the front end of the queue.
3. **Front**: Front points to the data at the front of the queue.
4. **Rear**: Rear points to the data at the rear of the queue.
5. **isEmpty**: isEmpty is a function or condition used to check if the queue is empty.

## Types of Queues

1. **Standard Queue**: This is the most common type of queue where data is processed in the order it arrives.
   ```python
   class Queue:
    def __init__(self):
        self.items = []

    def enqueue(self, item):
        self.items.append(item)

    def dequeue(self):
        if not self.is_empty():
            return self.items.pop(0)

    def is_empty(self):
        return len(self.items) == 0
   ```
2. **Priority Queue**: Priority queues assign a priority to each data element, and elements with higher priority are processed first.
   ```python
   import heapq
  
   class PriorityQueue:
      def __init__(self):
          self.elements = []
  
      def enqueue(self, item, priority):
          heapq.heappush(self.elements, (priority, item))
  
      def dequeue(self):
          if not self.is_empty():
              return heapq.heappop(self.elements)[1]
  
      def is_empty(self):
          return len(self.elements) == 0
   ```
3. **Circular Queue**: Similar to a standard queue but with the front and rear connected, allowing data to circulate within the structure.
    ```python
    class CircularQueue:
        def __init__(self, size):
            self.size = size
            self.queue = [None] * size
            self.front = self.rear = -1
    
        def enqueue(self, item):
            if (self.rear + 1) % self.size == self.front:
                print("Queue is full")
            elif self.front == -1:
                self.front = self.rear = 0
                self.queue[self.rear] = item
            else:
                self.rear = (self.rear + 1) % self.size
                self.queue[self.rear] = item
    
        def dequeue(self):
            if self.front == -1:
                print("Queue is empty")
            elif self.front == self.rear:
                temp = self.queue[self.front]
                self.front = self.rear = -1
                return temp
            else:
                temp = self.queue[self.front]
                self.front = (self.front + 1) % self.size
                return temp
    
        def is_empty(self):
            return self.front == -1
    ```
4. **Deque (Double-ended Queue)**: A queue that allows insertion and removal of data from both ends.
   ```python
   from collections import deque

   class Deque:
    def __init__(self):
        self.items = deque()

    def enqueue_front(self, item):
        self.items.appendleft(item)

    def enqueue_rear(self, item):
        self.items.append(item)

    def dequeue_front(self):
        if not self.is_empty():
            return self.items.popleft()

    def dequeue_rear(self):
        if not self.is_empty():
            return self.items.pop()

    def is_empty(self):
        return len(self.items) == 0
    ```
