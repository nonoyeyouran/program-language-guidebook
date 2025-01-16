# Python collections 模块常用操作详解

## 目录
1. [collections 模块简介](#collections-模块简介)
2. [Counter](#counter)
3. [defaultdict](#defaultdict)
4. [deque](#deque)
5. [namedtuple](#namedtuple)
6. [OrderedDict](#ordereddict)
7. [ChainMap](#chainmap)
8. [总结](#总结)

---

## collections 模块简介
`collections` 是 Python 标准库中的一个模块，提供了许多有用的数据结构，用于替代 Python 内置的数据类型（如 `list`、`dict` 等）。常用数据结构包括：
- `Counter`：计数器，用于统计元素出现的次数。
- `defaultdict`：带默认值的字典。
- `deque`：双端队列，支持高效的头尾操作。
- `namedtuple`：命名元组，为元组的每个字段命名。
- `OrderedDict`：有序字典，记录键值对的插入顺序。
- `ChainMap`：将多个字典合并为一个逻辑上的字典。

---

## Counter
`Counter` 是一个字典的子类，用于统计可哈希对象的出现次数。

### 常用操作
- 创建 `Counter`：
  `from collections import Counter`
  `c = Counter(['apple', 'banana', 'apple', 'orange'])`
  `print(c)`  # 输出: Counter({'apple': 2, 'banana': 1, 'orange': 1})
- 获取元素出现次数：
  `print(c['apple'])`  # 输出: 2
- 获取出现次数最多的元素：
  `print(c.most_common(1))`  # 输出: [('apple', 2)]
- 更新计数器：
  `c.update(['apple', 'banana'])`
  `print(c)`  # 输出: Counter({'apple': 3, 'banana': 2, 'orange': 1})

---

## defaultdict
`defaultdict` 是一个字典的子类，为字典中的键提供默认值。

### 常用操作
- 创建 `defaultdict`：
  `from collections import defaultdict`
  `d = defaultdict(int)`  # 默认值为 0
  `d['apple'] += 1`
  `print(d['apple'])`  # 输出: 1
  `print(d['banana'])`  # 输出: 0
- 使用自定义默认值：
  `d = defaultdict(lambda: 'unknown')`
  `print(d['apple'])`  # 输出: unknown

---

## deque
`deque` 是一个双端队列，支持高效的头尾操作。

### 常用操作
- 创建 `deque`：
  `from collections import deque`
  `d = deque([1, 2, 3])`
- 添加元素：
  `d.append(4)`  # 添加到尾部
  `d.appendleft(0)`  # 添加到头部
  `print(d)`  # 输出: deque([0, 1, 2, 3, 4])
- 删除元素：
  `d.pop()`  # 删除尾部元素
  `d.popleft()`  # 删除头部元素
  `print(d)`  # 输出: deque([1, 2, 3])
- 旋转队列：
  `d.rotate(1)`  # 向右旋转 1 步
  `print(d)`  # 输出: deque([3, 1, 2])

---

## namedtuple
`namedtuple` 是一个工厂函数，用于创建具有命名字段的元组。

### 常用操作
- 创建 `namedtuple`：
  `from collections import namedtuple`
  `Point = namedtuple('Point', ['x', 'y'])`
  `p = Point(1, 2)`
  `print(p.x, p.y)`  # 输出: 1 2
- 访问字段：
  `print(p[0], p[1])`  # 输出: 1 2
- 转换为字典：
  `print(p._asdict())`  # 输出: {'x': 1, 'y': 2}

---

## OrderedDict
`OrderedDict` 是一个字典的子类，记录键值对的插入顺序。

### 常用操作
- 创建 `OrderedDict`：
  `from collections import OrderedDict`
  `d = OrderedDict()`
  `d['apple'] = 1`
  `d['banana'] = 2`
  `print(d)`  # 输出: OrderedDict([('apple', 1), ('banana', 2)])
- 保持插入顺序：
  `d['orange'] = 3`
  `print(d)`  # 输出: OrderedDict([('apple', 1), ('banana', 2), ('orange', 3)])
- 删除并返回最后插入的键值对：
  `d.popitem(last=True)`  # 输出: ('orange', 3)

---

## ChainMap
`ChainMap` 将多个字典合并为一个逻辑上的字典，查找时按顺序搜索。

### 常用操作
- 创建 `ChainMap`：
  `from collections import ChainMap`
  `dict1 = {'apple': 1, 'banana': 2}`
  `dict2 = {'orange': 3}`
  `cm = ChainMap(dict1, dict2)`
  `print(cm['apple'])`  # 输出: 1
  `print(cm['orange'])`  # 输出: 3
- 添加新字典：
  `dict3 = {'grape': 4}`
  `cm = cm.new_child(dict3)`
  `print(cm['grape'])`  # 输出: 4

---

## 总结
- `collections` 模块提供了多种高效的数据结构，适用于不同的场景。
- `Counter` 用于统计元素出现次数，`defaultdict` 提供默认值，`deque` 支持高效的头尾操作。
- `namedtuple` 为元组字段命名，`OrderedDict` 记录插入顺序，`ChainMap` 合并多个字典。
- 掌握这些数据结构可以显著提高代码的效率和可读性。

---

通过以上内容，您可以快速掌握 Python 中 `collections` 模块的常用操作，并应用于实际开发中。
