# Hash Tables

A hash table (dictionary/map) stores key-value pairs with average O(1) lookup, insertion, and deletion using a hash function.

## How It Works

1. A **hash function** converts the key into an array index
2. The value is stored at that index
3. **Collisions** (same index for different keys) are handled via chaining or open addressing

## Time Complexity

| Operation | Average | Worst Case |
| --------- | ------- | ---------- |
| Search    | O(1)    | O(n)       |
| Insert    | O(1)    | O(n)       |
| Delete    | O(1)    | O(n)       |

## Code Examples

```python
# Python dictionary (built-in hash table)
user = {
    "id": 1,
    "name": "Alice",
    "email": "alice@example.com"
}

# Access
print(user["name"])  # Alice

# Check existence
if "email" in user:
    print("Email exists")

# Safe access with default
age = user.get("age", 0)  # Returns 0 if key missing

# Iterate
for key, value in user.items():
    print(f"{key}: {value}")
```

```javascript
// JavaScript object and Map
const user = { id: 1, name: "Alice" };

// ES6 Map for non-string keys
const cache = new Map();
cache.set("key1", "value1");
cache.get("key1"); // "value1"
```

## Use Cases

- Caching and memoization
- Database indexing
- Counting frequencies
- Storing configuration/settings

## Best Practices

- Choose good hash functions to minimize collisions
- Use appropriate load factor (typically 0.7)
- In Python, prefer `dict` over manual implementations
- Use `defaultdict` or `Counter` for specialized needs
