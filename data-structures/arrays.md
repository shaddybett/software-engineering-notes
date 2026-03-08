# Arrays

An array is a contiguous block of memory that stores elements of the same type. It provides constant-time access to elements via their index.

## Key Characteristics

- **Fixed size** (in most languages) or dynamic (like Python lists, JS arrays)
- **Zero-indexed** access
- **O(1)** access time by index
- **O(n)** insertion/deletion (shifting required)

## Common Operations

| Operation | Time Complexity |
| --------- | --------------- |
| Access    | O(1)            |
| Search    | O(n)            |
| Insert    | O(n)            |
| Delete    | O(n)            |
| Append    | O(1) amortized  |

## Code Examples

```python
# Python array operations
numbers = [1, 2, 3, 4, 5]

# Access by index
print(numbers[2])  # Output: 3

# Append element
numbers.append(6)

# Insert at position
numbers.insert(0, 0)  # [0, 1, 2, 3, 4, 5, 6]

# Remove element
numbers.pop()  # Removes last element
```

## Best Practices

- Use arrays when you need fast index-based access
- Prefer linked lists for frequent insertions/deletions in the middle
- Pre-allocate size if known to avoid resizing overhead
- Use array slicing for efficient subarray operations
