# Python 集合常用操作

## 目录
1. [创建集合](#创建集合)
2. [添加元素](#添加元素)
3. [删除元素](#删除元素)
4. [集合运算](#集合运算)
5. [集合比较](#集合比较)
6. [集合遍历](#集合遍历)
7. [集合长度](#集合长度)
8. [集合复制](#集合复制)
9. [集合与列表转换](#集合与列表转换)
10. [集合推导式](#集合推导式)

---

## 创建集合
- 使用 `{}` 创建集合（注意：空集合必须使用 `set()`）。
- 使用 `set()` 函数创建集合。
```
# 创建集合
my_set = {1, 2, 3}
empty_set = set()
```
---

## 添加元素
- 使用 `add()` 方法添加单个元素。
- 使用 `update()` 方法添加多个元素。
```
my_set = {1, 2, 3}
my_set.add(4)           # 添加单个元素
my_set.update([5, 6])   # 添加多个元素
```
---

## 删除元素
- 使用 `remove()` 方法删除指定元素（元素不存在时抛出异常）。
- 使用 `discard()` 方法删除指定元素（元素不存在时不抛出异常）。
- 使用 `pop()` 方法随机删除并返回一个元素。
- 使用 `clear()` 方法清空集合。
```
my_set = {1, 2, 3, 4, 5}
my_set.remove(3)        # 删除元素 3
my_set.discard(10)      # 尝试删除不存在的元素，不会报错
popped_element = my_set.pop()  # 随机删除并返回一个元素
my_set.clear()          # 清空集合
```
---

## 集合运算
- 并集：使用 `union()` 方法或 `|` 运算符。
- 交集：使用 `intersection()` 方法或 `&` 运算符。
- 差集：使用 `difference()` 方法或 `-` 运算符。
- 对称差集：使用 `symmetric_difference()` 方法或 `^` 运算符。
```
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# 并集
union_set = set1.union(set2)        # 或 set1 | set2

# 交集
intersection_set = set1.intersection(set2)  # 或 set1 & set2

# 差集
difference_set = set1.difference(set2)      # 或 set1 - set2

# 对称差集
symmetric_difference_set = set1.symmetric_difference(set2)  # 或 set1 ^ set2
```
---

## 集合比较
- 子集检查：使用 `issubset()` 方法或 `<=` 运算符。
- 真子集检查：使用 `<` 运算符。
- 超集检查：使用 `issuperset()` 方法或 `>=` 运算符。
- 真超集检查：使用 `>` 运算符。
- 不相交检查：使用 `isdisjoint()` 方法。
```
set1 = {1, 2, 3}
set2 = {1, 2, 3, 4, 5}

# 子集检查
is_subset = set1.issubset(set2)     # 或 set1 <= set2

# 真子集检查
is_proper_subset = set1 < set2

# 超集检查
is_superset = set2.issuperset(set1)  # 或 set2 >= set1

# 真超集检查
is_proper_superset = set2 > set1

# 不相交检查
is_disjoint = set1.isdisjoint({4, 5, 6})
```
---

## 集合遍历
- 使用 `for` 循环遍历集合中的元素。
```
my_set = {1, 2, 3}
for item in my_set:
    print(item)
```
---

## 集合长度
- 使用 `len()` 函数获取集合的长度。
```
my_set = {1, 2, 3}
length = len(my_set)
```
---

## 集合复制
- 使用 `copy()` 方法复制集合。
```
my_set = {1, 2, 3}
new_set = my_set.copy()
```
---

## 集合与列表转换
- 使用 `set()` 函数将列表转换为集合。
- 使用 `list()` 函数将集合转换为列表。
```
# 列表转集合
my_list = [1, 2, 2, 3]
my_set = set(my_list)

# 集合转列表
new_list = list(my_set)
```
---

## 集合推导式
- 使用集合推导式创建集合。
```
# 创建一个包含平方数的集合
squares = {x**2 for x in range(5)}
```
