**如何产生一个图的语法，容易犯错的点**
```python
graph = [[]]*n   # 该语法是对同一个list索引产生n个拷贝
graph = [[] for _ in range(n)]  # 这个语法是产生n个不同的list
```

**矩阵四边搜索简洁的写法**
```python
# 当前点（x,y)
for x2, y2 in ((x+1, y), (x-1, y), (x, y+1), (x, y-1)): # 依次搜索一个点的四个邻节点
if 0<=x1<m and 0<=y2<n: # 边界点的判断
```
**创建数组，特别是DP，应该用list**
```python
dp=[0 for _ in range(n)]
```
