# 容器
## 序列性容器
### vector

> 头文件：`<vector>`  
> 说明：`vector` 是**连续存储**的动态数组；随机访问 O(1)，尾部插入/删除均摊 O(1)，中间插入/删除通常 O(n)。

#### 1) 构造 / 析构 / 赋值

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`vector()`|—|无|默认构造，创建空容器。|
|`explicit vector(const Allocator& alloc)`|—|`alloc`|使用指定分配器构造空容器。|
|`explicit vector(size_type count, const Allocator& alloc = Allocator())`|—|`count`, `alloc`|构造含 `count` 个**值初始化**元素（如 `T{}`）的 vector。|
|`vector(size_type count, const T& value, const Allocator& alloc = Allocator())`|—|`count`, `value`, `alloc`|构造含 `count` 个 `value` 拷贝的 vector。|
|`template<class InputIt> vector(InputIt first, InputIt last, const Allocator& alloc = Allocator())`|—|`[first,last)`, `alloc`|范围构造，用迭代器区间元素初始化。|
|`vector(const vector& other)`|—|`other`|拷贝构造。|
|`vector(const vector& other, const Allocator& alloc)`|—|`other`, `alloc`|用指定分配器拷贝构造。|
|`vector(vector&& other) noexcept`|—|`other`|移动构造（C++11）。|
|`vector(vector&& other, const Allocator& alloc)`|—|`other`, `alloc`|用指定分配器移动构造（C++11）。|
|`vector(std::initializer_list<T> init, const Allocator& alloc = Allocator())`|—|`init`, `alloc`|初始化列表构造（C++11）。|
|`~vector()`|—|无|析构，释放资源。|
|`vector& operator=(const vector& other)`|`vector&`|`other`|拷贝赋值。|
|`vector& operator=(vector&& other) noexcept(/*依实现与Allocator*/)`|`vector&`|`other`|移动赋值（C++11）。|
|`vector& operator=(std::initializer_list<T> ilist)`|`vector&`|`ilist`|初始化列表赋值（C++11）。|
|`void assign(size_type count, const T& value)`|`void`|`count`, `value`|用 `count` 个 `value` 替换全部内容。|
|`template<class InputIt> void assign(InputIt first, InputIt last)`|`void`|`[first,last)`|用范围元素替换全部内容。|
|`void assign(std::initializer_list<T> ilist)`|`void`|`ilist`|用初始化列表替换全部内容（C++11）。|
|`allocator_type get_allocator() const`|`allocator_type`|无|返回当前使用的分配器副本。|

---

#### 2) 迭代器相关

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`iterator begin() noexcept`|`iterator`|无|指向首元素。|
|`const_iterator begin() const noexcept`|`const_iterator`|无|指向首元素（只读）。|
|`const_iterator cbegin() const noexcept`|`const_iterator`|无|指向首元素（只读，C++11）。|
|`iterator end() noexcept`|`iterator`|无|指向尾后位置。|
|`const_iterator end() const noexcept`|`const_iterator`|无|指向尾后位置（只读）。|
|`const_iterator cend() const noexcept`|`const_iterator`|无|指向尾后位置（只读，C++11）。|
|`reverse_iterator rbegin() noexcept`|`reverse_iterator`|无|反向首（对应最后一个元素）。|
|`const_reverse_iterator rbegin() const noexcept`|`const_reverse_iterator`|无|反向首（只读）。|
|`const_reverse_iterator crbegin() const noexcept`|`const_reverse_iterator`|无|反向首（只读，C++11）。|
|`reverse_iterator rend() noexcept`|`reverse_iterator`|无|反向尾后。|
|`const_reverse_iterator rend() const noexcept`|`const_reverse_iterator`|无|反向尾后（只读）。|
|`const_reverse_iterator crend() const noexcept`|`const_reverse_iterator`|无|反向尾后（只读，C++11）。|

---

#### 3) 容量相关

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`bool empty() const noexcept`|`bool`|无|是否为空。|
|`size_type size() const noexcept`|`size_type`|无|元素个数。|
|`size_type max_size() const noexcept`|`size_type`|无|理论最大可容纳元素数（受分配器/系统限制）。|
|`void reserve(size_type new_cap)`|`void`|`new_cap`|预留容量到至少 `new_cap`，减少扩容次数。|
|`size_type capacity() const noexcept`|`size_type`|无|当前已分配容量（≥ size）。|
|`void shrink_to_fit()`|`void`|无|请求收缩容量以匹配 `size()`（非强制，C++11）。|

---

#### 4) 元素访问

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`reference operator[](size_type pos)`|`reference`|`pos`|下标访问，不做越界检查。|
|`const_reference operator[](size_type pos) const`|`const_reference`|`pos`|只读下标访问，不检查越界。|
|`reference at(size_type pos)`|`reference`|`pos`|带越界检查；越界抛 `std::out_of_range`。|
|`const_reference at(size_type pos) const`|`const_reference`|`pos`|只读版本，越界抛异常。|
|`reference front()`|`reference`|无|首元素引用（空容器调用为未定义行为）。|
|`const_reference front() const`|`const_reference`|无|首元素只读引用。|
|`reference back()`|`reference`|无|尾元素引用（空容器调用为未定义行为）。|
|`const_reference back() const`|`const_reference`|无|尾元素只读引用。|
|`T* data() noexcept`|`T*`|无|指向底层连续数组首地址（可能为 `nullptr` 仅当空且实现如此）。|
|`const T* data() const noexcept`|`const T*`|无|只读指针版本。|

---

#### 5) 修改器（增删改）

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`void clear() noexcept`|`void`|无|清空所有元素，`capacity()` 通常不变。|
|`iterator insert(const_iterator pos, const T& value)`|`iterator`|`pos`, `value`|在 `pos` 前插入 `value`（拷贝）。返回新元素迭代器。|
|`iterator insert(const_iterator pos, T&& value)`|`iterator`|`pos`, `value`|在 `pos` 前插入 `value`（移动，C++11）。|
|`iterator insert(const_iterator pos, size_type count, const T& value)`|`iterator`|`pos`, `count`, `value`|在 `pos` 前插入 `count` 个 `value`。返回第一个插入元素迭代器。|
|`template<class InputIt> iterator insert(const_iterator pos, InputIt first, InputIt last)`|`iterator`|`pos`, `[first,last)`|在 `pos` 前插入范围元素。|
|`iterator insert(const_iterator pos, std::initializer_list<T> ilist)`|`iterator`|`pos`, `ilist`|在 `pos` 前插入初始化列表（C++11）。|
|`template<class... Args> iterator emplace(const_iterator pos, Args&&... args)`|`iterator`|`pos`, `args...`|在 `pos` 前**原地构造**元素（C++11）。|
|`template<class... Args> reference emplace_back(Args&&... args)`|`reference`|`args...`|在尾部原地构造元素（C++11；C++17 起返回引用；更早标准为 `void`）。|
|`void push_back(const T& value)`|`void`|`value`|尾部插入（拷贝）。|
|`void push_back(T&& value)`|`void`|`value`|尾部插入（移动，C++11）。|
|`void pop_back()`|`void`|无|删除尾元素（空容器调用为未定义行为）。|
|`iterator erase(const_iterator pos)`|`iterator`|`pos`|删除 `pos` 处元素，返回指向“被删元素之后”的迭代器。|
|`iterator erase(const_iterator first, const_iterator last)`|`iterator`|`[first,last)`|删除范围元素，返回 `last` 原位置对应的新迭代器。|
|`void resize(size_type count)`|`void`|`count`|调整大小：变大追加值初始化元素；变小截断尾部。|
|`void resize(size_type count, const T& value)`|`void`|`count`, `value`|变大时用 `value` 填充新增元素。|
|`void swap(vector& other) noexcept`|`void`|`other`|与 `other` 交换内容（通常 O(1)）。|

---

#### 6) 非成员函数 / 操作符（与 `vector` 配套）

| 函数（签名）                                                                                         |       返回值类型 | 参数           | 解释                                    |
| ---------------------------------------------------------------------------------------------- | ----------: | ------------ | ------------------------------------- |
| `bool operator==(const vector& a, const vector& b)`                                            |      `bool` | `a`, `b`     | 按元素比较是否相等。                            |
| `bool operator!=(const vector& a, const vector& b)`                                            |      `bool` | `a`, `b`     | 不等（C++20 前常显式提供；C++20 起可由 `==` 推导）。   |
| `bool operator<(const vector& a, const vector& b)`                                             |      `bool` | `a`, `b`     | 词典序比较（C++20 前常用）。                     |
| `bool operator<=(...) / >(...) / >=(...)`                                                      |      `bool` | `a`, `b`     | 词典序比较相关操作符（C++20 前常用）。                |
| `std::strong_ordering operator<=>(const vector& a, const vector& b)`                           |        比较类别 | `a`, `b`     | 三路比较（C++20；实际返回类型依 `T` 的比较能力而定）。      |
| `void swap(vector& a, vector& b) noexcept`                                                     |      `void` | `a`, `b`     | 交换两个 vector（等价于成员 `swap` 的 ADL 版本）。   |
| `template<class T, class Alloc, class U> size_type erase(vector<T,Alloc>& c, const U& value)`  | `size_type` | `c`, `value` | 删除所有等于 `value` 的元素，返回删除数量（C++20，非成员）。 |
| `template<class T, class Alloc, class Pred> size_type erase_if(vector<T,Alloc>& c, Pred pred)` | `size_type` | `c`, `pred`  | 删除所有满足谓词的元素，返回删除数量（C++20，非成员）。        |

#### deque
> 头文件：`<deque>`  
> 说明：`deque` 是**分段连续**存储的双端队列；支持随机访问 O(1)，两端插入/删除均摊 O(1)，中间插入/删除通常 O(n)。与 `vector` 不同，`deque` 的数据通常**不保证物理连续**。

##### 1) 构造 / 析构 / 赋值

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`deque()`|—|无|默认构造，创建空容器。|
|`explicit deque(const Allocator& alloc)`|—|`alloc`|使用指定分配器构造空容器。|
|`explicit deque(size_type count, const Allocator& alloc = Allocator())`|—|`count`, `alloc`|构造含 `count` 个**值初始化**元素（如 `T{}`）的 deque。|
|`deque(size_type count, const T& value, const Allocator& alloc = Allocator())`|—|`count`, `value`, `alloc`|构造含 `count` 个 `value` 拷贝的 deque。|
|`template<class InputIt> deque(InputIt first, InputIt last, const Allocator& alloc = Allocator())`|—|`[first,last)`, `alloc`|范围构造，用迭代器区间元素初始化。|
|`deque(const deque& other)`|—|`other`|拷贝构造。|
|`deque(const deque& other, const Allocator& alloc)`|—|`other`, `alloc`|用指定分配器拷贝构造。|
|`deque(deque&& other) noexcept`|—|`other`|移动构造（C++11）。|
|`deque(deque&& other, const Allocator& alloc)`|—|`other`, `alloc`|用指定分配器移动构造（C++11）。|
|`deque(std::initializer_list<T> init, const Allocator& alloc = Allocator())`|—|`init`, `alloc`|初始化列表构造（C++11）。|
|`~deque()`|—|无|析构，释放资源。|
|`deque& operator=(const deque& other)`|`deque&`|`other`|拷贝赋值。|
|`deque& operator=(deque&& other) noexcept(/*依实现与Allocator*/)`|`deque&`|`other`|移动赋值（C++11）。|
|`deque& operator=(std::initializer_list<T> ilist)`|`deque&`|`ilist`|初始化列表赋值（C++11）。|
|`void assign(size_type count, const T& value)`|`void`|`count`, `value`|用 `count` 个 `value` 替换全部内容。|
|`template<class InputIt> void assign(InputIt first, InputIt last)`|`void`|`[first,last)`|用范围元素替换全部内容。|
|`void assign(std::initializer_list<T> ilist)`|`void`|`ilist`|用初始化列表替换全部内容（C++11）。|
|`allocator_type get_allocator() const`|`allocator_type`|无|返回当前使用的分配器副本。|

---

##### 2) 迭代器相关

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`iterator begin() noexcept`|`iterator`|无|指向首元素。|
|`const_iterator begin() const noexcept`|`const_iterator`|无|指向首元素（只读）。|
|`const_iterator cbegin() const noexcept`|`const_iterator`|无|指向首元素（只读，C++11）。|
|`iterator end() noexcept`|`iterator`|无|指向尾后位置。|
|`const_iterator end() const noexcept`|`const_iterator`|无|指向尾后位置（只读）。|
|`const_iterator cend() const noexcept`|`const_iterator`|无|指向尾后位置（只读，C++11）。|
|`reverse_iterator rbegin() noexcept`|`reverse_iterator`|无|反向首（对应最后一个元素）。|
|`const_reverse_iterator rbegin() const noexcept`|`const_reverse_iterator`|无|反向首（只读）。|
|`const_reverse_iterator crbegin() const noexcept`|`const_reverse_iterator`|无|反向首（只读，C++11）。|
|`reverse_iterator rend() noexcept`|`reverse_iterator`|无|反向尾后。|
|`const_reverse_iterator rend() const noexcept`|`const_reverse_iterator`|无|反向尾后（只读）。|
|`const_reverse_iterator crend() const noexcept`|`const_reverse_iterator`|无|反向尾后（只读，C++11）。|

---

##### 3) 容量相关

> `deque` 没有 `reserve()` / `capacity()`（这是 `vector` 的特性）。

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`bool empty() const noexcept`|`bool`|无|是否为空。|
|`size_type size() const noexcept`|`size_type`|无|元素个数。|
|`size_type max_size() const noexcept`|`size_type`|无|理论最大可容纳元素数（受分配器/系统限制）。|
|`void shrink_to_fit()`|`void`|无|请求收缩内部存储以减少占用（非强制，C++11）。|

---

##### 4) 元素访问

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`reference operator[](size_type pos)`|`reference`|`pos`|下标访问，不做越界检查。|
|`const_reference operator[](size_type pos) const`|`const_reference`|`pos`|只读下标访问，不检查越界。|
|`reference at(size_type pos)`|`reference`|`pos`|带越界检查；越界抛 `std::out_of_range`。|
|`const_reference at(size_type pos) const`|`const_reference`|`pos`|只读版本，越界抛异常。|
|`reference front()`|`reference`|无|首元素引用（空容器调用为未定义行为）。|
|`const_reference front() const`|`const_reference`|无|首元素只读引用。|
|`reference back()`|`reference`|无|尾元素引用（空容器调用为未定义行为）。|
|`const_reference back() const`|`const_reference`|无|尾元素只读引用。|

---

##### 5) 修改器（增删改）

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`void clear() noexcept`|`void`|无|清空所有元素。|
|`iterator insert(const_iterator pos, const T& value)`|`iterator`|`pos`, `value`|在 `pos` 前插入 `value`（拷贝）。返回新元素迭代器。|
|`iterator insert(const_iterator pos, T&& value)`|`iterator`|`pos`, `value`|在 `pos` 前插入 `value`（移动，C++11）。|
|`iterator insert(const_iterator pos, size_type count, const T& value)`|`iterator`|`pos`, `count`, `value`|在 `pos` 前插入 `count` 个 `value`。返回第一个插入元素迭代器。|
|`template<class InputIt> iterator insert(const_iterator pos, InputIt first, InputIt last)`|`iterator`|`pos`, `[first,last)`|在 `pos` 前插入范围元素。|
|`iterator insert(const_iterator pos, std::initializer_list<T> ilist)`|`iterator`|`pos`, `ilist`|在 `pos` 前插入初始化列表（C++11）。|
|`template<class... Args> iterator emplace(const_iterator pos, Args&&... args)`|`iterator`|`pos`, `args...`|在 `pos` 前原地构造元素（C++11）。|
|`template<class... Args> reference emplace_back(Args&&... args)`|`reference`|`args...`|尾部原地构造（C++17 起返回引用；更早标准为 `void`）。|
|`void push_back(const T& value)`|`void`|`value`|尾部插入（拷贝）。|
|`void push_back(T&& value)`|`void`|`value`|尾部插入（移动，C++11）。|
|`void pop_back()`|`void`|无|删除尾元素（空容器调用为未定义行为）。|
|`template<class... Args> reference emplace_front(Args&&... args)`|`reference`|`args...`|头部原地构造（C++11；C++17 起通常返回引用，早期可能为 `void` 以实现为准）。|
|`void push_front(const T& value)`|`void`|`value`|头部插入（拷贝）。|
|`void push_front(T&& value)`|`void`|`value`|头部插入（移动，C++11）。|
|`void pop_front()`|`void`|无|删除首元素（空容器调用为未定义行为）。|
|`iterator erase(const_iterator pos)`|`iterator`|`pos`|删除 `pos` 处元素，返回指向“被删元素之后”的迭代器。|
|`iterator erase(const_iterator first, const_iterator last)`|`iterator`|`[first,last)`|删除范围元素，返回 `last` 原位置对应的新迭代器。|
|`void resize(size_type count)`|`void`|`count`|调整大小：变大追加值初始化元素；变小截断尾部。|
|`void resize(size_type count, const T& value)`|`void`|`count`, `value`|变大时用 `value` 填充新增元素。|
|`void swap(deque& other) noexcept`|`void`|`other`|与 `other` 交换内容（通常 O(1)）。|

---

##### 6) 非成员函数 / 操作符（与 `deque` 配套）

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`bool operator==(const deque& a, const deque& b)`|`bool`|`a`, `b`|按元素比较是否相等。|
|`bool operator!=(const deque& a, const deque& b)`|`bool`|`a`, `b`|不等（C++20 前常显式提供；C++20 起可由 `==` 推导）。|
|`bool operator<(const deque& a, const deque& b)`|`bool`|`a`, `b`|词典序比较（C++20 前常用）。|
|`bool operator<=(...) / >(...) / >=(...)`|`bool`|`a`, `b`|词典序比较相关操作符（C++20 前常用）。|
|`auto operator<=>(const deque& a, const deque& b)`|比较类别|`a`, `b`|三路比较（C++20；返回类型依 `T` 的比较能力而定）。|
|`void swap(deque& a, deque& b) noexcept`|`void`|`a`, `b`|交换两个 deque（等价于成员 `swap` 的 ADL 版本）。|
|`template<class T, class Alloc, class U> size_type erase(deque<T,Alloc>& c, const U& value)`|`size_type`|`c`, `value`|删除所有等于 `value` 的元素，返回删除数量（C++20，非成员）。|
|`template<class T, class Alloc, class Pred> size_type erase_if(deque<T,Alloc>& c, Pred pred)`|`size_type`|`c`, `pred`|删除所有满足谓词的元素，返回删除数量（C++20，非成员）。|

### list

#### 1) 构造 / 析构 / 赋值

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`list()`|—|无|默认构造，创建空链表。|
|`explicit list(const Allocator& alloc)`|—|`alloc`|使用指定分配器构造空链表。|
|`explicit list(size_type count, const Allocator& alloc = Allocator())`|—|`count`, `alloc`|构造含 `count` 个**值初始化**元素的 list。|
|`list(size_type count, const T& value, const Allocator& alloc = Allocator())`|—|`count`, `value`, `alloc`|构造含 `count` 个 `value` 拷贝的 list。|
|`template<class InputIt> list(InputIt first, InputIt last, const Allocator& alloc = Allocator())`|—|`[first,last)`, `alloc`|范围构造，用迭代器区间元素初始化。|
|`list(const list& other)`|—|`other`|拷贝构造。|
|`list(list&& other) noexcept`|—|`other`|移动构造（C++11）。|
|`list(std::initializer_list<T> init, const Allocator& alloc = Allocator())`|—|`init`, `alloc`|初始化列表构造（C++11）。|
|`~list()`|—|无|析构，释放节点资源。|
|`list& operator=(const list& other)`|`list&`|`other`|拷贝赋值。|
|`list& operator=(list&& other) noexcept`|`list&`|`other`|移动赋值（C++11）。|
|`list& operator=(std::initializer_list<T> ilist)`|`list&`|`ilist`|初始化列表赋值（C++11）。|
|`void assign(size_type count, const T& value)`|`void`|`count`, `value`|用 `count` 个 `value` 替换全部内容。|
|`template<class InputIt> void assign(InputIt first, InputIt last)`|`void`|`[first,last)`|用范围元素替换全部内容。|
|`void assign(std::initializer_list<T> ilist)`|`void`|`ilist`|用初始化列表替换全部内容（C++11）。|

---

#### 2) 迭代器相关

> 注意：`list` 的迭代器是 **双向迭代器 (Bidirectional Iterator)**，不支持 `+n` 或 `-n` 跳转，只能 `++` 或 `--`。

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`iterator begin() noexcept`|`iterator`|无|指向首元素。|
|`const_iterator begin() const noexcept`|`const_iterator`|无|指向首元素（只读）。|
|`const_iterator cbegin() const noexcept`|`const_iterator`|无|指向首元素（只读，C++11）。|
|`iterator end() noexcept`|`iterator`|无|指向尾后位置。|
|`const_iterator end() const noexcept`|`const_iterator`|无|指向尾后位置（只读）。|
|`const_iterator cend() const noexcept`|`const_iterator`|无|指向尾后位置（只读，C++11）。|
|`reverse_iterator rbegin() noexcept`|`reverse_iterator`|无|反向首（对应最后一个元素）。|
|`const_reverse_iterator crbegin() const noexcept`|`const_reverse_iterator`|无|反向首（只读，C++11）。|
|`reverse_iterator rend() noexcept`|`reverse_iterator`|无|反向尾后。|
|`const_reverse_iterator crend() const noexcept`|`const_reverse_iterator`|无|反向尾后（只读，C++11）。|

---

#### 3) 容量相关

> 注意：`list` 没有 `capacity()` 或 `reserve()`，因为节点是离散分配的。

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`bool empty() const noexcept`|`bool`|无|是否为空。|
|`size_type size() const noexcept`|`size_type`|无|元素个数（C++11 起保证 O(1)）。|
|`size_type max_size() const noexcept`|`size_type`|无|理论最大可容纳元素数。|

---

#### 4) 元素访问

> 注意：`list` 不支持 `operator[]` 或 `at()`。

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`reference front()`|`reference`|无|首元素引用。|
|`const_reference front() const`|`const_reference`|无|首元素只读引用。|
|`reference back()`|`reference`|无|尾元素引用。|
|`const_reference back() const`|`const_reference`|无|尾元素只读引用。|

---

#### 5) 通用修改器（增删改）

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`void clear() noexcept`|`void`|无|清空所有元素。|
|`iterator insert(const_iterator pos, const T& value)`|`iterator`|`pos`, `value`|在 `pos` 前插入 `value`（拷贝）。|
|`iterator insert(const_iterator pos, T&& value)`|`iterator`|`pos`, `value`|在 `pos` 前插入 `value`（移动，C++11）。|
|`iterator insert(const_iterator pos, size_type count, const T& value)`|`iterator`|`pos`, `count`, `value`|在 `pos` 前插入 `count` 个 `value`。|
|`template<class InputIt> iterator insert(const_iterator pos, InputIt first, InputIt last)`|`iterator`|`pos`, `[first,last)`|在 `pos` 前插入范围元素。|
|`template<class... Args> iterator emplace(const_iterator pos, Args&&... args)`|`iterator`|`pos`, `args...`|在 `pos` 前**原地构造**元素（C++11）。|
|`void push_back(const T& value)`|`void`|`value`|尾部插入（拷贝）。|
|`void push_back(T&& value)`|`void`|`value`|尾部插入（移动，C++11）。|
|`template<class... Args> reference emplace_back(Args&&... args)`|`reference`|`args...`|尾部原地构造元素（C++11；C++17 起返回引用）。|
|`void pop_back()`|`void`|无|删除尾元素。|
|`void push_front(const T& value)`|`void`|`value`|**头部插入**（拷贝）。|
|`void push_front(T&& value)`|`void`|`value`|**头部插入**（移动，C++11）。|
|`template<class... Args> reference emplace_front(Args&&... args)`|`reference`|`args...`|**头部原地构造**元素（C++11；C++17 起返回引用）。|
|`void pop_front()`|`void`|无|**删除首元素**。|
|`iterator erase(const_iterator pos)`|`iterator`|`pos`|删除 `pos` 处元素，返回下一元素迭代器。|
|`iterator erase(const_iterator first, const_iterator last)`|`iterator`|`[first,last)`|删除范围元素。|
|`void resize(size_type count)`|`void`|`count`|调整大小：变大追加值初始化元素；变小删除尾部。|
|`void resize(size_type count, const T& value)`|`void`|`count`, `value`|变大时用 `value` 填充新增元素。|
|`void swap(list& other) noexcept`|`void`|`other`|交换内容（仅交换内部指针，O(1)）。|

---

#### 6) 链表特有操作（成员函数）

> 提示：由于 `list` 迭代器非随机访问，使用 `std::sort` 等通用算法效率极低或无法编译。应优先使用以下成员函数，它们通常通过修改指针实现，不涉及元素拷贝，效率极高。

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`void merge(list& other)`|`void`|`other`|合并两个**已排序**的链表。`other` 变为空。|
|`template <class Compare> void merge(list& other, Compare comp)`|`void`|`other`, `comp`|自定义比较规则的合并。|
|`void splice(const_iterator pos, list& other)`|`void`|`pos`, `other`|将 `other` 所有元素移动到本链表 `pos` 之前。`other` 变为空。|
|`void splice(const_iterator pos, list& other, const_iterator it)`|`void`|`pos`, `other`, `it`|将 `other` 中 `it` 指向的元素移动到 `pos` 之前。|
|`void splice(const_iterator pos, list& other, const_iterator first, const_iterator last)`|`void`|`pos`, `other`, `first`, `last`|将 `other` 中范围元素移动到 `pos` 之前。|
|`size_type remove(const T& value)`|`size_type`|`value`|删除所有等于 `value` 的元素（C++20 起返回删除个数）。|
|`template<class UnaryPredicate> size_type remove_if(UnaryPredicate p)`|`size_type`|`p`|删除所有满足谓词 `p` 的元素（C++20 起返回删除个数）。|
|`void reverse() noexcept`|`void`|无|逆转链表（O(n)）。|
|`size_type unique()`|`size_type`|无|删除**连续**重复元素，只留一个（C++20 起返回删除个数）。|
|`template<class BinaryPredicate> size_type unique(BinaryPredicate p)`|`size_type`|`p`|自定义相等判定规则的去重。|
|`void sort()`|`void`|无|对链表排序（升序）。|
|`template<class Compare> void sort(Compare comp)`|`void`|`comp`|自定义比较规则排序。|

---

#### 7) 非成员函数 / 操作符

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`bool operator==(const list& a, const list& b)`|`bool`|`a`, `b`|按元素比较相等。|
|`std::strong_ordering operator<=>(const list& a, const list& b)`|比较类别|`a`, `b`|三路比较（C++20）。|
|`void swap(list& a, list& b) noexcept`|`void`|`a`, `b`|交换两个 list。|
|`size_type erase(list& c, const U& value)`|`size_type`|`c`, `value`|删除所有等于 `value` 的元素（C++20）。|
|`size_type erase_if(list& c, Pred pred)`|`size_type`|`c`, `pred`|删除所有满足谓词的元素（C++20）。|
## 关联性容器
### set
#### 1) 构造 / 析构 / 赋值

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`set()`|—|无|默认构造，创建空集合。|
|`explicit set(const Compare& comp, const Alloc& alloc = Alloc())`|—|`comp`, `alloc`|指定比较器（如 `std::greater<T>`）和分配器构造。|
|`template<class InputIt> set(InputIt first, InputIt last, ...)`|—|`[first,last)`, ...|范围构造。|
|`set(std::initializer_list<T> init, ...)`|—|`init`, ...|初始化列表构造（C++11）。|
|`set(const set& other)`|—|`other`|拷贝构造。|
|`set(set&& other) noexcept`|—|`other`|移动构造（C++11）。|
|`~set()`|—|无|析构。|
|`set& operator=(const set& other)`|`set&`|`other`|拷贝赋值。|
|`set& operator=(set&& other) noexcept`|`set&`|`other`|移动赋值（C++11）。|
|`set& operator=(std::initializer_list<T> ilist)`|`set&`|`ilist`|初始化列表赋值（C++11）。|

---

#### 2) 迭代器相关

> 注意：set 的迭代器是 双向迭代器 (Bidirectional Iterator)。
> 
> 关键点：所有迭代器指向的元素在语法上被视为 const，不可通过迭代器修改元素值（防止破坏红黑树顺序）。

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`begin()` / `cbegin()`|`iterator`|无|指向最小元素（默认排序下）。|
|`end()` / `cend()`|`iterator`|无|指向尾后。|
|`rbegin()` / `crbegin()`|`reverse_iterator`|无|反向首（最大元素）。|
|`rend()` / `crend()`|`reverse_iterator`|无|反向尾后。|

---

#### 3) 容量相关

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`bool empty() const noexcept`|`bool`|无|是否为空。|
|`size_type size() const noexcept`|`size_type`|无|元素个数。|
|`size_type max_size() const noexcept`|`size_type`|无|理论最大容量。|

---

#### 4) 查找操作 (Lookup)

| **函数（签名）**                                            | **返回值类型**        | **参数** | **解释**                                  |
| ----------------------------------------------------- | ---------------- | ------ | --------------------------------------- |
| `size_type count(const Key& key) const`               | `size_type`      | `key`  | 返回键为 `key` 的元素个数（在 `set` 中只能是 0 或 1）。   |
| `iterator find(const Key& key)`                       | `iterator`       | `key`  | 查找 `key`，找到返回迭代器，否则返回 `end()`。          |
| `const_iterator find(const Key& key) const`           | `const_iterator` | `key`  | 只读版本。                                   |
| `bool contains(const Key& key) const`                 | `bool`           | `key`  | 检查是否存在 `key`（C++20）。                    |
| `iterator lower_bound(const Key& key)`                | `iterator`       | `key`  | 返回指向**首个不小于**（$\ge$）`key` 的元素的迭代器。      |
| `iterator upper_bound(const Key& key)`                | `iterator`       | `key`  | 返回指向**首个大于**（$>$）`key` 的元素的迭代器。         |
| `pair<iterator,iterator> equal_range(const Key& key)` | `pair`           | `key`  | 返回 `lower_bound` 和 `upper_bound` 构成的范围。 |

---

#### 5) 修改器（增删）

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`void clear() noexcept`|`void`|无|清空所有元素。|
|`pair<iterator, bool> insert(const value_type& value)`|`pair`|`value`|插入元素。若存在则不插入。返回 `{迭代器, 是否插入成功}`。|
|`pair<iterator, bool> insert(value_type&& value)`|`pair`|`value`|移动插入（C++11）。|
|`iterator insert(const_iterator hint, const value_type& value)`|`iterator`|`hint`, `value`|带提示位置的插入（若 hint 正确可达 O(1)，否则 O(log n)）。|
|`template<class... Args> pair<iterator, bool> emplace(Args&&... args)`|`pair`|`args...`|原地构造插入（C++11）。|
|`iterator erase(const_iterator pos)`|`iterator`|`pos`|删除迭代器指向的元素，返回下一元素迭代器。|
|`iterator erase(const_iterator first, const_iterator last)`|`iterator`|`[first,last)`|删除范围。|
|`size_type erase(const Key& key)`|`size_type`|`key`|删除键为 `key` 的元素，返回删除个数（在 set 中为 0 或 1）。|
|`void swap(set& other) noexcept`|`void`|`other`|交换内容。|
|`node_type extract(const_iterator position)`|`node_type`|`pos`|提取节点（所有权转移），不进行拷贝/析构（C++17）。|
|`node_type extract(const Key& k)`|`node_type`|`k`|按 key 提取节点（C++17）。|
|`void merge(set& source)`|`void`|`source`|将 `source` 中的节点接合到当前 set（无拷贝），重复元素保留在 source 中（C++17）。|
### multiset
#### 1) 构造 / 析构 / 赋值

（与 `set` 相同，略）

#### 2) 迭代器 / 3) 容量

（与 `set` 相同，略）

#### 4) 查找操作 (Lookup) - 差异点

| **函数（签名）**                                            | **返回值类型**   | **参数** | **解释**                                    |
| ----------------------------------------------------- | ----------- | ------ | ----------------------------------------- |
| `size_type count(const Key& key) const`               | `size_type` | `key`  | 返回键为 `key` 的元素个数（**可能 > 1**）。             |
| `iterator find(const Key& key)`                       | `iterator`  | `key`  | 查找 `key`。若有重复，返回**任意一个**（通常是第一个）的迭代器。     |
| `iterator lower_bound(const Key& key)`                | `iterator`  | `key`  | 返回**第一个** $\ge$ `key` 的位置。                |
| `iterator upper_bound(const Key& key)`                | `iterator`  | `key`  | 返回**第一个** $>$ `key` 的位置。                  |
| `pair<iterator,iterator> equal_range(const Key& key)` | `pair`      | `key`  | 返回包含**所有**等于 `key` 元素的区间 `[first, last)`。 |

---

#### 5) 修改器（增删）- 差异点

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`iterator insert(const value_type& value)`|**`iterator`**|`value`|总是插入成功（允许重复），返回新元素的迭代器。**注意：不返回 bool**。|
|`template<class... Args> iterator emplace(Args&&... args)`|**`iterator`**|`args...`|原地构造，返回迭代器。|
|`size_type erase(const Key& key)`|`size_type`|`key`|删除**所有**等于 `key` 的元素，返回删除的总数。|
|`iterator erase(const_iterator pos)`|`iterator`|`pos`|删除指定的一个元素（即使有重复，只删迭代器指向的那一个）。|

---

#### 6) 非成员函数 (set & multiset 通用)

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`bool operator==(const set& a, const set& b)`|`bool`|`a`, `b`|比较内容是否完全相同。|
|`std::strong_ordering operator<=>(...)`|比较类别|`a`, `b`|三路比较（C++20）。|
|`size_type erase_if(set& c, Pred pred)`|`size_type`|`c`, `pred`|删除满足谓词的元素（C++20）。|
### map

> 头文件：`<map>`  
> 特点：**键唯一**的有序关联容器（通常红黑树实现），按 `Compare` 对 `Key` 排序；查找/插入/删除通常为 O(log n)

#### 1) 构造 / 析构 / 赋值

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`map()`|—|无|默认构造空容器。|
|`explicit map(const Compare& comp, const Allocator& alloc = Allocator())`|—|`comp`, `alloc`|指定比较器/分配器构造空容器。|
|`explicit map(const Allocator& alloc)`|—|`alloc`|指定分配器构造空容器。|
|`template<class InputIt> map(InputIt first, InputIt last, const Compare& comp = Compare(), const Allocator& alloc = Allocator())`|—|`[first,last)`, `comp`, `alloc`|迭代器范围构造（键唯一）。|
|`map(const map& other)`|—|`other`|拷贝构造。|
|`map(const map& other, const Allocator& alloc)`|—|`other`, `alloc`|指定分配器的拷贝构造。|
|`map(map&& other) noexcept`|—|`other`|移动构造（C++11）。|
|`map(map&& other, const Allocator& alloc)`|—|`other`, `alloc`|指定分配器的移动构造（C++11）。|
|`map(std::initializer_list<value_type> init, const Compare& comp = Compare(), const Allocator& alloc = Allocator())`|—|`init`, `comp`, `alloc`|初始化列表构造（C++11）。|
|`template<class R> map(std::from_range_t, R&& rg, const Compare& comp = Compare(), const Allocator& alloc = Allocator())`|—|`std::from_range`, `rg`, `comp`, `alloc`|范围构造标签（C++23）。([en.cppreference.com](https://en.cppreference.com/w/cpp/container/map/map.html?utm_source=chatgpt.com "std::map<Key,T,Compare,Allocator>"))|
|`~map()`|—|无|析构。|
|`map& operator=(const map& other)`|`map&`|`other`|拷贝赋值。|
|`map& operator=(map&& other) noexcept`|`map&`|`other`|移动赋值（C++11）。|
|`map& operator=(std::initializer_list<value_type> ilist)`|`map&`|`ilist`|初始化列表赋值（C++11）。|
|`allocator_type get_allocator() const`|`allocator_type`|无|获取分配器副本。|

> 说明：关联容器（如 `map`）没有 `assign()`（与序列容器不同）。

#### 2) 迭代器相关

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`iterator begin() noexcept` / `const_iterator begin() const noexcept`|`iterator` / `const_iterator`|无|指向首元素。|
|`const_iterator cbegin() const noexcept`|`const_iterator`|无|只读首元素迭代器（C++11）。|
|`iterator end() noexcept` / `const_iterator end() const noexcept`|`iterator` / `const_iterator`|无|指向尾后。|
|`const_iterator cend() const noexcept`|`const_iterator`|无|只读尾后（C++11）。|
|`reverse_iterator rbegin() noexcept` / `const_reverse_iterator rbegin() const noexcept`|`reverse_iterator` / `const_reverse_iterator`|无|反向首。|
|`const_reverse_iterator crbegin() const noexcept`|`const_reverse_iterator`|无|只读反向首（C++11）。|
|`reverse_iterator rend() noexcept` / `const_reverse_iterator rend() const noexcept`|`reverse_iterator` / `const_reverse_iterator`|无|反向尾后。|
|`const_reverse_iterator crend() const noexcept`|`const_reverse_iterator`|无|只读反向尾后（C++11）。|

#### 3) 容量相关

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`bool empty() const noexcept`|`bool`|无|是否为空。|
|`size_type size() const noexcept`|`size_type`|无|元素个数。|
|`size_type max_size() const noexcept`|`size_type`|无|理论最大容量。|

#### 4) 元素访问（`map` 独有）

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`mapped_type& operator[](const key_type& key)`|`mapped_type&`|`key`|若 `key` 不存在则**插入**一个（`mapped_type{}`），并返回其 `mapped_type` 引用。|
|`mapped_type& operator[](key_type&& key)`|`mapped_type&`|`key`|同上，但键可移动（C++11）。|
|`mapped_type& at(const key_type& key)`|`mapped_type&`|`key`|访问已存在键；不存在则抛 `std::out_of_range`。|
|`const mapped_type& at(const key_type& key) const`|`const mapped_type&`|`key`|只读版本。|

#### 5) 修改器（插入 / 删除 / 交换 / 节点）

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`void clear() noexcept`|`void`|无|清空所有元素。|
|`std::pair<iterator,bool> insert(const value_type& value)`|`pair<iterator,bool>`|`value`|插入键值对；若键已存在则不插入，`bool=false`。|
|`std::pair<iterator,bool> insert(value_type&& value)`|`pair<iterator,bool>`|`value`|移动插入（C++11）。|
|`iterator insert(const_iterator hint, const value_type& value)`|`iterator`|`hint`, `value`|带位置提示插入；返回插入位置迭代器。|
|`iterator insert(const_iterator hint, value_type&& value)`|`iterator`|`hint`, `value`|带 hint 的移动插入（C++11）。|
|`template<class InputIt> void insert(InputIt first, InputIt last)`|`void`|`[first,last)`|范围插入（跳过重复键）。|
|`void insert(std::initializer_list<value_type> ilist)`|`void`|`ilist`|初始化列表插入（C++11）。|
|`template<class R> void insert_range(R&& rg)`|`void`|`rg`|范围插入（C++23）。([en.cppreference.com](https://en.cppreference.com/w/cpp/container/map/insert_range.html?utm_source=chatgpt.com "std::map<Key,T,Compare,Allocator>::insert_range"))|
|`template<class... Args> std::pair<iterator,bool> emplace(Args&&... args)`|`pair<iterator,bool>`|`args...`|原地构造并尝试插入（键唯一）。|
|`template<class... Args> iterator emplace_hint(const_iterator hint, Args&&... args)`|`iterator`|`hint`, `args...`|带 hint 的原地构造插入。|
|`template<class... Args> std::pair<iterator,bool> try_emplace(const key_type& k, Args&&... args)`|`pair<iterator,bool>`|`k`, `args...`|**仅当键不存在**时，原地构造 `mapped_type(args...)` 并插入（C++17）。|
|`template<class... Args> iterator try_emplace(const_iterator hint, const key_type& k, Args&&... args)`|`iterator`|`hint`, `k`, `args...`|带 hint 的 `try_emplace`（C++17）。|
|`template<class M> std::pair<iterator,bool> insert_or_assign(const key_type& k, M&& obj)`|`pair<iterator,bool>`|`k`, `obj`|键不存在则插入；存在则对 `mapped_type` 赋值（C++17）。|
|`template<class M> iterator insert_or_assign(const_iterator hint, const key_type& k, M&& obj)`|`iterator`|`hint`, `k`, `obj`|带 hint 的 `insert_or_assign`（C++17）。|
|`iterator erase(const_iterator pos)`|`iterator`|`pos`|删除 `pos` 元素，返回后继迭代器。|
|`iterator erase(const_iterator first, const_iterator last)`|`iterator`|`[first,last)`|删除范围，返回 `last` 对应位置。|
|`size_type erase(const key_type& key)`|`size_type`|`key`|按键删除（最多删除 1 个），返回删除个数。|
|`void swap(map& other) noexcept`|`void`|`other`|交换内容。|
|`node_type extract(const_iterator pos)`|`node_type`|`pos`|节点提取（不析构元素）（C++17）。|
|`node_type extract(const key_type& key)`|`node_type`|`key`|按键提取节点（C++17）。|
|`void merge(map& source)` / `void merge(map&& source)`|`void`|`source`|合并：从 `source` 迁移**不冲突键**的节点（C++17）。|
|`std::pair<iterator,bool> insert(node_type&& nh)`|`pair<iterator,bool>`|`nh`|插入节点句柄（键唯一，C++17）。|
|`iterator insert(const_iterator hint, node_type&& nh)`|`iterator`|`hint`, `nh`|带 hint 的节点插入（C++17）。|

> 备注：当 `Compare` 支持透明比较（`is_transparent`）时，`find/erase/count/contains/lower_bound/upper_bound/equal_range` 等通常还存在“异质查找”的模板重载（接收任意可比较的 `K`）。

#### 6) 查找（Lookup）

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`size_type count(const key_type& key) const`|`size_type`|`key`|返回键等于 `key` 的元素数量（`map` 只可能是 0 或 1）。|
|`iterator find(const key_type& key)` / `const_iterator find(const key_type& key) const`|`iterator` / `const_iterator`|`key`|查找键，返回迭代器或 `end()`。|
|`bool contains(const key_type& key) const`|`bool`|`key`|是否包含该键（C++20）。|
|`std::pair<iterator,iterator> equal_range(const key_type& key)`|`pair<it,it>`|`key`|返回等价键的范围（对 `map` 要么空要么单元素）。|
|`iterator lower_bound(const key_type& key)` / `const_iterator lower_bound(const key_type& key) const`|`iterator` / `const_iterator`|`key`|第一个 `!(elem_key < key)` 的位置。|
|`iterator upper_bound(const key_type& key)` / `const_iterator upper_bound(const key_type& key) const`|`iterator` / `const_iterator`|`key`|第一个 `(key < elem_key)` 的位置。|

#### 7) 观察器（Observers）

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`key_compare key_comp() const`|`key_compare`|无|返回键比较器副本。|
|`value_compare value_comp() const`|`value_compare`|无|返回值比较器（按 `value_type` 比较，本质比较 `first`）。|

#### 8) 非成员函数 / 操作符

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`bool operator==(const map& a, const map& b)`|`bool`|`a`, `b`|按元素比较是否相等。|
|`auto operator<=>(const map& a, const map& b)`|比较类别|`a`, `b`|三路比较（C++20；返回类型依元素比较能力而定）。|
|`void swap(map& a, map& b) noexcept`|`void`|`a`, `b`|交换两个 `map`（ADL）。|
|`template<class K, class T, class C, class A, class U> size_type erase(map<K,T,C,A>& c, const U& value)`|`size_type`|`c`, `value`|删除所有等于 `value` 的元素（C++20 非成员）。|
|`template<class K, class T, class C, class A, class Pred> size_type erase_if(map<K,T,C,A>& c, Pred pred)`|`size_type`|`c`, `pred`|删除所有满足谓词的元素（C++20 非成员）。|


### multimap
 >头文件：`<map>`  
> 特点：允许**键重复**的有序关联容器；同一键可有多个元素.

#### 1) 构造 / 析构 / 赋值

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`multimap()`|—|无|默认构造空容器。|
|`explicit multimap(const Compare& comp, const Allocator& alloc = Allocator())`|—|`comp`, `alloc`|指定比较器/分配器构造空容器。|
|`explicit multimap(const Allocator& alloc)`|—|`alloc`|指定分配器构造空容器。|
|`template<class InputIt> multimap(InputIt first, InputIt last, const Compare& comp = Compare(), const Allocator& alloc = Allocator())`|—|`[first,last)`, `comp`, `alloc`|范围构造（允许重复键）。|
|`multimap(const multimap& other)` / `multimap(multimap&& other) noexcept`|—|`other`|拷贝/移动构造（移动 C++11）。|
|`multimap(std::initializer_list<value_type> init, const Compare& comp = Compare(), const Allocator& alloc = Allocator())`|—|`init`, `comp`, `alloc`|初始化列表构造（C++11）。|
|`template<class R> multimap(std::from_range_t, R&& rg, const Compare& comp = Compare(), const Allocator& alloc = Allocator())`|—|`std::from_range`, `rg`, `comp`, `alloc`|范围构造标签（C++23）。([en.cppreference.com](https://en.cppreference.com/w/cpp/container/multimap/multimap.html?utm_source=chatgpt.com "std::multimap<Key,T,Compare,Allocator>"))|
|`~multimap()`|—|无|析构。|
|`multimap& operator=(const multimap& other)` / `multimap& operator=(multimap&& other) noexcept`|`multimap&`|`other`|拷贝/移动赋值（移动 C++11）。|
|`multimap& operator=(std::initializer_list<value_type> ilist)`|`multimap&`|`ilist`|初始化列表赋值（C++11）。|
|`allocator_type get_allocator() const`|`allocator_type`|无|获取分配器副本。|

#### 2) 迭代器相关

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`begin / cbegin / end / cend`|`iterator/const_iterator`|无|正向遍历接口（同 `map`）。|
|`rbegin / crbegin / rend / crend`|`reverse_iterator/const_reverse_iterator`|无|反向遍历接口（同 `map`）。|

#### 3) 容量相关

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`bool empty() const noexcept`|`bool`|无|是否为空。|
|`size_type size() const noexcept`|`size_type`|无|元素个数。|
|`size_type max_size() const noexcept`|`size_type`|无|理论最大容量。|

#### 4) 修改器（插入 / 删除 / 交换 / 节点）

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`void clear() noexcept`|`void`|无|清空所有元素。|
|`iterator insert(const value_type& value)`|`iterator`|`value`|插入一个元素（允许重复键），返回插入位置迭代器。|
|`iterator insert(value_type&& value)`|`iterator`|`value`|移动插入（C++11）。|
|`iterator insert(const_iterator hint, const value_type& value)`|`iterator`|`hint`, `value`|带 hint 插入。|
|`iterator insert(const_iterator hint, value_type&& value)`|`iterator`|`hint`, `value`|带 hint 的移动插入（C++11）。|
|`template<class InputIt> void insert(InputIt first, InputIt last)`|`void`|`[first,last)`|范围插入（允许重复键）。|
|`void insert(std::initializer_list<value_type> ilist)`|`void`|`ilist`|初始化列表插入（C++11）。|
|`template<class R> void insert_range(R&& rg)`|`void`|`rg`|范围插入（C++23）。([en.cppreference.com](https://en.cppreference.com/w/cpp/container/multimap/insert_range.html?utm_source=chatgpt.com "std::multimap<Key,T,Compare,Allocator>::insert_range"))|
|`template<class... Args> iterator emplace(Args&&... args)`|`iterator`|`args...`|原地构造并插入（允许重复键）。|
|`template<class... Args> iterator emplace_hint(const_iterator hint, Args&&... args)`|`iterator`|`hint`, `args...`|带 hint 的原地构造插入。|
|`iterator erase(const_iterator pos)`|`iterator`|`pos`|删除 `pos` 元素，返回后继迭代器。|
|`iterator erase(const_iterator first, const_iterator last)`|`iterator`|`[first,last)`|删除范围。|
|`size_type erase(const key_type& key)`|`size_type`|`key`|按键删除**所有等价键**元素，返回删除个数。|
|`void swap(multimap& other) noexcept`|`void`|`other`|交换内容。|
|`node_type extract(const_iterator pos)`|`node_type`|`pos`|提取节点（C++17）。|
|`node_type extract(const key_type& key)`|`node_type`|`key`|提取某个等价键的一个节点（具体取哪个由实现决定）（C++17）。|
|`void merge(multimap& source)` / `void merge(multimap&& source)`|`void`|`source`|合并：从 `source` 迁移节点（`multimap` 允许重复键，通常会迁移全部）（C++17）。|
|`iterator insert(node_type&& nh)`|`iterator`|`nh`|插入节点句柄（允许重复键，C++17）。|
|`iterator insert(const_iterator hint, node_type&& nh)`|`iterator`|`hint`, `nh`|带 hint 的节点插入（C++17）。|

> 说明：`multimap` **没有** `operator[]` / `at` / `try_emplace` / `insert_or_assign`（这些是“键唯一且可按键访问 mapped_type”的 `map` 特性）。

#### 5) 查找（Lookup）

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`size_type count(const key_type& key) const`|`size_type`|`key`|返回等价键的元素数量（可能 ≥ 0）。|
|`iterator find(const key_type& key)` / `const_iterator find(const key_type& key) const`|`iterator` / `const_iterator`|`key`|查找任一等价键元素（返回其中一个，否则 `end()`）。|
|`bool contains(const key_type& key) const`|`bool`|`key`|是否包含该键（C++20）。|
|`std::pair<iterator,iterator> equal_range(const key_type& key)`|`pair<it,it>`|`key`|返回该键对应的**全部等价元素范围**。|
|`iterator lower_bound(const key_type& key)` / `const_iterator lower_bound(const key_type& key) const`|`iterator` / `const_iterator`|`key`|第一个不小于 `key` 的位置。|
|`iterator upper_bound(const key_type& key)` / `const_iterator upper_bound(const key_type& key) const`|`iterator` / `const_iterator`|`key`|第一个大于 `key` 的位置。|

#### 6) 观察器（Observers）

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`key_compare key_comp() const`|`key_compare`|无|返回键比较器副本。|
|`value_compare value_comp() const`|`value_compare`|无|返回值比较器（按 `value_type` 比较键）。|

#### 7) 非成员函数 / 操作符

|函数（签名）|返回值类型|参数|解释|
|---|--:|---|---|
|`bool operator==(const multimap& a, const multimap& b)`|`bool`|`a`, `b`|按元素序列比较是否相等。|
|`auto operator<=>(const multimap& a, const multimap& b)`|比较类别|`a`, `b`|三路比较（C++20）。|
|`void swap(multimap& a, multimap& b) noexcept`|`void`|`a`, `b`|交换两个 `multimap`（ADL）。|
|`template<class K, class T, class C, class A, class U> size_type erase(multimap<K,T,C,A>& c, const U& value)`|`size_type`|`c`, `value`|删除所有等于 `value` 的元素（C++20 非成员）。|
|`template<class K, class T, class C, class A, class Pred> size_type erase_if(multimap<K,T,C,A>& c, Pred pred)`|`size_type`|`c`, `pred`|删除所有满足谓词的元素（C++20 非成员）。|

---

如果你接下来要我继续按同一模板补 `set / multiset`，我建议顺序是：`set`（键唯一）→ `multiset`（键可重复），这样对比最清晰。
## 容器适配器
### stack
#### 1) 构造 / 析构 / 赋值

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`stack()`|—|无|默认构造（使用底层容器的默认构造）。|
|`explicit stack(const Container& cont)`|—|`cont`|使用现有的容器 `cont` 初始化栈（拷贝）。|
|`explicit stack(Container&& cont)`|—|`cont`|使用现有的容器 `cont` 初始化栈（移动，C++11）。|
|`stack(const stack& other)`|—|`other`|拷贝构造。|
|`stack(stack&& other) noexcept`|—|`other`|移动构造（C++11）。|
|`~stack()`|—|无|析构。|
|`stack& operator=(const stack& other)`|`stack&`|`other`|拷贝赋值。|
|`stack& operator=(stack&& other) noexcept`|`stack&`|`other`|移动赋值（C++11）。|

---

#### 2) 迭代器相关

> 注意：stack 不提供迭代器 (begin(), end() 等)。
> 
> 设计初衷是为了严格限制访问模式，确保只能操作栈顶。如果需要遍历，请直接使用 vector 或 deque。

---

#### 3) 容量相关

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`bool empty() const`|`bool`|无|检查栈是否为空。|
|`size_type size() const`|`size_type`|无|返回栈中元素个数。|

---

#### 4) 元素访问

> **警告**：在空栈上调用 `top()` 是未定义行为，务必先检查 `!empty()`。

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`reference top()`|`reference`|无|返回栈顶元素的引用（可修改）。|
|`const_reference top() const`|`const_reference`|无|返回栈顶元素的只读引用。|

---

#### 5) 修改器（增删）

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`void push(const T& value)`|`void`|`value`|将元素压入栈顶（拷贝）。|
|`void push(T&& value)`|`void`|`value`|将元素压入栈顶（移动，C++11）。|
|`template<class... Args> void emplace(Args&&... args)`|`void`|`args...`|在栈顶**原地构造**新元素（C++11，效率高于 push）。|
|`void pop()`|`void`|无|移除栈顶元素。**注意：返回 void，不返回被移除的元素**。|
|`void swap(stack& other) noexcept`|`void`|`other`|交换两个栈的内容。|

---

#### 6) 非成员函数

| **函数（签名）**                                        | **返回值类型** | **参数**   | **解释**         |
| ------------------------------------------------- | --------- | -------- | -------------- |
| `bool operator==(const stack& a, const stack& b)` | `bool`    | `a`, `b` | 比较底层容器内容是否相等。  |
| `std::strong_ordering operator<=>(...)`           | 比较类别      | `a`, `b` | 三路比较（C++20）。   |
| `void swap(stack& a, stack& b) noexcept`          | `void`    | `a`, `b` | 交换两个栈（ADL 版本）。 |
### queue
#### 1) 构造 / 析构 / 赋值

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`queue()`|—|无|默认构造。|
|`explicit queue(const Container& cont)`|—|`cont`|使用现有容器初始化。|
|`explicit queue(Container&& cont)`|—|`cont`|移动现有容器初始化（C++11）。|
|`queue(const queue& other)`|—|`other`|拷贝构造。|
|`queue(queue&& other) noexcept`|—|`other`|移动构造（C++11）。|
|`~queue()`|—|无|析构。|
|`queue& operator=(const queue& other)`|`queue&`|`other`|拷贝赋值。|
|`queue& operator=(queue&& other) noexcept`|`queue&`|`other`|移动赋值（C++11）。|

---

#### 2) 迭代器相关

> **无迭代器**：`queue` 不允许遍历，只能访问头部和尾部。

---

#### 3) 容量相关

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`bool empty() const`|`bool`|无|检查队列是否为空。|
|`size_type size() const`|`size_type`|无|返回元素个数。|

---

#### 4) 元素访问

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`reference front()`|`reference`|无|返回**队首**元素引用（即最早进入的元素）。|
|`const_reference front() const`|`const_reference`|无|队首只读引用。|
|`reference back()`|`reference`|无|返回**队尾**元素引用（即最后进入的元素）。|
|`const_reference back() const`|`const_reference`|无|队尾只读引用。|

---

#### 5) 修改器（增删）

| **函数（签名）**                                             | **返回值类型** | **参数**    | **解释**              |
| ------------------------------------------------------ | --------- | --------- | ------------------- |
| `void push(const T& value)`                            | `void`    | `value`   | 队尾入队（拷贝）。           |
| `void push(T&& value)`                                 | `void`    | `value`   | 队尾入队（移动，C++11）。     |
| `template<class... Args> void emplace(Args&&... args)` | `void`    | `args...` | 队尾原地构造（C++11）。      |
| `void pop()`                                           | `void`    | 无         | **移除队首元素**。返回 void。 |
| `void swap(queue& other) noexcept`                     | `void`    | `other`   | 交换内容。               |
### priority_queue
#### 1) 构造 / 析构 / 赋值

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`priority_queue()`|—|无|默认构造（空）。|
|`priority_queue(const Compare& compare)`|—|`comp`|指定比较器构造（如 `std::greater<T>` 用于最小堆）。|
|`priority_queue(const Compare& comp, const Container& cont)`|—|`comp`, `cont`|指定比较器和底层容器初始化。|
|`template<class InputIt> priority_queue(InputIt first, InputIt last)`|—|`[first,last)`|**范围构造**。会执行建堆操作（通常 O(n)）。|
|`priority_queue(const priority_queue& other)`|—|`other`|拷贝构造。|
|`priority_queue(priority_queue&& other)`|—|`other`|移动构造（C++11）。|
|`~priority_queue()`|—|无|析构。|
|`priority_queue& operator=(...)`|`priority_queue&`|`other`|赋值操作。|

---

#### 2) 迭代器相关

> **无迭代器**：为了维护堆的性质，不提供对内部元素的随意遍历。

---

#### 3) 容量相关

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`bool empty() const`|`bool`|无|是否为空。|
|`size_type size() const`|`size_type`|无|元素个数。|

---

#### 4) 元素访问

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`const_reference top() const`|`const_reference`|无|返回**优先级最高**（默认是数值最大）的元素引用。**只读**，不可修改。|

---

#### 5) 修改器（增删）

> 注意：`push` 和 `pop` 的复杂度通常为 $O(\log n)$。

|**函数（签名）**|**返回值类型**|**参数**|**解释**|
|---|---|---|---|
|`void push(const T& value)`|`void`|`value`|插入元素并调整堆顺序。|
|`void push(T&& value)`|`void`|`value`|移动插入（C++11）。|
|`template<class... Args> void emplace(Args&&... args)`|`void`|`args...`|原地构造插入（C++11）。|
|`void pop()`|`void`|无|**移除优先级最高**（栈顶）的元素。|
|`void swap(priority_queue& other) noexcept`|`void`|`other`|交换内容。|

---

### 常用技巧提示

1. **如何实现最小堆（Min-Heap）？**
    
    - 默认 `priority_queue` 是最大堆（使用 `std::less`）。
        
    - 若要每次 `pop` 出**最小**的元素，需将比较器改为 `std::greater`：
        
        C++
        
        ```
        std::priority_queue<int, std::vector<int>, std::greater<int>> min_heap;
        ```
        
2. **底层容器选择**
    
    - `queue` 默认用 `deque` 是为了在两端操作时都保持高效。
        
    - `priority_queue` 默认用 `vector` 是因为堆排序需要频繁的随机访问（计算父子节点下标），且 `vector` 内存连续，缓存命中率最高。

# 算法
## 非变异算法
## 变异算法

# 迭代器
