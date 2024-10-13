**如何产生一个图的语法，容易犯错的点**
```python
graph = [[]]*n   # 该语法是对同一个list索引产生n个拷贝
graph = [[] for _ in range(n)]  # 这个语法是产生n个不同的list
```
