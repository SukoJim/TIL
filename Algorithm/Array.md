# Arrays

An **array** is one of the most fundamental and important data structures in computer science. An array is a data structure that stores elements of the same data type in a fixed-size contiguous memory space. Each element can be accessed using an index, starting from 0. Arrays support fast access and retrieval of data and serve as the foundation for various algorithms and data structures.

## Key Characteristics of Arrays

1. **Fixed Size**: Arrays have a fixed size when created, and their size cannot be changed.

2. **Uniform Data Type**: Arrays store elements of the same data type. For example, an integer array stores only integer values.

3. **Contiguous Memory**: Elements of an array are stored in contiguous memory locations, which makes memory management efficient.

4. **Index-Based Access**: Each element in the array has a unique index, allowing for fast access to elements.

## Example of Using Arrays (in Python)

```python
# Creating an array
arr = [1, 2, 3, 4, 5]

# Checking the length of the array
length = len(arr)  # 5

# Accessing elements in the array
element = arr[2]  # 3

# Modifying elements in the array
arr[1] = 6  # [1, 6, 3, 4, 5]

# Iterating through the array
for i in arr:
    print(i)

# Adding elements to the array (in Python, it acts like a dynamic array)
arr.append(7)  # [1, 6, 3, 4, 5, 7]

# Removing elements from the array
arr.pop(3)  # [1, 6, 3, 5, 7]

# Initializing an empty array
arr = []

# Slicing an array to get a subset
subset = arr[1:4]  # Gets elements from index 1 to 3 (inclusive)
