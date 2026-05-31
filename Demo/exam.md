# 面向对象编程II(C++ STL)考试
### 一、选择题(单选或者多选皆有可能)
**1. 下列说法错误的是：**

- [ ] A. 如果没有 STL 提供的各种容器和算法，有一些(C 和 C++)编程任务无法完成。
- [ ] B. 我们的这门课程，我只需熟练掌握各种容器和算法的使用即可。

---

**2. 有关 traits 技术的说法正确的是：**

- [ ] A. 使用 traits 技术,可以编制出具有统一接口的函数或类模板，方便了用户的使用。
- [ ] B. 为了编制出具有统一接口的函数或类模板，增加了这些程序员的编程难度。
- [ ] C. 如果有一个问题能用模板特化来解决，那就没必要使用 traits 技术。

---

**3. 有关使用函数适配器的问题。**

有一个编程任务，需要一个函数对象，可以使用 STL 的函数对象(但需要用适配器进行包装后才能使用)，也可以使用自己编制的函数对象。如果按照程序的可靠性考虑，下列选择正确的是：

- [ ] A. 用适配器对 STL 的函数对象进行包装，然后再使用，但缺点是需要花费时间来熟悉函数适配器。
- [ ] B. 直接编制一个新的函数对象,优点是无需花费时间熟悉函数适配器，这样完成的速度最快。

---

**4. 有关迭代器的问题。下列说法正确的是：**

- [ ] A. 迭代器是专属于特定容器的，所以迭代器的接口因容器的不同而不同。
- [ ] B. 算法的一致性(不因容器而异)依赖于迭代器的接口特点。

---

**5. 已知 it 是容器的迭代器，可以正确执行 it=it+2 的容器是：**

- [ ] A. vector
- [ ] B. deque
- [ ] C. list

---

**6. 下列容器的哪几种，可用算法 equal 来比较(同类)容器的内容是否相同？**

- [ ] A. vector
- [ ] B. list
- [ ] C. set
- [ ] D. map

---

**7. 为了快速地由学生的学号找到该生的其它相关信息，学生的信息(包括了学号)宜用那种容器存储?**

- [ ] A. vector
- [ ] B. list
- [ ] C. set
- [ ] D. map

---

**8. 对于(标准输入输出、文件、字符串)流，可以作为分隔符是：**

- [ ] A. 空格
- [ ] B. 换行符
- [ ] C. #
- [ ] D. TAB

### 二、程序阅读题

**1. 已知 `bitset<4> b(14);` 则 `b.to_string()` 的结果为________. (5 分)**

---

**2. 下述程序运行后，则屏幕显示________. (5 分)**

```cpp
int a[5] = {9,7,5,3,1};
int *it = find_if(a, a+5, bind1st(greater<int>(), 5));
cout << distance(a, it) << endl;
```

---

**3. 下述程序运行后，则屏幕显示________. (5 分)**

```cpp
string strResult = "";
string strText = "How   are   you";
istringstream istr(strText);
cout << "string : ";
while (!istr.eof())
{
    istr >> strResult;
    cout << strResult << "  ";
}
cout << endl;
```

---

**4. 下述程序运行后，则屏幕显示________. (5 分)**

```cpp
bool fun(int v1, int v2)
{
    return (8 == (v1+v2));
}

int main()
{
    int a[6] = { 11,9,7,5,3,1 };
    int b[4] = { 1,3,5,7 };
    int *it = search(a, a + 6, b, b+4, fun);
    cout << distance(a, it) << endl;
    return 1;
}
```

---

**5. 下述程序运行后，则屏幕显示________. (5 分)**

```cpp
int A1[6] = { 3, 1, 4, 1, 5, 3 };
set<int, greater<int>> sm(A1, A1 + 6);
copy(sm.begin(), sm.end(), ostream_iterator<int>(cout, " "));
cout << endl;
```

---

**6. 下述程序运行后，则屏幕显示的第一行是________. (8分)**
**屏幕显示的最后一行是________. (2分)**

```cpp
template<typename KEY, typename VAL>
struct pair_equ
{
    bool operator()(pair<KEY, VAL>& v1, pair<KEY, VAL>& v2)
    {
        return(v1.first == v2.first);
    }
};

template<typename KEY, typename VAL> 
map<KEY, string> operator +(map<KEY, VAL>& in1, map<KEY, VAL>& in2)
{
    map<KEY, string> out;
    ostringstream os;
    typename map<KEY, VAL>::iterator it1 = in1.begin();
    typename map<KEY, VAL>::iterator it2 = in2.begin();
    if(in1.size() != in2.size()) return out;    //如果个数不同就返回
    //如果俩容器有不同的key就返回:
    if(!equal(in1.begin(), in1.end(), in2.begin(), pair_equ<const KEY, VAL>())) return out;
    KEY key; VAL val;
    while (it1 != in1.end())
    {
        os.str("");
        os << (*it1).second << "  " << (*it2).second;
        key = (*it1).first;
        val = os.str();
        out.insert(pair<KEY, string>(key, val));
        it1++; it2++;
    }
    return out;
}

template<typename KEY, typename VAL>
ostream& operator<<(ostream& os, map<KEY, VAL>& var)
{
    typename map<KEY, VAL>::iterator it1;
    for (it1 = var.begin(); it1 != var.end(); it1++)
    {
        os << (*it1).first << "  " << (*it1).second << endl;
    }
    return os;
}

int main() {
    map<int, string> mymap;
    pair<int, string> s1(1, "cc");    pair<int, string> t1(1, "Tcc");
    pair<int, string> s2(3, "bb");    pair<int, string> t2(3, "Tbb");
    pair<int, string> s3(6, "aa");    pair<int, string> t3(6, "Taa");
    pair<int, string> s4(5, "dd");    pair<int, string> t4(5, "Tdd");
    pair<int, string> s5(4, "ee");    pair<int, string> t5(4, "Tee");

    pair<int, string> pa1[] = { s1,s2,s3,s4,s5 };
    map<int, string> mapA(pa1, pa1 + 5);

    pair<int, string> pa2[] = { t1,t2,t3,t4,t5 };
    map<int, string> mapB(pa2, pa2 + 5);

    map<int, string> map_out;
    map_out = mapA + mapB;
    cout << map_out;

    mapB.erase(6);
    map_out = mapA + mapB;
    cout << map_out.size() << endl;
    return 0;
}
```

---

**7. 下述程序运行后，已知屏幕第一行显示的是 `4  8`，问屏幕第二行显示的是________. (5分)**

```cpp
template <typename T> class TraitsHelper { };

template <> class TraitsHelper<int>
{
public:
    typedef double ret_type;
    typedef double par_type;
};

template <> class TraitsHelper<double>
{
public:
    typedef int ret_type;
    typedef int par_type;
};

template <typename T>
class Test
{
public:
    typename TraitsHelper<T>::ret_type
    Compute(typename TraitsHelper<T>::par_type para)
    {
        return para * sizeof(para);
    }
};

int main() {
    Test<int> tt1;
    Test<double> tt2;
    cout << sizeof(int) << "  " << sizeof(double) << endl;
    cout << tt1.Compute(10) << "  " << tt2.Compute(10) << endl;
    return 0;
}
```

### 三、编程题

**1. 编程判断任意二个 set 容器的内容是否相等，要求屏幕输出是：`1  0`**

编程要求：只能填写下划线处的指令，下划线处的指令可能需要一条或多条。

`template<class T, class _Pr1, class _Pr2>` // `_Pr1`、`_Pr2`是自定义函数

```cpp
bool operator == (const set<T, _Pr1>& v1, const set<T, _Pr2>& v2)
{
    typename set<T, _Pr1>::iterator it1 = v1.begin();
    ________________________①
    if(________________________②) return false;
    while (it1 != v1.end())
    {
        ________________________③
    }
    return true;
}

int main()
{
    int a1[] = { 1,2,3,4 };
    int a2[] = { 4,3,2,1 };
    int a3[] = { 4,3,2,1,5, 6 };
    set<int, less<int>> s1(a1, a1 + 4);
    set<int, greater<int>> s2(a2, a2 + 4);
    set<int, greater<int>> s3(a3, a3 + 6);
    cout << (s1 == s2) << "  " << (s1 == s3) << endl;
    return 0;
}
```

---

**2. 编程从控制台输出 vector 的全部内容，要求屏幕输出是：`1  2  3  4`**

编程要求：只能填写下划线处的指令，下划线处的指令可能需要一条或多条。

```cpp
template <class T>
ostream& operator << (ostream& os, vector<T>& v)
{
    ________________________①
}

int main()
{
    int a1[] = { 1,2,3,4 };
    vector<int> v1(a1, a1 + 4);
    cout << v1 << endl;
    return 0;
}
```

---

**3. 编程统计 `vector<int>` 中偶数的个数。要求:只能用 STL 算法实现。**

编程要求：只能填写下划线处的指令，下划线处的指令可能需要一条或多条。

```cpp
________________________①//此处为仿函数定义

int main()
{
    int a1[] = { 1,2,3,4,5,6,8 };
    vector<int> v1(a1, a1 + sizeof(a1) / sizeof(int));
    ________________________②//此处为STL算法函数
    cout << ret << endl;
    return 0;
}
```