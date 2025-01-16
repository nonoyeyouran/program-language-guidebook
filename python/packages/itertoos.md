# Python itertools 模块常用操作详解

## 目录
1. [itertools 模块简介](#itertools-模块简介)
2. [无限迭代器](#无限迭代器)
   - [count](#count)
   - [cycle](#cycle)
   - [repeat](#repeat)
3. [组合迭代器](#组合迭代器)
   - [product](#product)
   - [permutations](#permutations)
   - [combinations](#combinations)
   - [combinations_with_replacement](#combinations_with_replacement)
4. [分组迭代器](#分组迭代器)
   - [groupby](#groupby)
5. [其他实用工具](#其他实用工具)
   - [chain](#chain)
   - [zip_longest](#zip_longest)
   - [tee](#tee)
6. [总结](#总结)

---

## itertools 模块简介
`itertools` 是 Python 标准库中的一个模块，提供了许多高效的迭代器工具，用于处理迭代器和序列。它可以帮助我们简化代码并提高性能。

---

## 无限迭代器

### count
- **功能**：生成从指定值开始的无限递增序列。
- **示例**：
  `from itertools import count`
  `for i in count(10):`
      `if i > 15: break`
      `print(i)`  # 输出: 10, 11, 12, 13, 14, 15

### cycle
- **功能**：无限循环遍历可迭代对象。
- **示例**：
  `from itertools import cycle`
  `c = cycle('ABC')`
  `for i in range(5):`
      `print(next(c))`  # 输出: A, B, C, A, B

### repeat
- **功能**：重复生成指定值的无限序列。
- **示例**：
  `from itertools import repeat`
  `r = repeat(10, 3)`  # 重复 10 三次
  `print(list(r))`  # 输出: [10, 10, 10]

---

## 组合迭代器

### product
- **功能**：计算多个可迭代对象的笛卡尔积。
- **示例**：
  `from itertools import product`
  `p = product('AB', '12')`
  `print(list(p))`  # 输出: [('A', '1'), ('A', '2'), ('B', '1'), ('B', '2')]

### permutations
- **功能**：生成可迭代对象的所有排列。
- **示例**：
  `from itertools import permutations`
  `p = permutations('ABC', 2)`  # 生成长度为 2 的排列
  `print(list(p))`  # 输出: [('A', 'B'), ('A', 'C'), ('B', 'A'), ('B', 'C'), ('C', 'A'), ('C', 'B')]

### combinations
- **功能**：生成可迭代对象的所有组合。
- **示例**：
  `from itertools import combinations`
  `c = combinations('ABC', 2)`  # 生成长度为 2 的组合
  `print(list(c))`  # 输出: [('A', 'B'), ('A', 'C'), ('B', 'C')]

### combinations_with_replacement
- **功能**：生成可迭代对象的所有组合（允许元素重复）。
- **示例**：
  `from itertools import combinations_with_replacement`
  `c = combinations_with_replacement('ABC', 2)`
  `print(list(c))`  # 输出: [('A', 'A'), ('A', 'B'), ('A', 'C'), ('B', 'B'), ('B', 'C'), ('C', 'C')]

---

## 分组迭代器

### groupby
- **功能**：根据键函数对可迭代对象进行分组。
- **示例**：
  `from itertools import groupby`
  `data = [('A', 1), ('A', 2), ('B', 3), ('B', 4)]`
  `for key, group in groupby(data, lambda x: x[0]):`
      `print(key, list(group))`
  # 输出:
  # A [('A', 1), ('A', 2)]
  # B [('B', 3), ('B', 4)]

---

## 其他实用工具

### chain
- **功能**：将多个可迭代对象连接成一个迭代器。
- **示例**：
  `from itertools import chain`
  `c = chain('ABC', '123')`
  `print(list(c))`  # 输出: ['A', 'B', 'C', '1', '2', '3']

### zip_longest
- **功能**：将多个可迭代对象打包成一个迭代器，长度不足时用指定值填充。
- **示例**：
  `from itertools import zip_longest`
  `z = zip_longest('ABC', '12', fillvalue='X')`
  `print(list(z))`  # 输出: [('A', '1'), ('B', '2'), ('C', 'X')]

### tee
- **功能**：将一个迭代器拆分为多个独立的迭代器。
- **示例**：
  `from itertools import tee`
  `t1, t2 = tee('ABC')`
  `print(list(t1))`  # 输出: ['A', 'B', 'C']
  `print(list(t2))`  # 输出: ['A', 'B', 'C']

---

## 总结
- `itertools` 模块提供了丰富的迭代器工具，适用于处理复杂的迭代任务。
- 常用工具包括无限迭代器（`count`、`cycle`、`repeat`）、组合迭代器（`product`、`permutations`、`combinations`）、分组迭代器（`groupby`）以及其他实用工具（`chain`、`zip_longest`、`tee`）。
- 掌握这些工具可以显著提高代码的效率和可读性。

---

通过以上内容，您可以快速掌握 Python 中 `itertools` 模块的常用操作，并应用于实际开发中。
