---
type: 核心概念
tags:
  - Concept
domain: 数据结构
---
## 一句话定位
C 语言标准库提供的内存管理、内存操作、字符串操作与辅助工具函数是实现数据结构的基础设施——malloc/calloc/realloc/free 负责动态分配与释放，memset/memcpy/memmove/memcmp 负责内存块的初始化、复制与比较，strlen/strcpy/strcmp/strstr/strtok 等负责字符串的求长、复制、比较、查找与分割，sizeof/assert/NULL 提供编译期计算与运行时安全检查。

## 它解决什么问题？
C 语言本身不提供自动垃圾回收或动态数组等高级抽象，数据结构（顺序表、链表、树、图等）的底层实现依赖这些函数手动管理内存的生命周期、初始化存储空间以及进行安全的字节级数据搬运。

## 主要概念
malloc，calloc，realloc，free，memset，memcpy，memmove，memcmp，strlen，strcpy，strncpy，strcat，strncat，strcmp，strncmp，strstr，strchr，strrchr，strtok，sprintf，snprintf，sizeof，assert，NULL，offsetof，内存泄漏，悬空指针，内存重叠

> **缩写对照**
> - **malloc**：memory allocation，内存分配
> - **calloc**：contiguous allocation，连续内存分配并清零
> - **realloc**：re-allocation，重新分配内存
> - **free**：释放动态内存
> - **memcpy**：memory copy，内存复制（不处理重叠）
> - **memmove**：memory move，内存移动（处理重叠）
> - **memset**：memory set，内存设置
> - **memcmp**：memory compare，内存比较
> - **NULL**：null pointer，空指针常量
> - **strlen**：string length，字符串长度
> - **strcpy**：string copy，字符串复制
> - **strncpy**：string copy with n，限长字符串复制
> - **strcat**：string concatenate，字符串拼接
> - **strncat**：string concatenate with n，限长字符串拼接
> - **strcmp**：string compare，字符串比较
> - **strncmp**：string compare with n，限长字符串比较
> - **strstr**：string string，查找子串
> - **strchr**：string character，查找字符（正向）
> - **strrchr**：string reverse character，查找字符（反向）
> - **strtok**：string token，字符串分割
> - **sprintf**：string printf，格式化输出到字符串
> - **snprintf**：safe string printf，安全格式化输出到字符串

## 概念解析
#### 动态内存分配
- **malloc**：`void *malloc(size_t size)`，分配 size 字节的未初始化内存，返回指向该内存块的指针。
	- 返回值：成功则返回 void 指针（可强制转换为任意类型），失败返回 NULL。
	- 分配的内存内容**未初始化**（含随机垃圾值），需手动初始化（如通过 memset 或逐元素赋值）。
	- 数据结构中使用：`LNode *p = (LNode *)malloc(sizeof(LNode))` 创建链表新结点。
- **calloc**：`void *calloc(size_t num, size_t size)`，分配 num 个 size 字节的连续内存块并**全部初始化为 0**，返回首地址指针。
	- 与 malloc 的关键区别：自动清零，适合需要零初始化的数组或结构体。
	- 数据结构中使用：`int *arr = (int *)calloc(n, sizeof(int))` 创建零初始化动态数组。
- **realloc**：`void *realloc(void *ptr, size_t new_size)`，调整先前分配的内存块大小至 new_size，必要时复制旧数据到新位置。
	- 扩展时新增部分内容**未初始化**，缩小则丢弃尾部数据（释放的不可再访问）。
	- 返回值：新地址可能与原地址不同，切勿直接用原指针接收（原地址被释放后原指针变成悬空指针）。
	- 安全用法：`int *new_ptr = (int *)realloc(old_ptr, new_size); if (new_ptr) old_ptr = new_ptr;`。
	- 数据结构中使用：动态顺序表容量不足时扩容，`realloc(L.data, L.capacity * 2 * sizeof(ElemType))`。
- **free**：`void free(void *ptr)`，释放之前由 malloc/calloc/realloc 分配的内存块，归还给堆。
	- 释放后 ptr 变为**悬空指针**，应立即置为 NULL 以防止误用。
	- 重复释放同一块内存（double free）或释放非动态分配的内存均属未定义行为。
	- 内存泄漏：动态分配的内存未及时释放，程序持续运行会耗尽堆空间。
#### 内存操作函数（`<string.h>`）
- **memset**：`void *memset(void *s, int c, size_t n)`，将 s 指向的内存块前 n 字节填充为 c（实际取 c 的低 8 位），返回 s。
	- 最常见的用途是将结构体或数组清零：`memset(&node, 0, sizeof(Node))`。
	- 注意：按字节填充，对非 char 数组初始化可能产生意外值（如 `memset(arr, 1, n * sizeof(int))` 不会将 int 设为 1）。
- **memcpy**：`void *memcpy(void *dest, const void *src, size_t n)`，从 src 复制 n 字节到 dest，返回 dest。
	- 源和目标地址**不可重叠**，重叠时行为未定义，速度比 memmove 稍快。
	- 数据结构中使用：顺序表插入元素时移动数据块 `memcpy(L.data + i, L.data + i - 1, (L.length - i + 1) * sizeof(ElemType))`。
- **memmove**：`void *memmove(void *dest, const void *src, size_t n)`，从 src 复制 n 字节到 dest，返回 dest。
	- 与 memcpy 的区别在于**处理重叠区域**：memmove 通过临时拷贝保证源和目标重叠时仍能正确复制。
	- 不确定是否重叠时优先用 memmove 替代 memcpy（性能差异可忽略）。
- **memcmp**：`int memcmp(const void *s1, const void *s2, size_t n)`，比较 s1 和 s2 前 n 字节，按字节无符号比较。
	- 返回值：相等返回 0；s1 < s2 返回负数；s1 > s2 返回正数。
	- 数据结构中使用：`memcmp(&a, &b, sizeof(Node)) == 0` 比较两个结构体是否逐字节相等（注意结构体填充字节未初始化时可能误判）。
#### 字符串操作函数（`<string.h>`）
- **strlen**：`size_t strlen(const char *s)`，返回 s 指向的字符串长度（不含结尾 `\0`），遍历直到遇到 `\0`，时间复杂度 $O(n)$。
	- 反复调用同一字符串应缓存结果，数据结构中串的定长/堆分配存储的求长操作如 `StrLength(S)` 常封装为 `return strlen(S.ch)`。
- **strcpy / strncpy**：`char *strcpy(char *dest, const char *src)` 将 src（含 `\0`）复制到 dest；`char *strncpy(char *dest, const char *src, size_t n)` 最多复制 n 个字符。
	- strcpy 不检查目的缓冲区大小，可能造成缓冲区溢出，优先用 strncpy 或 snprintf。
	- strncpy 在 src 长度 >= n 时不追加 `\0`，调用方需手动补 `\0`。
	- 数据结构中使用：串的赋值操作 `StrAssign(&T, chars)` 底层通过 strcpy 实现。
- **strcat / strncat**：`char *strcat(char *dest, const char *src)` 将 src 追加到 dest 末尾；`char *strncat(char *dest, const char *src, size_t n)` 最多追加 n 个字符。
	- strcat 不检查目的缓冲区剩余空间，存在溢出风险；strncat 会在追加后自动添加 `\0`。
	- 数据结构中使用：串的连接操作 `Concat(&T, S1, S2)` 底层调用 strcat 或 memcpy 实现。
- **strcmp / strncmp**：`int strcmp(const char *s1, const char *s2)` 按字典序逐字符比较到 `\0` 为止；`int strncmp(const char *s1, const char *s2, size_t n)` 最多比较前 n 个字符。
	- 返回值：相等返回 0；s1 < s2 返回负数；s1 > s2 返回正数。
	- 数据结构中使用：串的比较操作 `StrCompare(S, T)` 直接封装为 `return strcmp(S.ch, T.ch)`；在 BST 或散列表中也常作为键的比较函数传入。
- **strstr**：`char *strstr(const char *haystack, const char *needle)`，在 haystack 中查找 needle 第一次出现的位置，返回指针；未找到返回 NULL。
	- 朴素实现 $O(nm)$，glibc 等实现使用更优算法（如 Two-Way）。
	- 数据结构中使用：串的子串定位操作 `Index(S, T)` 的底层实现。
- **strchr / strrchr**：`char *strchr(const char *s, int c)` 在 s 中正向查找字符 c 第一次出现的位置；`strrchr` 反向查找最后一次出现的位置。找到返回指针，未找到返回 NULL。
	- 常用于解析分隔符，如 `strchr(s, ',')` 定位逗号分隔符。
- **strtok**：`char *strtok(char *str, const char *delim)`，按分隔符集合 delim 切割字符串，首次调用传入 str，后续传入 NULL 继续分割，返回下一个 token 的指针；无更多 token 时返回 NULL。
	- 内部维护静态指针，不可重入且线程不安全（多线程场景用 `strtok_r`）。
	- 每次调用会修改原字符串（将分隔符替换为 `\0`），原字符串必须可写。
	- 数据结构中使用：解析输入表达式（如 CSV、命令行参数）时按分隔符提取 token。
- **sprintf / snprintf**：`int sprintf(char *buf, const char *fmt, ...)` 按格式写入 buf；`int snprintf(char *buf, size_t size, const char *fmt, ...)` 最多写入 size-1 个字符并追加 `\0`。
	- sprintf 不检查缓冲区大小，存在溢出风险，优先使用 snprintf。
	- 若返回值 >= size 说明输出被截断（snprintf 可据此计算实际需要的大小）。
	- 数据结构中使用：串的格式化赋值操作，如 `snprintf(S.ch, MaxSize, "%d+%d=%d", a, b, a + b)`。

#### 辅助工具
- **sizeof**：编译时一元运算符，返回类型或变量的字节大小，类型为 `size_t`。
	- 对数组名使用时返回整个数组的字节大小（而非指针大小），可用于计算数组元素个数：`sizeof(arr) / sizeof(arr[0])`。
	- 数据结构中使用：写通用代码时通过 `sizeof(ElemType)` 保持类型无关性。
- **assert**：`assert(expr)`，若 expr 为假则向 stderr 输出错误信息并终止程序（定义在 `<assert.h>`）。
	- 仅在编译未定义 `NDEBUG` 宏时生效，发布版本可通过定义 `NDEBUG` 移除断言。
	- 数据结构中使用：在插入、删除等操作前校验参数合法性，如 `assert(i >= 1 && i <= L.length + 1)`。
- **NULL**：空指针常量，在 C 中定义为 `(void *)0` 或 `0`，在 C++ 中定义为 `0`，表示指针不指向任何有效对象。
	- 对 NULL 解引用是未定义行为（通常导致段错误），解引用前必须判空。
	- 动态分配失败时 malloc 等返回 NULL，调用前应检查：`if (!p) { /* 分配失败处理 */ }`。
- **offsetof**：`offsetof(type, member)`，返回结构体成员在结构体中的字节偏移量（定义在 `<stddef.h>`）。
	- 数据结构中使用：手动管理内存布局或实现泛型数据结构时计算成员偏移。

## 相关概念问题
