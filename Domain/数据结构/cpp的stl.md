---
type: 核心概念
tags:
  - Concept
domain: 数据结构
---
## 一句话定位
C++ STL 容器是泛型数据结构模板，封装了常见的数据组织方式与算法，提供统一接口以高效管理元素集合。

## 它解决什么问题？
免去手写基础数据结构（如动态数组、链表、哈希表）的重复劳动，通过统一的迭代器-算法-容器三层架构实现数据与操作解耦。

## 主要概念

顺序容器、关联容器、无序关联容器、容器适配器、迭代器

> **缩写对照**
> - **STL**：Standard Template Library，标准模板库
> - **RAII**：Resource Acquisition Is Initialization，资源获取即初始化

## 概念解析

### typedef
c语言中`struct node` 才是完整的结构体类型名，`node` 本身只是结构体标签（tag），不是类型别名，因此如果要声明变量时要用 `struct node n;`。
使用typedef可以给他取别名，例如：
```c
typedef struct node{
    int data;
    struct node *next;
} *p,Node;//其中p代表struct node *，Node代表struct node 
```

### 容器总览

- **分类**：顺序容器（元素位置由插入顺序决定）、关联容器（元素位置由键的排序规则决定）、无序关联容器（元素位置由哈希值决定）、容器适配器（基于底层容器封装受限接口）。
  - 顺序容器：`vector` `deque` `list` `forward_list` `array` `string`
  - 关联容器：`set` `multiset` `map` `multimap`（底层红黑树，$O(\log n)$）
  - 无序关联容器：`unordered_set` `unordered_multiset` `unordered_map` `unordered_multimap`（底层哈希表，均摊 $O(1)$）
  - 容器适配器：`stack` `queue` `priority_queue`

### 通用成员函数（几乎所有容器共有）

#### 迭代器
- `begin()` / `end()`：起始/尾后迭代器
- `cbegin()` / `cend()`：const 迭代器
- `rbegin()` / `rend()`：反向迭代器

#### 容量
- `size()`：元素个数，$O(1)$
- `empty()`：判空，$O(1)$
- `max_size()`：理论最大容量

#### 修改
- `clear()`：清空所有元素
- `insert(iter, val)` / `emplace(iter, args...)`：在迭代器位置插入/原地构造
- `erase(iter)` / `erase(first, last)`：删除元素
- `swap(other)`：交换两容器内容，$O(1)$

### vector（动态数组）

- **定义**：连续内存的动态数组，支持随机访问，尾部插入/删除均摊 $O(1)$，中间插入/删除 $O(n)$。
  - 容量以倍数（通常2倍）增长，扩容时复制或移动旧元素
  - 元素连续存储，`data()` 可获取原始指针
  - 

#### 主要成员
- **构造函数**：v(n,0)，对象v全部为0
- **随机访问**：`operator[]` 不检查越界，`at(i)` 检查越界并抛 `std::out_of_range`
- **首尾**：`front()` / `back()` 返回首/尾元素引用
- **尾部修改**：`push_back(val)` / `emplace_back(args...)` / `pop_back()`
- **容量**：`capacity()` 当前分配容量，`reserve(n)` 预留容量，`shrink_to_fit()` 释放多余容量
- **大小**：`resize(n)` 调整元素个数，多余的元素值初始化或丢弃

### deque（双端队列）

- **定义**：由分段连续内存块组成的双端队列，两端插入/删除 $O(1)$，随机访问 $O(1)$（常数比 vector 稍大），中间插入/删除 $O(n)$。
  - 扩容时无需复制旧元素，只需分配新内存块
  - 支持 `operator[]` 和 `at()`

#### 主要成员
- 除与 vector 类似的 `push_back` / `pop_back` 等，额外有：
- `push_front(val)` / `emplace_front(args...)` / `pop_front()`：头部插入/删除

### list（双向链表）

- **定义**：双向链表，任意位置插入/删除 $O(1)$，不支持随机访问，遍历 $O(n)$。
  - 迭代器不会因插入/删除其他元素而失效（被删除元素本身除外）
  - 自带 `sort()` `merge()` `reverse()` 等成员函数（比泛型算法更高效或专属）

#### 主要成员
- `push_back(val)` / `emplace_back(args...)` / `pop_back()`
- `push_front(val)` / `emplace_front(args...)` / `pop_front()`
- `splice(iter, other, [first, last])`：将另一 list 的元素接合到 iter 前，$O(1)$
- `remove(val)`：删除所有等于 val 的元素
- `remove_if(pred)`：按谓词删除
- `unique()`：删除相邻重复元素
- `merge(other)`：合并两个已排序 list，other 被清空
- `sort()`：链表专用排序，$O(n \log n)$
- `reverse()`：逆置链表

### forward_list（单向链表）

- **定义**：单向链表，只有 `forward` 方向指针，内存开销比 list 更小，仅支持头部操作和 `insert_after` / `erase_after`。
  - 无 `size()`（部分实现提供了但为 $O(n)$），无 `push_back` / `pop_back`（无尾前驱指针）

#### 主要成员
- `push_front(val)` / `emplace_front(args...)` / `pop_front()`
- `insert_after(iter, val)` / `emplace_after(iter, args...)` / `erase_after(iter)`
- `before_begin()` / `cbefore_begin()`：返回首元素之前的迭代器（用于在头部之前插入）

### array（定长数组）

- **定义**：封装 C 风格定长数组，大小在编译期确定，零开销包装。
  - 与 C 数组不同，不会退化为指针（传递时保留大小信息）

#### 主要成员
- `operator[]` / `at(i)` / `front()` / `back()`
- `data()`：返回底层数组指针
- `fill(val)`：填充所有元素为 val
- `size()`：constexpr，编译期可知

### string（字符串）

- **定义**：`basic_string<char>` 的类型别名，本质是字符的动态数组，接口与 vector 类似并额外提供字符串专属操作。
  - 小字符串优化（SSO, Small String Optimization），短字符串不分配堆内存

#### 主要成员（仅列与 vector 差异部分）
- `c_str()` / `data()`：返回 C 风格字符串（以 `\0` 结尾）
- `substr(pos, count)`：截取子串，$O(n)$
- `find(str)` / `rfind(str)`：正向/反向查找
- `compare(other)`：字典序比较
- `append(str)` / `operator+=`：追加
- `replace(pos, count, str)`：替换子串
- `stoi` / `stod` / `to_string` 等全局函数做数值互转

### set / multiset（集合 / 多重集合）

- **定义**：基于红黑树的有序集合，元素自动排序，set 元素唯一、multiset 允许重复，插入/删除/查找 $O(\log n)$。
  - 默认 `std::less` 排序，可自定义比较器
  - 元素不可修改（修改会破坏排序），只能删后重插

#### 主要成员
- `insert(val)` / `emplace(args...)`：插入，返回 `pair<iterator, bool>`（bool 表示是否插入成功，multiset 只返回 iterator）
- `find(val)`：查找，返回迭代器或 `end()`
- `count(val)`：计数，set 至多返回1，$O(\log n)$；multiset 可能返回多个，$O(\log n + k)$
- `lower_bound(val)` / `upper_bound(val)`：下界/上界
- `equal_range(val)`：返回 `pair<iterator, iterator>` 等于 val 的范围
- `erase(iter)` / `erase(val)`：删除指定元素或指定值
- `extract(val)` / `extract(iter)`：C++17，从树中解出节点（node handle），可修改或移入其他 set

### map / multimap（映射 / 多重映射）

- **定义**：基于红黑树的有序键值对容器，key 唯一（map）或可重复（multimap），按 key 排序，插入/删除/查找 $O(\log n)$。
  - 元素类型为 `pair<const Key, T>`，key 不可修改
  - `operator[]` 仅在 map 中存在（key 不存在时值初始化插入），multimap 无此操作

#### 主要成员
- `operator[](key)`：若 key 不存在则插入 `{key, T{}}` 后返回 value 引用（仅 map）
- `at(key)`：带越界检查，key 不存在抛 `std::out_of_range`（仅 map）
- `insert({key, val})` / `emplace(key, val)`：插入键值对
- `find(key)` `count(key)` `lower_bound(key)` `upper_bound(key)` `equal_range(key)` 同 set
- `try_emplace(key, args...)`：C++17，key 不存在时才构造 value，避免不必要的临时对象
- `insert_or_assign(key, val)`：C++17，key 存在则赋值，不存在则插入

### unordered_set / unordered_multiset / unordered_map / unordered_multimap

- **定义**：基于哈希表的无序容器，均摊插入/删除/查找 $O(1)$，最坏 $O(n)$，元素无顺序保证。
  - 需提供哈希函数 `std::hash<Key>` 和等值比较 `std::equal_to<Key>`
  - 桶（bucket）相关接口：`bucket_count()` `load_factor()` `rehash(n)` `reserve(n)`
  - 元素是无序的，迭代顺序取决于哈希值和桶分布

#### 主要成员
- 对外接口与对应有序容器基本一致（`insert` `find` `erase` `count` 等）
- 无 `lower_bound` / `upper_bound`（因为无序）
- `load_factor()`：平均每桶元素数
- `max_load_factor()`：触发 rehash 的阈值
- `rehash(n)`：设置桶数至少为 n
- `reserve(n)`：预留空间使至少容纳 n 个元素而不 rehash

### stack（栈）

- **定义**：基于 deque（默认）适配的 LIFO 结构，仅暴露栈顶操作。
  - 可指定底层容器（`stack<int, vector<int>>`），要求容器支持 `back()` `push_back()` `pop_back()`

#### 主要成员
- `push(val)` / `emplace(args...)`：压栈
- `pop()`：弹栈，不返回值
- `top()`：返回栈顶引用
- `size()` / `empty()`

### queue（队列）

- **定义**：基于 deque（默认）适配的 FIFO 结构，队尾入队头出。
  - 可指定底层容器（需支持 `back()` `push_back()` `front()` `pop_front()`）

#### 主要成员
- `push(val)` / `emplace(args...)`：入队
- `pop()`：出队，不返回值
- `front()` / `back()`：队头/队尾引用
- `size()` / `empty()`

### priority_queue（优先队列）

- **定义**：基于 vector（默认）适配的堆结构，默认大顶堆（`std::less` 得最大元素在堆顶），插入 $O(\log n)$，取堆顶 $O(1)$。
  - 可指定底层容器（需支持随机访问和 `push_back` `pop_back`）与比较器 `priority_queue<int, vector<int>, greater<int>>` 得小顶堆

#### 主要成员
- `push(val)` / `emplace(args...)`：插入
- `pop()`：移除堆顶，不返回值
- `top()`：返回堆顶引用
- `size()` / `empty()`

## 相关概念问题
