<!-- Slide number: 1 -->

![](img/Ch3_图片1.jpg)
# 软件测试方法和技术
第3章 软件测试基本方法
同济大学  朱少民
版权所有©️ 仅限于教学使用

### Notes:

<!-- Slide number: 2 -->
# 第2章 回顾
软件缺陷是软件质量的对立面
软件缺陷(Bug)是什么
软件测试的分类：层次、类型和方法
静态测试与动态测试
主动测试与被动测试
黑盒测试与白盒测试
测试层次：单元、集成、系统和验收
软件测试工作范畴：测试需求分析、计划与设计、执行、结果评估

### Notes:

<!-- Slide number: 3 -->
3.1 基于直觉和经验的方法
3.2 基于输入域的方法
3.3 基于组合及其优化的方法
3.4 基于逻辑覆盖的方法
3.5 基于缺陷模式的测试
3.6 基于模型的测试
3.7 形式化测试方法
版权所有©️ 仅限于教学使用

### Notes:
3.1基于直觉和经验的方法	35
3.1.1 Ad-hoc测试方法和ALAC测试	36
3.1.2 错误推测法	37

3.2 基于输入域的方法	38
3.2.1 等价类划分法	38
3.2.2 边界值分析法	41

3.3 基于组合及其优化的方法	45
3.3.1 判定表方法	45
3.3.2 因果图法	47
3.3.3 Pair-wise方法	50
3.3.4 正交试验法	51

3.4 基于逻辑覆盖的方法	53
3.4.1 判定覆盖	54
3.4.2 条件覆盖	55
3.4.3 判定条件覆盖	56
3.4.4 条件组合覆盖	57
3.4.5 基本路径覆盖	59

3.5 基于缺陷模式的测试	62
3.5.1 常见的缺陷模式	64
3.5.2 DPBT的测试过程	65

3.6 基于模型的测试	65
3.6.1 功能图法	67
3.6.2 模糊测试方法	69

3.7 形式化测试方法	71
3.7.1 形式化方法
3.7.2 形式化验证
3.7.3 扩展有限状态机方法

<!-- Slide number: 4 -->
# 方法论和具体方法
从方法论看，更多体现了一种哲学的思想，例如辩证统一的方法，在测试中有许多对立统一体，如静态测试和动态测试、白盒测试和黑盒测试、自动化测试和手工测试等。
软件测试的方法论来源于软件工程的方法论，例如有面向对象的开发方法，就有面向对象的测试方法；有敏捷方法，就有和敏捷方法对应的敏捷测试。

![http://2.bp.blogspot.com/_JdybrokZBAk/Ri-geJwwj9I/AAAAAAAAAdI/Y7MBbIcHmPw/s320/colored_boxes.png](img/Ch3_Picture7.jpg)

### Notes:

<!-- Slide number: 5 -->
# 黑盒测试方法和白盒测试

![](img/Ch3_Picture64.jpg)

客户需求

输出
输入

事件驱动
结构化测试
逻辑驱动测试
基于需求的测试
数据驱动测试

### Notes:

<!-- Slide number: 6 -->
# 过去常提“黑盒和白盒”方法

等价类划分法
边界值分析法
判定表方法
因果图法
Pairwise方法
正交试验法
功能图法

语句覆盖
判定覆盖
条件覆盖
判定条件覆盖
条件组合覆盖
基本路径覆盖
结构化测试方法
白盒方法
黑盒方法
基于需求的测试方法

6

### Notes:

<!-- Slide number: 7 -->
# 方法论：测试方法
上下文驱动方法
基于需求验证的方法
基于场景的测试方法
基于模型的方法
基于经验的方法

![testing-and-test-automation-1.png](img/Ch3_图片2.jpg)

7

### Notes:

<!-- Slide number: 8 -->
# SWBOK对测试方法的分类
| 基于输入域的测试（IDBT） | 等价类、边界值、两两组合（pairwise）、随机测试 | 黑盒测试 |
| --- | --- | --- |
| 基于代码的测试 （CBT） | 基于控制流的标准、基于数据流的标准、CBT参考模型 | 白盒测试 |
| 基于故障模式的测试（FBT） | 故障模型、错误猜测法、变异测试 |  |
| 基于使用的测试（UBT） | 操作配置（operational profile）、用户观察启发 | 黑盒测试 |
| 基于模型的测试（MBT） | 决策表、有限状态机、形式化验证、TTCN3、工作流模型 |  |
| 基于应用特性的测试（TBNA） | OOS、web、real-time、SOA、embedded、safe-critical | 应用领域 |
8

### Notes:

<!-- Slide number: 9 -->
3.1 基于直觉和经验的方法
3.1.1 Ad-hoc测试方法和ALAC测试
3.1.2 错误推测法

### Notes:
3.2 基于输入域的方法
3.3 基于组合及其优化的方法
3.4 基于逻辑覆盖的方法
3.5 基于缺陷模式的测试
3.6 基于模型的测试
3.7 形式化测试方法

<!-- Slide number: 10 -->
# 3.1.1 ALAC测试和随机测试
ALAC，是Act-like-a-customer（象客户那样做）的简写，ALAC测试方法是一种基于客户使用产品的知识开发出来的测试方法，它的出发点是著名的Pareto 80/20规律

![3-19.gif](img/Ch3_Picture4.jpg)

### Notes:

<!-- Slide number: 11 -->
# 3.1.2 错误猜测法
错误推测法是测试者根据经验、知识和直觉来发现软件错误，来推测程序中可能存在的各种错误，从而有针对性的进行测试。
发现程序经常出现的错误的方法：
单元测试中发现的模块错误；
产品的以前版本曾经发现的错误；
输入数据为0或字符为空；
当软件要求输入时(比如在文本框中),不是没有输入正确的信息，而是根本没有输入任何内容，单单按了Enter键；
… …

### Notes:

<!-- Slide number: 12 -->
3.2 基于输入域的方法
3.2.1 等价类划分法
3.2.2 边界值分析法

### Notes:
3.2 基于输入域的方法
3.3 基于组合及其优化的方法
3.4 基于逻辑覆盖的方法
3.5 基于缺陷模式的测试
3.6 基于模型的测试
3.7 形式化测试方法

<!-- Slide number: 13 -->
# 3.2.1 等价类划分方法
等价类是某个输入域的子集，在该子集中每个输入数据的作用是等效的.
将输入数据分成若干个等价类，从每个等价类选取一个代表性的数据作为测试用例
等价类分为有效等价类（合理的数据）和无效等价类（异常的数据）

all inputs
i1

i4

i2

i3

<!-- Slide number: 14 -->
# 等价类划分方法应用示例

greater than range

in range

less than range

greater than value

less than value

value
输入条件规定了取值范围或值的个数，则可以划分为一个有效等价类和两个无效等价类
输入条件规定了输入值的集合，可以确立一个有效等价类和一个无效等价类
N个条件……

member of set
not member of set

<!-- Slide number: 15 -->
# 练习

![](img/Ch3_Picture4.jpg)

有效等价类如何划分？
无效等价类呢？
等价类1: Integer
等价类2: Decimal fraction
等价类3: Negative
等价类4: Invalid input

<!-- Slide number: 16 -->
# 3.2.2 边界值分析方法
BVA – Boundary Value Analysis
很多错误发生在输入或输出范围的边界上，因此针对各种边界情况设置测试用例，可以更有效地发现缺陷。
设计方法：
确定边界情况（输入或输出等价类的边界）
选取正好等于、刚刚大于或小于边界值作为测试数据

<!-- Slide number: 17 -->
# 示例1
如果输入条件规定了值的范围，则应取刚达到这个范围的边界的值，以及刚刚超越这个范围边界的值作为测试输入数据。

如果输入条件规定了值的个数，则用最大个数、最小个数、比最小个数少一、比最大个数多一的数作为测试数据。

a

b

（1,20]  即  1< x <= 20

a

b

{X} =（1，5，10，15，20）

<!-- Slide number: 18 -->
# 示例2
Test cases :
任意的正常值:      随机选择几个选项 边界值:   选择所有选项 边界值:   一个都不选边界值:  选择一个选项

<!-- Slide number: 19 -->
# 一些特殊的边界值
ASCII Table
| Character | ASCII Value | Character | ASCII Value |
| --- | --- | --- | --- |
| Null Space / 0 1 2 9 ; @ A | 0 32 47 48 49 50 57 58 64 65 | B Y Z [ ‘ a b y z { | 66 89 90 91 96 97 98 121 122 123 |
二进制
| Term | 取值范围 |
| --- | --- |
| Bit Nibble Byte Word Kilo Mega Giga Tera | 0 or 1 0-15 <Half byte> 0-255 0-65535 or 0-4294967295 1024 1048576 1073741824 1099511627776 |

<!-- Slide number: 20 -->
# 一些特殊的边界值 –续
First/last， First-1/Last+1
Min/Max，Min-1/max+1
Star/Finish， Start-1/Finish+1
Empty/Full
Less than empty/ more than full
Slower/Faster
Largest/Smallest
Over/Under， just Over/Just Under
Shortest/Longest
… …

数值
字符
位置
数量
速度
位置
体积

![5-1](img/Ch3_Picture4.jpg)
缺省值、空格、(none)、0、Null等

<!-- Slide number: 21 -->
# 练习
用边界值方法设计下列测试数据
Username
规则：12个字符以内，不能为空
   只能用字母、数字、_ 、-，不能用空格
   以字母开始
   大小写不敏感

2. Password
 规则：不少于6个字符
 大小写敏感

<!-- Slide number: 22 -->
3.3 基于组合及其优化的方法
3.3.1 判定表方法
3.3.2 因果图法
3.3.3 Pair-wise方法
3.3.4 正交试验法

<!-- Slide number: 23 -->
# 3.3.1 判定表方法
在实际应用中，许多输入是由多个因素构成，而不是单一因素，这时就需要多因素组合分析。
对于多因素，有时可以直接对输入条件（成立或不成立）进行组合设计，不需要进行因果分析，这时就采用判定表方法。
判定表由“条件和活动”两部分组成，即列出一个测试活动执行所需的条件组合，所有可能的条件（输入）组合定义了一系列的选择，而测试活动（结果输出）需要考虑每一个选择。

<!-- Slide number: 24 -->
# 判定表方法术语及应用
规则

条件桩：问题的所有条件
动作桩：针对问题所采取的动作
条件项：所列条件的具体赋值（输出）
动作项：在条件项组合情况下应采取的动作（输出）
规则：任何一个条件组合的特定取值及其相应的动作

![](img/Ch3_图片1.jpg)
条件桩
动作桩
最后每一列需要设计一条测试用例覆盖，有几条规则（组合）就有几条测试用例

### Notes:

<!-- Slide number: 25 -->
# 判定表组合优化讨论

![](img/Ch3_图片1.jpg)

条件桩
-
-
动作桩

### Notes:

<!-- Slide number: 26 -->
# 判定表方法示例
|  | ID | 项目名称 | R1 | R2 | R3 | R4 | R5 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 条件项 | C1 | 此商品在经营范围 | N | Y | Y | Y | Y |
|  | C2 | 此商品可以发货 | - | Y | Y | N | N |
|  | C3 | 此客户没有拖欠过付款 | - | Y | N | Y | N |
| 动作项 | A1 | 货到后允许客户转账 |  | 1 |  |  |  |
|  | A2 | 货到客户必须立即付款 |  |  | 1 |  |  |
|  | A3 | 重新组织货源 |  |  |  | 1 | 1 |
|  | A4 | 电话通知 |  |  |  | 1 |  |
|  | A5 | 书面通知 | 1 |  |  |  | 1 |

<!-- Slide number: 27 -->
# 3.3.2 因果图方法
针对更为复杂的“多种输入条件、产生多种结果”设计组合测试用例。
设计方法：
分析软件Spec描述的哪些是原因（输入条件）、哪些是结果（输出），给每个原因和结果赋予一个标示符。
找出原因与结果、原因与原因之间的对应关系，画出因果图
在因果图上标上哪些不可能发生的因果关系，表明约束或限制条件
根据因果图，创建（转化为）判定表，将复杂的逻辑关系转化为简单的组合矩阵
把判定表的每一列转化为测试用例。

<!-- Slide number: 28 -->
# 因果图的基本符号
有因必有果关系
非-关系：只有当因 i 不存在时，果 j 才出现
或-关系：如果因 i1 或因 i2 或……因 in 存在时，结果 j 才出现。
与-关系：只有当因 i1 与因 i2 与……因 in 同时存在时，结果 j 才出现。
i
j

i
j

i1

i2

j

in
i1

i2

j

in

<!-- Slide number: 29 -->
# 条件之间的关系
b1
b1
b1
a
a
a
.
.
.
.
.
.
.
.
.
E
I
O
R
M
IR
bn
bn
bn
b
b
b
E（互斥）：最多只能有一个条件被满足
I（包含）：至少有一个条件被满足
O（唯一）：正好（只能一个）条件满足
R（要求）：满足了条件 a 要求满足条件 b
M（屏蔽）：满足条件 a 隐含的要求不满足条件 b
IR（无关）：如果满足了条件 a，条件b 就无关重要了

<!-- Slide number: 30 -->
# 示例
A

B

C
E



D



E
R

（A or B or C） And (D or E)
| A | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 0 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| B | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 0 |
| C | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| D | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 1 |
| E | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 0 | 1 |
| 结果 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 |
（互斥）

（要求）

<!-- Slide number: 31 -->
# 因果图方法设计工具
BenderRBT Cause-Effect Graphing

![](img/Ch3_图片37.jpg)

![Bender2.png](img/Ch3_图片5.jpg)
http://www.benderrbt.com/bendersoftware.htm#over

<!-- Slide number: 32 -->
# 3.3.3 Pairwise方法
（两两组合）
背景：大部分缺陷是在两个变量取值冲突的测试时被发现的
处理的问题：多个变量、每个变量有多个取值的组合数太大（不再是条件成立、不成立两种情况）
定义：确保某个变量取值和另一个变量取值成对出现都会被覆盖
效果：可大幅度降低组合的数量

![](img/Ch3_图片5.jpg)

<!-- Slide number: 33 -->
# 5. Pairwise具体示例
开始两两组合设计
（两两组合）
A1、B1、C1
A1、B2、C2
A1、B3、C3
A：A1、A2、A3
B：B1、B2、B3
C：C1、C2、C3
A2、B1、C2
A2、B2、C3
A2、B3、C1
完全组合测试数是多少？
A3、B1、C3
A3、B2、C1
A3、B3、C2

<!-- Slide number: 34 -->
# Pairwise处理更复杂的情况
曝光值：-2.0、-1.5、-1、-0.5 和 +0.5、+1、+1.5、+2
白平衡：白炽灯、荧光灯、闪光灯、阴天等
感光度：自动，100，200，400，800，1600，3200
 分辨率：低，中，高，超高
效果：无，负片，灰度，深褐色

![屏幕快照 2014-09-07 下午3.55.38.png](img/Ch3_图片4.jpg)
Pairwise：8*7 = 56
56/3584 = 1.56%
完整组合：8*4*7*4*4 = 3584

<!-- Slide number: 35 -->
# Pairwise方法来自于经验数据
大部分缺陷是在两个变量取值冲突的测试时被发现的，而不需要测试所有的完整组合

![屏幕快照 2014-09-08 下午3.25.10.png](img/Ch3_图片1.jpg)

![屏幕快照 2014-09-08 下午3.30.42.png](img/Ch3_图片3.jpg)

### Notes:
http://msdn.microsoft.com/en-us/library/cc150619.aspx
https://hexawise.com/case-studies/bcbsnc

<!-- Slide number: 36 -->
# Pairwise方法来自于经验数据 – 续

![屏幕快照 2015-03-23 下午4.45.04.png](img/Ch3_图片2.jpg)

不同强度的组合故障覆盖率

### Notes:
http://msdn.microsoft.com/en-us/library/cc150619.aspx
https://hexawise.com/case-studies/bcbsnc

<!-- Slide number: 37 -->
# Pairwise方法工具

![temp.png](img/Ch3_图片3.jpg)
http://www.pairwise.org/tools.asp

### Notes:
http://msdn.microsoft.com/en-us/library/cc150619.aspx
https://hexawise.com/case-studies/bcbsnc

<!-- Slide number: 38 -->
# Pairwise工具推荐:ACTS

![](img/Ch3_图片5.jpg)

### Notes:
http://msdn.microsoft.com/en-us/library/cc150619.aspx
https://hexawise.com/case-studies/bcbsnc

<!-- Slide number: 39 -->
# 3.3.4 正交实验法

![](img/Ch3_图片4.jpg)
处理的问题：和Pairwise类似
依据与思想：依据Galois理论，从大量的（实验）数据（测试例）中挑选适量的、有代表性的点（条件组合），从而合理地安排实验（测试）的一种科学实验设计方法
确定影响功能的因子与状态
选择一个合适的正交表
利用正交表构造测试数据集
正交实验法
Orthogonal experimental design
正交表
https://www.york.ac.uk/depts/maths/tables/orthogonal.htm

### Notes:

<!-- Slide number: 40 -->
# 正交实验法示例
与两两组合一致
A1、B1、C1
A1、B2、C2
A1、B3、C3

![](img/Ch3_图片2.jpg)
A2、B1、C2
A2、B2、C3
A2、B3、C1
A3、B1、C3
A3、B2、C1
A3、B3、C2

### Notes:

<!-- Slide number: 41 -->
# 正交表生成工具

![Design Wizard](img/Ch3_Picture2.jpg)

![Design Wizard](img/Ch3_Picture4.jpg)

![L8 Array](img/Ch3_Picture6.jpg)
https://www.weibull.com/hotwire/issue131/hottopics131.htm

### Notes:
https://support.minitab.com/en-us/minitab/21/help-and-how-to/statistical-modeling/doe/supporting-topics/basics/orthogonal-designs/

<!-- Slide number: 42 -->
# 小结
等价类划分

边界值分析
单因素

多因素
静态
因果分析法

决策表
正交试验法

基于需求的测试方法
功能图

有限状态机
动态
其它
错误推测法

### Notes:

<!-- Slide number: 43 -->
3.4 基于逻辑覆盖的方法
3.4.1 判定覆盖
3.4.2 条件覆盖
3.4.3 判定条件覆盖
3.4.4 条件组合覆盖
3.4.5 基本路径覆盖

<!-- Slide number: 44 -->
# 结构化测试方法
语句覆盖
判定覆盖
条件覆盖
判定/条件覆盖
条件组合覆盖
MC/DC覆盖
基本路径覆盖

![](img/Ch3_Picture64.jpg)

### Notes:

<!-- Slide number: 45 -->
# 逻辑覆盖 vs. 路径覆盖
逻辑覆盖：以程序或系统的内部逻辑结构为基础，分为语句覆盖、判定覆盖、判定-条件覆盖、条件组合覆盖等；
基本路径测试：在程序或业务控制流程的基础上，分析控制构造的环路复杂性，导出基本可执行路径集合，从而设计出测试用例。

### Notes:

<!-- Slide number: 46 -->
# （代码行）语句覆盖
设计若干测试用例，运行被测程序，使程序中的每个可执行语句至少被执行一次
a

IF
3
b

c
4

d
ENDIF
5

e
IF
6
f

j
7

h
ENDIF
8

i
9
程序源代码
1.	dim a, b as integer
dim c as double
if (a >0 and b > 0) then
     c = c / a
end if
if (a > 1 or c > 1) then
     c = c + 1
end if
c = b + c
程序控制流图
(a, b ,c)= (1, 1, 2)

覆盖

### Notes:

<!-- Slide number: 47 -->
# 语句覆盖不能发现的问题
程序源代码
1.	dim a, b as integer
dim c as double
if (a >0 or b > 0) then
     c = c / a
end if
if (a > 1 and c > 1) then
     c = c + 1
end if
c = b + c
程序源代码
1.	dim a, b as integer
dim c as double
if (a >0 and b > 0) then
     c = c / a
end if
if (a > 1 or c > 1) then
     c = c + 1
end if
c = b + c

如果开发写错了
and
or
(a, b ,c)= (1, 1, 2)

### Notes:

<!-- Slide number: 48 -->
# 3.4.1 判定/分支覆盖
判定覆盖：设计若干用例，运行被测程序，使得程序中每个判断的取真分支和取假分支至少经历一次，即判断真假值均曾被满足。
一个判定代表着程序的一个分支，所以判定覆盖也被称为分支覆盖。
(a, b ,c)= (1, 1, 2)

![WhiteBoxTestCase](img/Ch3_Picture2.jpg)
(a, b ,c)= (-1, 1, 0)

### Notes:

<!-- Slide number: 49 -->
# 3.4.2 条件覆盖
条件覆盖的基本思想是设计若干测试用例，执行被测程序以后，要使每个判断中每个条件的可能取值至少满足一次。

a>0

b>0
（a>0 and b>0）
条件

### Notes:

<!-- Slide number: 50 -->
# 示例：列出所有条件

![WhiteBoxTestCase1](img/Ch3_Picture2.jpg)
判定M：
条件a>0： 取.T.时为T1
取.F.时为F1
条件b>0： 取.T.时为T2
取.F.时为F2；

判定N：
条件a>1： 取.T.时为T3
取.F.时为F3
条件c>1： 取.T.时为T4
取.F.时为F4

![WhiteBoxTestCase](img/Ch3_Picture3.jpg)

<!-- Slide number: 51 -->
# 示例续：覆盖所有条件

![WhiteBoxTestCase](img/Ch3_Picture3.jpg)
(a, b ,c)= (2, -1, 0)
T1, F2, T3, F4
(a, b ,c)= (-1, 1, 2)
F1, T2, F3, T4
但有什么问题吗？

<!-- Slide number: 52 -->
# 3.4.3 判定-条件覆盖
判定-条件覆盖是判定和条件覆盖设计方法的交集，即设计足够的测试用例，使得判断条件中的所有条件可能取值至少执行一次，同时，所有判断的可能结果至少执行一次

| 条件 | 取值 | 覆盖条件 | 分支 | 覆盖判定 |
| --- | --- | --- | --- | --- |
| a>0, b>0, a>1，c>1 | (a, b ,c)= (2, 1, 2) | T1，T2，T3，T4 | a>0 AND b>0 | M=.T. N=.T. |
| a<=0, b<=0, a<=1, c<=1 | (a, b ,c)= (-1, 0, 1) | F1，F2，F3，F4 | a>1 OR c>1 | M=.F. N=.F. |

### Notes:

<!-- Slide number: 53 -->
# 3.4.4 条件组合测试
条件组合覆盖的基本思想是设计足够的测试用例，使得判断中每个条件的所有可能至少出现一次，并且每个判断本身的判定结果也至少出现一次。
它与条件覆盖的差别是它不是简单地要求每个条件都出现“真”与“假”两种结果，而是要求让这些结果的所有可能组合都至少出现一次
.T.  .T.    (1, 1)
.T.  .F.    (1, -1)
.F.  .T.    (-1, 1)
.F.  .F.    (-1, -1)

（a>0 and b>0）

### Notes:

<!-- Slide number: 54 -->
# 组合覆盖 vs 路径覆盖

![WhiteBoxTestCase1](img/Ch3_Picture2.jpg)
| 测试用例 | 覆盖条件 | 覆盖路径 | 覆盖组合 |
| --- | --- | --- | --- |
| 输入：a=2，b=1，c=6 输出：a=2，b=1，c=5 | T1，T2，T3，T4 | P1（1-2-4） | 1，5 |
| 输入：(a,b,c)=(2,-1,-2) 输出：(a,b,c)=(2,-1,-2) | T1，F2，T3，F4 | P3（1-3-4） | 2，6 |
| 输入：(a,b,c)=(-1,2,3) 输出：(a,b,c)=(-1,2,6) | F1，T2，F3，T4 | P3（1-3-4） | 3，7 |
| 输入：(a,b,c)=(-1,-2,-3) 输出：(a,b,c)=(-1,-2,-5) | F1，F2，F3，F4 | P4（1-3-5） | 4，8 |

覆盖了所有组合，但覆盖路径有限，1-2-5 没被覆盖

### Notes:

<!-- Slide number: 55 -->
# 问题
条件组合效率不高，有些测试是不必要的
判定/条件 还不够强
.T.  .T.    (1, 1)
.T.  .F.    (1, -1)
.F.  .T.    (-1, 1)
.F.  .F.    (-1, -1)

（a>0 and b>0）

<!-- Slide number: 56 -->
# 修正条件/判定覆盖（MC/DC）
每个判定的所有可能结果至少能取值一次；
判定中的每个条件的所有可能结果至少取值一次；
 一个判定中的每个条件独立地对结果产生影响；
每个入口和出口至少执行一次
.T.  .T.    (1, 1)
.T.  .F.    (1, -1)
.F.  .T.    (-1, 1)

（a>0 and b>0） 会有多少条用例？
>= n+1 test cases for a decision with n inputs.
http://www.dsl.uow.edu.au/~sergiy/MCDC.html
http://en.wikipedia.org/wiki/Modified_Condition/Decision_Coverage

<!-- Slide number: 57 -->
# 3.4.5 基本路径覆盖
设计所有的测试用例，来覆盖程序中基本的执行路径。
| 测试用例 | 覆盖路径 | 覆盖条件 | 覆盖组合 |
| --- | --- | --- | --- |
| 输入：a=2，b=1，c=6 输出：a=2，b=1，c=5 | P1（1-2-4） | T1，T2，T3，T4 | 1，5 |
| 输入：a=1，b=1，c=-3 输出：a=1，b=1，c=-2 | P2（1-2-5） | T1，T2，F3，F4 | 1，8 |
| 输入：a=2，b=-1，c=-2 输出：a=2，b=-1，c=-2 | P3（1-3-4） | T1，F2，T3，F4 | 2，6 |
| 输入：a=-1，b=2，c=3 输出：a=-1，b=2，c=6 | P3（1-3-4） | F1，T2，F3，T4 | 3，7 |
| 输入：a=-1，b=-2，c=-3 输出：a=-1，b=-2，c=-5 | P4（1-3-5） | F1，F2，F3，F4 | 4，8 |

### Notes:

<!-- Slide number: 58 -->
# 基本路径覆盖的设计过程

依据代码绘制流程图
确定流程图的圈复杂度（cyclomatic complexity ）
确定线性独立路径的基本集合( basis set )
设计测试用例覆盖每条基本路径

### Notes:

<!-- Slide number: 59 -->
# 示例 – 从源代码到流程图

1
2
3
6
4
7
8
5
9
10

11
Procedure: process records

1.	Do While records remain
2.		Read record;
3.		If record field 1 = 0 Then
4.			store in buffer;
5.			increment counter;
6.		Else If record field 2 = 0 Then
7.				reset counter;
8.			Else store in file;
9.			End If
10.		End If
11.	End Do
End

### Notes:

<!-- Slide number: 60 -->
# 流程图简化
1
2,3
6
9
8
7
4,5
10
11

1
2
3
6
4
7
8
5
9
10

11

### Notes:

<!-- Slide number: 61 -->
# 计算圈复杂度
圈复杂度（Cyclomatic complexity）: 代码逻辑复杂度的度量，提供了被测代码的路径数量。复杂度越高，出错的概率越大

modules

V(G)

  V(G) = 区域数量(由节点、连线包围的区域，包括图形外部区域)
  V(G) = 连线数量 - 节点数量 + 2
  V(G) = 简单可预测节点数量 + 1

### Notes:
2.	Determine the cyclomatic complexity of the resultant flow graph
	Note:	can be determined without developing a flow graph
			count all conditional statements in a component
				compound conditions count as 2
				(number of Boolean operators + 2)

<!-- Slide number: 62 -->
# 圈复杂度计算示例
1
Region 1
2,3
6
9
7
8
4,5
Region 2
Region 3
10

11
Region 4
V(G)=4
11 - 9 + 2 = 4

### Notes:

<!-- Slide number: 63 -->
# 确定独立路径集合
独立路径：至少引入一系列新的处理语句或条件的任何路径
基本集：由独立路径构成的集合
由基本集导出的测试用例，保证每行代码语句至少被执行一次
基本集合不一定唯一
不需要活动图, 但最好绘制程序流程图
最好每个单元都进行基本路径测试，对关键组件则是必要的

### Notes:
3.	Determine a basis set of linearly independent paths
equal to cyclomatic complexity number
identify predicate nodes as an aid in derivation of test cases

<!-- Slide number: 64 -->
# 示例：基本路径测试用例
保证每条基本路径被执行一次

1
2
3
6
4
8
7
5
9
10

11

 Path1: 1-2-3-6-7-9-10-1-11

 Path2: 1-2-3-6-8-9-10-1-11
 Path3: 1-2-3-4-5-10-1-11
Path4: 1-11

### Notes:

<!-- Slide number: 65 -->
# 逻辑覆盖小结
语句覆盖

判定覆盖DC
基本路径覆盖BPC
条件覆盖CC

条件/判定覆盖CC/DC

MC/DC

条件组合覆盖MCC
Condition Coverage (CC)
Decision Coverage (DC)
Multiple Condition Coverage (MCC)
Modiﬁed Condition/Decision Coverage (MC/DC)

<!-- Slide number: 66 -->
# 拓展
数据流覆盖：数据流程图、代码中变量的定义与引用
控制流覆盖：业务流程基本路径覆盖，代码中的逻辑覆盖

<!-- Slide number: 67 -->
3.5 基于缺陷模式的测试
3.5.1 常见的缺陷模式
3.5.2 DPBT的自动化实现

<!-- Slide number: 68 -->
# 3.5.1 常见的缺陷模式
故障模型
安全漏洞模型
性能模型
并发故障模型
不良习惯模型
代码国际化模型
易诱骗代码模型

![http://vif.tugraz.at/uploads/pics/model-based_02.jpg](img/Ch3_Picture4.jpg)

### Notes:

<!-- Slide number: 69 -->
# 3.5.2 DPBT的自动化实现
DPBT：Defect-Pattern-Based Testing
预处理/预编译
词法分析(Lexical Analysis)
语法分析( Parsing) 和语义处理( Semantic Analysis)
抽象语法树生成
控制流图生成
IP 扫描
人工确认

### Notes:

<!-- Slide number: 70 -->
实现的通用框架
函数调用
Mod-effect

被测源程序
抽象解释
SSA
解析
抽象
语法树
多态分析
数据流等基本分析方法
符号执行
指向分析
全局变量分析
前后支配
图可达
程序状态空间
SMT
OWASP
CWE
基于缺陷模式的
逻辑表达式
缺陷模式
逻辑表达式求解
CERT
检测结果
SSA：Static Single-Assignment
SMT：satisfiability modulo theories
CWE：Common Weakness Enumeration
Handbook of satisfiability. Vol. 185. IOS press, 2009

### Notes:
CWE（Common Weakness Enumeration，通用缺陷枚举），是一个安全漏洞词典,是由美国国土安全部国家计算机安全部门资助的软件安全战略性项目，枚举了上千种最新的漏洞(缺陷)模式，通过该认证代表了产品或服务与“CWE”兼容，证明产品能够支持国际上主要漏洞(缺陷)模式的检测
布尔可满足性问题（Boolean satisfiability problem；SAT ）属于决定性问题，也是第一个被证明属于NP完全的问题
SMT求解器也被集成到一些大型工具中,比如HOL/Isabelle、ESC/Java2、ACL2、UCLID、BLAST、ureka,CUTE和PEX等.

<!-- Slide number: 71 -->
3.6 基于模型的测试
MBT：Model-based testing
3.6.1 功能图法
3.6.2 模糊测试方法

<!-- Slide number: 72 -->
# 什么是MBT？

![屏幕快照 2017-04-26 上午8.33.46.png](img/Ch3_图片3.jpg)
基于模型的测试 (MBT, Model-based testing)：通过构建能够正确描述被测软件系统功能特性的模型，然后基于这个模型产生测试用例并执行这些测试用例的过程

### Notes:
“模糊测试方法、变异测试” 在介绍安全性测试时已讨论过

<!-- Slide number: 73 -->
# MBT基本原理（实施过程）

![](img/Ch3_Picture2.jpg)
为被测试系统（SUT）建模
基于模型产生测试用例
将抽象的测试具体化使测试用例具有可执行性
执行测试
分析测试结果

<!-- Slide number: 74 -->
MBT 架构

![TEMA model achitecture.png](img/Ch3_图片5.jpg)

<!-- Slide number: 75 -->
# 常见的MBT方法
有限状态机（finite state machines，FSM），包括扩展的有限状态机（EFSM）
符号执行(Symbolic Execution) 是指一种使用符号值代替数字值执行程序的程序分析技术
定理证明（Theorem proving）通过一组能够明确定义系统行为的逻辑表达式 （谓词）来完成模型构建
模型检验（Model checking）对属性的测试，如果属性在模型中是有效的，模型检验能发现证据或反例
随机／半随机模型（如模糊测试方法、变异测试、马尔科夫链）
其它方法：基于UML的MBT、因果图方法等

### Notes:
约束逻辑编程和符号执行（Constraint logic programming and symbolic execution），约束编程可用于选择测试用例，这是通过求解一组变量之上的约束以满足特定的约束
随机／半随机模型，完成一些不确定性的测试，包括模糊控制器（Fuzz Controller）、马尔科夫链（Markov chain）等。
变异测试（mutation-based fuzzers）生成测试（generation-based fuzzers）

<!-- Slide number: 76 -->
# 3.6.1 功能图法
每个程序的功能通常由静态说明和动态说明组成
静态说明描述了输入条件和输出条件之间的对应关系
动态说明描述了输入数据的次序或者转移的次序
功能图法就是为了解决动态说明问题的一种测试用例的设计方法
功能图由状态迁移图（state transition diagram，STD）和逻辑功能模型（logic function model， LFM）构成

### Notes:

<!-- Slide number: 77 -->
# 状态迁移图
状态迁移图，描述系统状态变化的动态信息——动态说明，由状态和迁移来描述，状态指出数据输入的位置（或时间），而迁移则指明状态的改变

![6-10](img/Ch3_Picture5.jpg)

### Notes:

<!-- Slide number: 78 -->
# 如何设计测试用例？
功能图法设计测试用例，就是如何覆盖软件所表现出来的所有状态，可以转化为两个层次的测试用例
从功能逻辑模型（决策表或因果图）导出局部测试用例，覆盖各个状态的各种输入数据的组合
从状态迁移图导出整体的测试用例，以覆盖系统（程序）控制的逻辑路径
功能图法是综合运用黑盒方法和白盒方法来设计测试用例，即整体上选用白盒方法——路径覆盖、分支和条件覆盖等，而局部上选用的是黑盒方法——决策表或因果图方法

### Notes:

<!-- Slide number: 79 -->
# 3.6.2 模糊测试方法
Fuzz Testing

![http://fuzzing.org/wp-content/book_cover.jpg](img/Ch3_Picture4.jpg)
模糊测试：在一个被测试程序中附加上随机数据（fuzz）作为程序的输入。如果被测试程序出现问题（例如 Crush ,或者异常退出），就可以定位程序的缺陷。
模糊测试的巨大优势：测试设计极其简单，系统的行为先入为主。
79

<!-- Slide number: 80 -->
# 几种不同模糊器的构造
黑盒随机模糊，对正确格式的输入数据进行随机变异，然后用这些变异的输入运行程序，看是否能够触发异常。
基于语法的模糊，是模糊复杂格式输入的替代方法，需要指定输入格式的输入语法、哪些输入部分要进行模糊化以及如何模糊化。
白盒模糊处理，由微软研究院于2008年首创，这种方法包括：动态地执行被测程序，从执行过程中遇到的条件分支收集输入约束。然后，系统地逐个否定所有这些约束，并使用约束求解器求解，其解被映射到执行不同程序执行路径的新输入。使用系统搜索技术重复这个过程，试图扫描程序的所有可行的执行路径。
80

### Notes:
黑盒随机模糊，对正确格式的输入数据进行随机变异，然后用这些变异的输入运行程序，看是否能够触发异常。这是一种简单的hack，如果一个应用从未进行过模糊测试，可以用这种技术有效地发现应用中的漏洞。
基于语法的模糊，是模糊复杂格式输入的替代方法，需要指定输入格式的输入语法，还指定哪些输入部分要进行模糊化以及如何模糊化。基于语法的模糊生成器会生成许多新的输入，每个输入满足语法编码的约束。基于语法的fuzzing通过模糊生成器的用户的创造力和专业知识来指导fuzzing。
白盒模糊处理，由微软研究院于2008年首创，这种方法包括：动态地执行测试下的程序，并从执行过程中遇到的条件分支收集输入约束。然后，系统地逐个否定所有这些约束，并使用约束求解器求解，其解被映射到执行不同程序执行路径的新输入。使用系统搜索技术重复这个过程，试图扫描程序的所有可行的执行路径。与黑盒随机模糊相比，白盒模糊通常更精确，可以运行更多的代码，从而发现更多的bug。

<!-- Slide number: 81 -->
# American fuzzy lop方法
AFL是一款开源的模糊测试工具，是当今使用最广泛的Fuzzer，这个工具在程序执行前对程序源码进行插桩（instrumentation），以便在程序执行过程中实时获取程序的执行情况。AFL采用遗传算法对程序的输入进行变异能够在程序运行的时候注入自己的代码， 然后自动产生测试用例进行模糊测试。简化一下，整个算法可以总结为：
将用户提供的初始测试用例加载到队列中。
从队列中获取下一个输入文件。
试图将测试用例修剪到不改变程序测量行为的最小尺寸。
使用均衡的、经过充分研究的各种传统模糊策略，重复地对文件进行变异。
如果任何产生的变异导致插桩记录新的状态转换，将变异的输出作为一个新的条目添加到队列中。
转到第2步
https://afl-1.readthedocs.io/en/latest/
https://github.com/google/AFL

<!-- Slide number: 82 -->
# 变异测试
mutation testing
变异测试（Mutation Testing）是一种在细节方面改进程序源代码的软件测试方法。变异操作是模拟典型应用错误（定位代码的弱点）、或强制产生有效地测试

![](img/Ch3_图片11.jpg)

![](img/Ch3_图片10.jpg)

![](img/Ch3_图片8.jpg)

<!-- Slide number: 83 -->
# 变异测试的方法与流程

![](img/Ch3_图片11.jpg)

![](img/Ch3_图片7.jpg)

<!-- Slide number: 84 -->
3.7 形式化方法
3.7.1 形式化方法
3.7.2 形式化验证
3.7.3 扩展有限状态机方法

<!-- Slide number: 85 -->
# 3.7.1 形式化方法
形式化方法:基于数学的方法（数学表示、精确的数学语义）来描述目标软件系统属性的一种技术
形式化规范说明语言的构成：语法、语义和一组关系
形式化方法可应用在软件规格和验证之上，包括软件系统的精确建模和软件规格特性的具体描述，即可以看作是面向模型的形式化方法和面向属性的形式化方法

可参考：
http://en.wikipedia.org/wiki/Formal_method

### Notes:

<!-- Slide number: 86 -->
# 示例
巴科斯范式（Backus–Naur Form, BNF)

![BNC.png](img/Ch3_图片6.jpg)

### Notes:

<!-- Slide number: 87 -->
# 形式化三部曲

![http://www.cse.chalmers.se/research/hats/sites/default/files/IntegrativeTechnology.png](img/Ch3_Picture2.jpg)
形式化描述
形式化开发
形式化验证

### Notes:

<!-- Slide number: 88 -->
# 形式化的具体方法
基于模型的方法，如Z语言、B语言等
代数方法，如OBJ、CLEAR、ASL、ACT等
过程代数方法，如CSP、CCS、ACP、LOTOS、TPCCS等
基于逻辑的方法，如区间时序逻辑、Hoare 逻辑、模态逻辑、时序逻辑、时序代理模型等。
基于网络的方法

### Notes:

<!-- Slide number: 89 -->
# 3.7.2 形式化验证
形式化验证，就是根据某些形式规范或属性，使用形式逻辑方法证明其正确性或非正确性。
一般通过形式化规范进行分析和推理，研究它的各种静态和动态性质，验证是否一致、完整，从而找出所存在的错误和缺陷。
无法证明某个系统没有缺陷，因为不能定义 “没有缺陷”。只能证明一个系统不存在我们可以想得到的缺陷，以及验证满足系统质量要求的属性

### Notes:

<!-- Slide number: 90 -->
# 形式化验证的一些具体方法
多数是基于模型的，也可以归为MBT方法
有限状态机（FSM）或扩展有限状态机（EFSM）
SPIN和线性时态语言
UML 语义转换
标准RBAC模型
扩展的RBAC模型和基于粒计算的RBAC模型
符号模型检验
BAN逻辑模型

### Notes:

<!-- Slide number: 91 -->
# 有限状态机
有限状态机（ Finite State Machine ，FSM）是对象行为建模的工具，以描述对象在其生命周期内所经历的状态序列，以及如何响应来自外界的各种事件

![3-14.gif](img/Ch3_Picture4.jpg)

<!-- Slide number: 92 -->
# 示例：状态图
一个堆栈的状态图(state diagram)

top

push
*

pop
 [height> 1]

push
 [height < max-1]
top

init

push

push
[height = max-1]

filled
full
empty

pop
 [height= 1]
pop

delete

Initial and final state
说明

state transition

state
Name
来源: nach Spillner, Linz: Basiswissen Softwaretest, 2005

<!-- Slide number: 93 -->
# 状态图转化为树结构、生成测试用例

 initial

init

pop

   ERROR

empty

delete

top

   ERROR

push
  deleted

  filled

delete

   ERROR

pop
top

push
push
pop

empty
  filled
full
 filled
 filled

delete

   ERROR

push
*
pop

top

full
full
filled

<!-- Slide number: 94 -->
# 状态图工具：Spec Explorer

![Spec Explorer 2010 Visual Studio Power Tool](img/Ch3_Picture4.jpg)

![http://blogs.msdn.com/blogfiles/sechina/WindowsLiveWriter/7607f00c44f6_9970/image_12%5B1%5D_2.png](img/Ch3_Picture2.jpg)

<!-- Slide number: 95 -->
# 示例：ATS4_AppModel

![MBT-ATS4.png](img/Ch3_图片5.jpg)
http://ats4appmodel.sourceforge.net/

<!-- Slide number: 96 -->
# 补充：基于场景的测试方法
测试用例 = 用户故事（行为） + 场景 + 测试数据
场景：条件、前提、运行环境等

场景

数据

![](img/Ch3_图片3.jpg)

### Notes:

<!-- Slide number: 97 -->
# 示例：基于场景的测试
  用户	               	 上下文(场景)		           目标
首次安装使用
特定时间打开App（12:00/ 20:00）
预定成功后
取消订单后
退出App后

入门级用户
熟练用户
随便看看
查找符合自己要求的酒店
预定酒店
入住酒店
离开酒店

<!-- Slide number: 98 -->
# 练习：列出测试场景和数据

![](img/Ch3_图片4.jpg)
针对某典型用例列出测试场景和测试数据

场景

数据

98

### Notes:
针对刚才完成的用户故事，拿出3个不同类型的US进行切分

<!-- Slide number: 99 -->
# 事件流图
作为承兑人，根据委托收款请求，签发承兑

无条件支付？不得转让？已转让了吗？收款人清楚吗？收款人是否破产？金额超过上限？

超过上限
已转让
有条件支付

不得
转让

不符合条件
收款人破产
99

### Notes:
票据的自助式受理，完成票据的存入、存储、记账
功能上要考虑身份认证、防伪识别

<!-- Slide number: 100 -->
# 基于场景的测试方法 – 示例
正常场景 从账户中成功取款
可选场景：无法取款,因为:
用户的银行卡号被拒绝,因为银行卡无法被 ATM 机识别
用户三次以上都没能正确地输入密码。
用户三次或三次以上都没能正确地输入密码,ATM 机发生吞卡
用户选择了存款或转账功能,而不是取款功能
用户在插入的卡上选择了一个非正确的账户
用户的取款数额不正确
ATM机的现金不足
用户输入了一个不存在的数额
用户输入的数额超出了每日的取款限额
用户银行卡账户的余额不足

100

<!-- Slide number: 101 -->
# 基于场景的测试方法 – 示例（续）

![](img/Ch3_图片6.jpg)
101

<!-- Slide number: 102 -->
# 基于场景的测试方法 – 示例（续）
成功地从账户中提取现金 (覆盖 U1,S1.1,U2,S2.1,U3.1,U4, S4.1,U5,S5.1,S6,S7,S8,S9,U6)
用户银行卡无法被ATM机识别 (覆盖U1,S1.2,S9)
用户输入密码不正确<3 次 (覆盖 U1,S1.1,U2,S2.2)
3 次输入用户密码不正确 (覆盖 U1,S1.1,U2,S2.2,U2,S2.3,S3)
ATM 机中现金不足 (覆盖 U1, S1.1, U2, S2.1, U3.1, U4,S4.1,U5, S5.3)
用户账户余额不足(覆盖 U1, S1.1, U2,S2.1, U3.1, U4, S4.1,U5, S5.6)
用户输入的取款金额不正确 (覆盖 U1, S1.1,U2, S2.1, U3.1, U4, S4.1, U5, S5.2)
用户输入的密码不正确 > 3 次 (覆盖 U1,S1.1,U2, S2.2, U2, S2.2,U2,S2.3,S3)
用户输入一个不存在的数额 (覆盖 U1, S1.1, U2,S2.1, U3.1, U4,S4.1, U5,S5.4)
用户输入的金额超出了日取款限制(覆盖 U1, S1.1, U2,S2.1,U3.1,U4, S4.1, U5, S5.5)
…… 用户选择存款或转账 (覆盖 U1, S1.1,U2, S2.1, U3.2, S10)
102

<!-- Slide number: 103 -->
语句覆盖

![](img/Ch3_图片1.jpg)
| 测试用例名称 | 测试用例描述 | 测试路径 |
| --- | --- | --- |
| CASE1 | 投保成功：年龄20，男性，健康体、有医疗保险 | ABC |
| CASE2 | 投保成功：年龄20，男性，非健康体且没有基本医疗 | ABE |
判定覆盖
| CASE3 | 投保成功：年龄20，男性，健康体，有医疗保险 | 判定A=“真” 判定B=“真” |
| --- | --- | --- |
| CASE4 | 投保不成功：年龄15，男性 | 判定A=“假” |
| CASE5 | 投保成功：年龄20，男性，健康体，没有医疗保险 | 判定A=“真” 判定B=“假” |
请参考《软件测试实验教程》（清华大学出版社，2019）

<!-- Slide number: 104 -->
完成条件覆盖设计

![](img/Ch3_图片2.jpg)
条件覆盖

| 测试用例名称 | 测试用例描述 | 测试条件 |
| --- | --- | --- |
| CASE1 |  |  |
| CASE2 |  |  |
| CASE3 |  |  |
请参考《软件测试实验教程》（清华大学出版社，2019）

### Notes:
的朋友戴比上学老是迟到，她想改变这个糟糕的情况，请你提建议。你需要从戴比那儿获得哪些信息才能给她一个好的建议？
在老师引导下，孩子们会重点考虑：为什么戴比会经常迟到？或者说，让她迟到的因素有哪些，这些因素哪些能有改变，哪些无法改变？能改变的因素，改进方法有哪些

<!-- Slide number: 105 -->
# 本章小结
方法论：黑盒方法（基于需求的测试方法）、结构化方法（逻辑覆盖和基本路径覆盖）、基于场景的方法
数据流覆盖：数据流程图、代码中变量的定义与引用
控制流覆盖：业务流程基本路径覆盖，代码中的逻辑覆盖
最常用的方法：等价类划分、边界值分析、决策表、Pairwise等
不同层次的覆盖：代码、功能/非功能、业务
最常用的覆盖标准：语句覆盖、分支覆盖和MC/DC覆盖

<!-- Slide number: 106 -->
# 思考题
为何在航空航天应用软件中会使用MC/DC代码覆盖标准？
为什么敏捷测试中适合使用基于场景的测试设计方法？

### Notes:
重点学习内容，可以通过留实操作业或提问的方式，巩固学习成果

<!-- Slide number: 107 -->
# 作业一
1. Testwell CTC++
2. CoverageMeter
3. BullseyeCoverage
4. GCT
5. CppUnit
6. Dynamic Code Coverage
7. TCAT C/C++
8. COVTOOL
9. gocv
10. xCover

![屏幕快照 2014-03-13 下午1.12.49.png](img/Ch3_图片9.jpg)
DC/CC

MC/DC

+
BPC
找一合适的函数代码 + 选择一覆盖率工具 – 完成三种覆盖率的测试

<!-- Slide number: 108 -->
作业二
针对下列因素，使用工具ACTS完成不同强度的组合测试，如果存在约束条件，需要添加后进行计算：
驾驶记录: 过去五年内没有违规，过去三年内没有违规, 过去三年内违规小于3次, 过去三年内违规3次或三次以上、过去一年内违规3次或三次以上。
汽车型号：一般国产车、高档国产车（>=20万）、进口车、高档进口车（>=100万）
使用汽车的方式：出租车、商务车、私家车
所住的地区：城市中心地带、市区、郊区、农村
受保的项目：全保，自由组合、最基本保险
司机的驾龄：<=1年、<=3年、<=5年、<=10年、>10年
保险方式：首次参保、第2次参保、连续受保（>=3次）

<!-- Slide number: 109 -->
# 感 谢 聆 听
朱少民 / 同济大学

### Notes:
每课结束时使用“以上是本节课的内容”“这一章讲到这里”