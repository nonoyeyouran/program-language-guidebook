# Python Pandas 模块全面操作详解

## 目录
1. [Pandas 简介](#pandas-简介)
2. [数据结构](#数据结构)
   - [Series](#series)
   - [DataFrame](#dataframe)
3. [数据读取与写入](#数据读取与写入)
   - [读取数据](#读取数据)
   - [写入数据](#写入数据)
4. [数据清洗](#数据清洗)
   - [处理缺失值](#处理缺失值)
   - [处理重复值](#处理重复值)
   - [数据类型转换](#数据类型转换)
   - [重命名列](#重命名列)
   - [重置索引](#重置索引)
5. [数据筛选](#数据筛选)
   - [条件筛选](#条件筛选)
   - [列选择](#列选择)
   - [排序](#排序)
   - [抽样](#抽样)
6. [数据统计与分析](#数据统计与分析)
   - [基本统计](#基本统计)
   - [分组统计](#分组统计)
   - [数据透视表](#数据透视表)
7. [数据合并与分组](#数据合并与分组)
   - [数据合并](#数据合并)
   - [数据连接](#数据连接)
   - [数据分组](#数据分组)
8. [时间序列处理](#时间序列处理)
   - [创建时间序列](#创建时间序列)
   - [时间序列操作](#时间序列操作)
9. [数据透视与映射](#数据透视与映射)
   - [数据透视表](#数据透视表)
   - [数据映射](#数据映射)
10. [数据堆叠与解堆叠](#数据堆叠与解堆叠)
    - [数据堆叠](#数据堆叠)
    - [数据解堆叠](#数据解堆叠)
11. [其他高级操作](#其他高级操作)
    - [数据分箱](#数据分箱)
    - [数据排序与排名](#数据排序与排名)
    - [数据迭代](#数据迭代)
12. [总结](#总结)

---

## Pandas 简介
Pandas 是 Python 中用于数据处理和分析的核心库，提供了高效的数据结构（如 `Series` 和 `DataFrame`）以及丰富的数据操作功能。它是数据科学和数据分析领域的重要工具。

---

## 数据结构

### Series
- **Series** 是一维带标签的数组，可以存储任意类型的数据。
- 创建 Series：
  import pandas as pd
  s = pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'])
- 访问数据：
  print(s['a'])  # 输出: 1
- 基本操作：
  - 索引：`s.index`
  - 值：`s.values`
  - 描述统计：`s.describe()`
  - 唯一值：`s.unique()`
  - 值计数：`s.value_counts()`

### DataFrame
- **DataFrame** 是二维带标签的数据结构，类似于电子表格或 SQL 表。
- 创建 DataFrame：
  data = {'name': ['Alice', 'Bob', 'Charlie'], 'age': [25, 30, 35]}
  df = pd.DataFrame(data)
- 访问数据：
  - 按列访问：`df['name']`
  - 按行访问：`df.loc[0]`
  - 按位置访问：`df.iloc[0]`
- 基本操作：
  - 列名：`df.columns`
  - 索引：`df.index`
  - 描述统计：`df.describe()`
  - 转置：`df.T`

---

## 数据读取与写入

### 读取数据
- 从 CSV 文件读取：
  df = pd.read_csv('data.csv')
- 从 Excel 文件读取：
  df = pd.read_excel('data.xlsx')
- 从 SQL 数据库读取：
  import sqlite3
  conn = sqlite3.connect('database.db')
  df = pd.read_sql_query('SELECT * FROM table_name', conn)
- 从 JSON 文件读取：
  df = pd.read_json('data.json')
- 从 HTML 表格读取：
  df = pd.read_html('https://example.com/table.html')[0]

### 写入数据
- 写入 CSV 文件：
  df.to_csv('output.csv', index=False)
- 写入 Excel 文件：
  df.to_excel('output.xlsx', index=False)
- 写入 SQL 数据库：
  df.to_sql('table_name', conn, if_exists='replace', index=False)
- 写入 JSON 文件：
  df.to_json('output.json')

---

## 数据清洗

### 处理缺失值
- 检查缺失值：
  print(df.isnull())
- 删除缺失值：
  df.dropna(inplace=True)
- 填充缺失值：
  df.fillna(0, inplace=True)  # 用 0 填充缺失值

### 处理重复值
- 检查重复值：
  print(df.duplicated())
- 删除重复值：
  df.drop_duplicates(inplace=True)

### 数据类型转换
- 转换数据类型：
  df['age'] = df['age'].astype(float)

### 重命名列
- 重命名列：
  df.rename(columns={'old_name': 'new_name'}, inplace=True)

### 重置索引
- 重置索引：
  df.reset_index(drop=True, inplace=True)

---

## 数据筛选

### 条件筛选
- 筛选满足条件的行：
  filtered_df = df[df['age'] > 30]

### 列选择
- 选择特定列：
  selected_columns = df[['name', 'age']]

### 排序
- 按列排序：
  sorted_df = df.sort_values(by='age', ascending=False)

### 抽样
- 随机抽样：
  sampled_df = df.sample(n=2)  # 随机抽取 2 行

---

## 数据统计与分析

### 基本统计
- 描述性统计：
  print(df.describe())
- 求和：
  print(df['age'].sum())
- 平均值：
  print(df['age'].mean())

### 分组统计
- 按列分组并统计：
  grouped_df = df.groupby('name').mean()

### 数据透视表
- 创建数据透视表：
  pivot_df = df.pivot_table(values='age', index='name', aggfunc='mean')

---

## 数据合并与分组

### 数据合并
- 合并两个 DataFrame：
  df1 = pd.DataFrame({'A': ['A0', 'A1'], 'B': ['B0', 'B1']})
  df2 = pd.DataFrame({'A': ['A2', 'A3'], 'B': ['B2', 'B3']})
  merged_df = pd.concat([df1, df2])

### 数据连接
- 按列连接：
  df1 = pd.DataFrame({'key': ['K0', 'K1'], 'A': ['A0', 'A1']})
  df2 = pd.DataFrame({'key': ['K0', 'K1'], 'B': ['B0', 'B1']})
  joined_df = pd.merge(df1, df2, on='key')

### 数据分组
- 按列分组并聚合：
  grouped_df = df.groupby('name').agg({'age': ['mean', 'max']})

---

## 时间序列处理

### 创建时间序列
- 创建时间序列：
  dates = pd.date_range('20230101', periods=6)
  df = pd.DataFrame({'date': dates, 'value': [1, 2, 3, 4, 5, 6]})

### 时间序列操作
- 按时间筛选：
  filtered_df = df[df['date'] > '20230103']
- 重采样：
  resampled_df = df.resample('D', on='date').mean()

---

## 数据透视与映射

### 数据透视表
- 创建数据透视表：
  pivot_df = df.pivot_table(values='age', index='name', columns='gender', aggfunc='mean')

### 数据映射
- 使用 `map()` 函数：
  df['category'] = df['age'].map(lambda x: '儿童' if x < 14 else '成人')

---

## 数据堆叠与解堆叠

### 数据堆叠
- 堆叠：
  stacked_df = df.stack()

### 数据解堆叠
- 解堆叠：
  unstacked_df = df.unstack()

---

## 其他高级操作

### 数据分箱
- 将连续数据分箱：
  df['age_group'] = pd.cut(df['age'], bins=[0, 14, 18, 60, 100], labels=['儿童', '青少年', '成人', '老人'])

### 数据排序与排名
- 排序：
  sorted_df = df.sort_values(by='age')
- 排名：
  df['rank'] = df['age'].rank()

### 数据迭代
- 按行迭代：
  for index, row in df.iterrows():
      print(row['name'], row['age'])

---

## 总结
- Pandas 提供了强大的数据处理和分析功能，适用于数据清洗、筛选、统计、合并、分组、时间序列处理等任务。
- 常用操作包括数据读取与写入、缺失值处理、条件筛选、分组统计、数据透视表、时间序列处理等。
- 掌握 Pandas 的基本用法可以显著提高数据处理的效率。

---

通过以上内容，您可以全面掌握 Python 中 `pandas` 模块的所有操作，并应用于实际开发中。
