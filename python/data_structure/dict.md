# Python 字典常用操作

## 目录
1. [创建字典](#创建字典)
2. [访问字典中的值](#访问字典中的值)
3. [添加或更新键值对](#添加或更新键值对)
4. [删除键值对](#删除键值对)
5. [检查键是否存在](#检查键是否存在)
6. [获取字典的键、值或键值对](#获取字典的键值或键值对)
7. [遍历字典](#遍历字典)
8. [字典合并](#字典合并)
9. [字典推导式](#字典推导式)
10. [获取字典的长度](#获取字典的长度)
11. [复制字典](#复制字典)
12. [默认值处理](#默认值处理)
13. [字典排序](#字典排序)
14. [字典与 JSON 转换](#字典与-json-转换)

---

## 创建字典
- 使用 `{}` 创建空字典。
- 使用 `{'key': value}` 创建带初始值的字典。
- 使用 `dict()` 构造函数创建字典。
```
# 空字典
my_dict = {}

# 带初始值的字典
my_dict = {'name': 'Alice', 'age': 25}

# 使用 dict() 构造函数
my_dict = dict(name='Alice', age=25)
```
---

## 访问字典中的值
- 通过键访问值：`dict[key]`。
- 使用 `get()` 方法访问值，避免键不存在时抛出异常。
```
# 通过键访问值
name = my_dict['name']

# 使用 get() 方法，避免键不存在时抛出异常
age = my_dict.get('age')
```
---

## 添加或更新键值对
- 添加新键值对：`dict[key] = value`。
- 更新已有键的值：`dict[key] = new_value`。
```
# 添加新键值对
my_dict['city'] = 'New York'

# 更新已有键的值
my_dict['age'] = 26
```
---

## 删除键值对
- 使用 `del` 语句删除键值对。
- 使用 `pop()` 方法删除并返回指定键的值。
- 使用 `popitem()` 方法删除并返回最后一个键值对。
- 使用 `clear()` 方法清空字典。
```
# 使用 del 语句
del my_dict['city']

# 使用 pop() 方法，返回被删除的值
age = my_dict.pop('age')

# 使用 popitem() 方法，删除并返回最后一个键值对
key, value = my_dict.popitem()

# 清空字典
my_dict.clear()
```
---

## 检查键是否存在
- 使用 `in` 关键字检查键是否存在。
```
if 'name' in my_dict:
    print("Name exists in the dictionary")
```
---

## 获取字典的键、值或键值对
- 使用 `keys()` 方法获取所有键。
- 使用 `values()` 方法获取所有值。
- 使用 `items()` 方法获取所有键值对。
```
# 获取所有键
keys = my_dict.keys()

# 获取所有值
values = my_dict.values()

# 获取所有键值对
items = my_dict.items()
```
---

## 遍历字典
- 遍历键：`for key in dict`。
- 遍历键值对：`for key, value in dict.items()`。
```
# 遍历键
for key in my_dict:
    print(key)

# 遍历键值对
for key, value in my_dict.items():
    print(f"{key}: {value}")
```
---

## 字典合并
- 使用 `update()` 方法合并字典。
- 使用 `**` 操作符合并字典（Python 3.5+）。
```
# 使用 update() 方法
dict1 = {'a': 1, 'b': 2}
dict2 = {'b': 3, 'c': 4}
dict1.update(dict2)  # dict1 现在是 {'a': 1, 'b': 3, 'c': 4}

# 使用 ** 操作符（Python 3.5+）
merged_dict = {**dict1, **dict2}
```
---

## 字典推导式
- 使用字典推导式创建字典。
```
# 创建一个字典，键为数字，值为其平方
squares = {x: x**2 for x in range(5)}
```
---

## 获取字典的长度
- 使用 `len()` 函数获取字典的长度。
```
length = len(my_dict)
```
---

## 复制字典
- 使用 `copy()` 方法进行浅拷贝。
- 使用 `copy.deepcopy()` 进行深拷贝。
```
# 浅拷贝
new_dict = my_dict.copy()

# 深拷贝
import copy
new_dict = copy.deepcopy(my_dict)
```
---

## 默认值处理
- 使用 `setdefault()` 方法设置默认值。
```
# 使用 setdefault() 方法
my_dict.setdefault('gender', 'unknown')  # 如果 'gender' 不存在，则设置为 'unknown'
```
---

## 字典排序
- 按键排序：使用 `sorted()` 函数。
- 按值排序：使用 `sorted()` 函数结合 `lambda` 表达式。
```
# 按键排序
sorted_dict = {k: my_dict[k] for k in sorted(my_dict)}

# 按值排序
sorted_dict = {k: v for k, v in sorted(my_dict.items(), key=lambda item: item[1])}
```
---

## 字典与 JSON 转换
- 使用 `json.dumps()` 将字典转换为 JSON 字符串。
- 使用 `json.loads()` 将 JSON 字符串转换为字典。
```
import json

# 字典转 JSON 字符串
json_str = json.dumps(my_dict)

# JSON 字符串转字典
my_dict = json.loads(json_str)
```
