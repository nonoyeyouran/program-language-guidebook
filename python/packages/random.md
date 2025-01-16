# Python random 模块常用操作详解

## 目录
1. [random 模块简介](#random-模块简介)
2. [生成随机数](#生成随机数)
   - [random()](#random)
   - [uniform()](#uniform)
   - [randint()](#randint)
   - [randrange()](#randrange)
3. [随机选择](#随机选择)
   - [choice()](#choice)
   - [choices()](#choices)
   - [sample()](#sample)
   - [shuffle()](#shuffle)
4. [随机种子](#随机种子)
   - [seed()](#seed)
5. [总结](#总结)

---

## random 模块简介
`random` 是 Python 标准库中的一个模块，用于生成伪随机数。它提供了多种函数，支持生成随机数、随机选择、随机打乱等操作。

---

## 生成随机数

### random()
- **功能**：生成一个 `[0.0, 1.0)` 范围内的随机浮点数。
- **示例**：
  ```
  import random
  print(random.random())
  ```
### uniform()
- **功能**：生成指定范围内的随机浮点数。
- **示例**：
  ```
  import random
  print(random.uniform(1.0, 10.0))
  ```
### randint()
- **功能**：生成指定范围内的随机整数（包含两端点）。
- **示例**：
  ```
  import random
  print(random.randint(1, 10))
  ```
### randrange()
- **功能**：生成指定范围内的随机整数（不包含结束值）。
- **示例**：
  ```
  import random
  print(random.randrange(1, 10))
  ```
---

## 随机选择

### choice()
- **功能**：从序列中随机选择一个元素。
- **示例**：
  ```
  import random
  fruits = ['apple', 'banana', 'orange']
  print(random.choice(fruits))
  ```
### choices()
- **功能**：从序列中随机选择多个元素（允许重复）。
- **示例**：
  ```
  import random
  fruits = ['apple', 'banana', 'orange']
  print(random.choices(fruits, k=2))
  ```
### sample()
- **功能**：从序列中随机选择多个元素（不允许重复）。
- **示例**：
  ```
  import random
  fruits = ['apple', 'banana', 'orange']
  print(random.sample(fruits, k=2))
  ```
### shuffle()
- **功能**：随机打乱序列的顺序。
- **示例**：
  ```
  import random
  fruits = ['apple', 'banana', 'orange']
  random.shuffle(fruits)
  print(fruits)
  ```
---

## 随机种子

### seed()
- **功能**：设置随机种子，使随机结果可重复。
- **示例**：
  ```
  import random
  random.seed(42)
  print(random.random())
  ```
---

## 总结
- `random` 模块提供了丰富的随机数生成和随机选择功能。
- 常用函数包括 `random()`、`uniform()`、`randint()`、`randrange()` 等用于生成随机数，以及 `choice()`、`choices()`、`sample()`、`shuffle()` 等用于随机选择。
- 通过 `seed()` 可以设置随机种子，使随机结果可重复。

---

通过以上内容，您可以快速掌握 Python 中 `random` 模块的常用操作，并应用于实际开发中。
