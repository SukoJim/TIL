# Stack

A stack is a data structure that temporarily stores data, following the Last-In-First-Out (LIFO) principle. Stacks are commonly used in various algorithms and problems, including function calls, parenthesis matching, and postfix notation evaluation.

## Basic Concepts

- **Push**: The operation of adding an item to the top of the stack is called "push." New elements are pushed onto the stack, becoming the new top element.

- **Pop**: The operation of removing and returning the top item from the stack is called "pop." The most recently added item (the top of the stack) is removed.

- **Top**: The "top" of the stack refers to the element currently at the top. You can access the top element without removing it.

- **IsEmpty**: A stack can be checked for emptiness using the "isEmpty" operation. If the stack has no elements, it is considered empty.


## Implementation in Python
In Python, you can implement a stack using the list data structure. Here's a simple example of a stack implementation:
```
class Stack:
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        if not self.is_empty():
            return self.items.pop()

    def peek(self):
        if not self.is_empty():
            return self.items[-1]

    def is_empty(self):
        return len(self.items) == 0

    def size(self):
        return len(self.items)
```
### When using python built-in library you can implement like this : 
```
from collections import deque

stack = deque()

stack.append(1)      # Push
stack.append(2)
stack.pop()           # Pop
stack.append(3)

print(stack)          # Output: deque([1, 3])
```