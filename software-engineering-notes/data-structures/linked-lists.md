# Linked Lists

A linked list is a linear data structure where elements (nodes) are connected via pointers. Each node contains data and a reference to the next node.

## Types

- **Singly Linked List**: Each node points to the next node
- **Doubly Linked List**: Nodes have pointers to both next and previous
- **Circular Linked List**: Last node points back to the first

## Key Characteristics

- Dynamic size (no pre-allocation needed)
- Efficient insertions/deletions at known positions: O(1)
- No random access (must traverse): O(n)
- Extra memory for storing pointers

## Code Example

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = new_node

    def display(self):
        current = self.head
        while current:
            print(current.data, end=" -> ")
            current = current.next
```

## When to Use

- Frequent insertions/deletions at arbitrary positions
- Unknown or variable data size
- Implementing stacks, queues, or graphs
- When memory allocation flexibility is needed
