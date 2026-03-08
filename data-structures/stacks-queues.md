# Stacks and Queues

Two fundamental abstract data types that manage collections with specific access patterns.

## Stack (LIFO - Last In, First Out)

Elements are added and removed from the same end (top).

### Operations

- `push(item)`: Add to top - O(1)
- `pop()`: Remove from top - O(1)
- `peek()`: View top element - O(1)

```python
# Stack implementation using list
stack = []
stack.append(1)  # push
stack.append(2)
stack.pop()      # returns 2

# Or use collections.deque for better performance
from collections import deque
stack = deque()
```

### Use Cases

- Undo/redo operations
- Browser back button
- Function call stack
- Expression parsing

## Queue (FIFO - First In, First Out)

Elements are added at the rear and removed from the front.

### Operations

- `enqueue(item)`: Add to rear - O(1)
- `dequeue()`: Remove from front - O(1)
- `front()`: View first element - O(1)

```python
from collections import deque

queue = deque()
queue.append(1)     # enqueue
queue.append(2)
queue.popleft()     # dequeue, returns 1
```

### Use Cases

- Task scheduling
- Print job spooling
- BFS traversal
- Message queues

## Best Practices

- Use `collections.deque` in Python (O(1) for both ends)
- Avoid using list for queues (pop(0) is O(n))
- Consider `queue.Queue` for thread-safe operations
