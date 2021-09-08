<!--
 * @Author: your name
 * @Date: 2021-09-05 10:18:55
 * @LastEditTime: 2021-09-09 00:25:05
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \AI-learing\README.md
-->

# AI-learning

学校大三开的人工智能课程

## 绪论

### 什么是人工智能

**AI 至今没有统一的定义**
AI 使一部机器的反应方式就像是一个人在行动时所依据的智能
AI 是关于知识的科学，即怎样表示知识、获取知识和使用知识的科学
AI 研究如何使计算机去做过去只有人才能做的富有智能的工作
AI 是让机器做本需要人的智能才能做到的事情的一门学科
AI 是一个知识信息处理系统

### 人工智能的定义

人工智能是一门研究如何制造出人造的智能机器或智能系统，来模拟人类智能活动的能力，以延伸人们智能的科学

### 智能的概念

源于拉丁“Legere”，意思是收集、汇集，智能通常用来表示从中进行选择、理解和感觉
**智能的定义和描述**：
（1）善于判断、理解和推理
（2）综合智力——主要是指“相互关系的训练”
（3）形成要领和掌握含义的能力
（4）全面考试的能力或思维的效率
（5）先天的、综合的和认知的能力
（6）智力活动包括在某一情况下抓住本质并对他们作出适当的反应
（7）适当地行动、理智地思考、有效地适应环境的总体能力。
（8）身体和社会环境的适应性
判断、理解、推理、形成概念、适当的反应和适应性等

### 图灵测试

测试的参与者：测试人
被测试人：一个人，一个声称自己有人类智力的机器
测试过程：测试人与被测试人是分开的，测试人只有通过一些装置（如键盘）向被测试人问一些问题，这些问题随便是什么问题都可以
**重要意义**：使实验研究智能行为成为可能

问过一些问题后
测试人能正确地分出谁是人谁是机器——**机器没有通过图灵测试**
测试人没有分出谁是机器谁是人——**机器通过了图灵测试，具有了图灵测试意义下的智能**

### 中文屋子问题

仅仅成功执行算法本身并不意味着对所发生的事情有丝毫理解
被锁在中文屋子里的希尔勒不理解故事中的任何一个词
希尔勒的中文屋子问题
提出了一个什么是理解的问题
也许体现了**人的智能**和**人工智能**的不同

### AI 的研究目标

AI 是研究如何制造出人造的智能机器或智能系统，来模拟人类智能活动的能力，以延伸人们智能的科学

### AI 的研究途径

**心理学（符号主义）**：
人工智能源于数理逻辑。认识的基本元素是符号，智能和知识可用符号表示、擅长抽象思维
人工智能的主流学派，代表有纽厄尔、肖、西蒙和尼尔逊等
启发式程序、专家系统、知识工程
**生理学（联结主义）**：
原理主要为神经网络及神经网络间的连接机制与学习算法
认为认识的基本元素是神经元，认识过程是大量神经元的并行活动，擅长形象思维
M-P 神经细胞模型、BP 神经网络模型、Hopfield 神经网络模型
**生物进化（行为主义）**：
原理为控制论及感知论，认为人工智能源于控制论。代表人物有布鲁克斯
Brooks 研制的智能机器人

### AI 的历史

- 阶段 1：萌芽期（1956 年以前）
- 阶段 2：人工智能基础技术的研究和形成(1956—1970)
- 发展和实用化阶段(1971—1980)
- 知识工程与专家系统(1980 年至今)

## 搜索问题

### 回溯策略

思想：

- 首先将规则给出一个固定的排序
- 在搜索时，对当前状态（搜索开始时，当前状态是初始状态）依次检测每一条规则，在当前状态未使用过的规则中找到第一条可触发规则，应用于当前状态，得到的新状态重新设置为当前状态，并重复以上搜索
- 如果当前状态无规则可用，或者所有规则已经被试探过仍未找到问题的解，则将当前状态的前一个状态（即直接生成该状态的状态）设置为当前状态
  重复以上搜索，直到找到问题的解，或者试探了所有可能后仍找不到问题的解为止

#### 回溯搜索算法

BACKTRACK（DATA）
**DATA**：当前状态
**返回值**：从当前状态到目标状态的路径（以规则表的形式表示）或 FAIL

递归过程 BACKTRACK(DATA)

> 1. IF TERM（DATA），RETURN NIL；TERM 取真即找到目标，则过程返回空表 NIL。
> 2. IF DEADEND（DATA），RETURN FAIL；DEADEND 取真，即该状态不合法，则过程返回 FAIL，必须回溯。
> 3. RULES：＝ APPRULES（DATA）；APPRULES 计算 DATA 的可应用规则集，依某种原则（任意排列或按启发式准则）排列后赋给 RULES。
> 4. LOOP：IF NULL（RULES），RETURN FAIL；NULL 取真，即规则用完未找到目标，过程返回 FAIL，必须回溯。
> 5. R：＝ FIRST（RULES）；取头条可应用规则。
> 6. RULES：＝ TAIL（RULES）；删去头条规则，减少可应用规则表的长度。
> 7. RDATA：＝ GEN（R，DATA）；调用规则 R 作用于当前状态，生成新状态。
> 8. PATH：＝ BACKTRACK（RDATA）；对新状态递归调用本过程。
> 9. IF PATH ＝ FAIL，GO LOOP；当 PATH ＝ FAIL 时，递归调用失败，则转移调用另一规则进行测试。
> 10. RETURN CONS（R，PATH）；过程返回解路径规则表（或局部解路径子表）。

#### 几个特殊点

> 1. NIL：sg 满足结束条件
> 2. FAIL：需要回溯
> 3. **两个回溯点**
>    IF DEADEND（DATA），RETURN FAIL
>    IF NULL（RULES），RETURN FAIL
> 4. 最高层 FAIL：搜索失败
> 5. 第十步：成功找到解 RETURN CONS（R，PATH）
> 6. 第三步：可用规则排序 RULES：＝ APPRULES（DATA）

#### 存在的问题

- 深度问题
- 死循环问题

#### 解决方法

- 对搜索深度加以限制
- 记录从初始状态到当前状态的路径

#### 改进的回溯算法

**BACKTRACK1（DATALIST）**
**DATALIST**：从初始到当前的状态表（逆向）
**返回值**：从当前状态到目标状态的路径
（以规则表的形式表示）或 FAIL

> 1. DATA：＝ FIRST（DATALIST）；设置 DATA 为当前状态。
> 2. IF MEMBER（DATA，TAIL（DATALIST）），RETURN FAIL；TAIL 是取尾操作，表示取表 DATALIST 中除了第一个元素以外的所有元素。如果 DATA 在 TAIL（DATALIST）中存在，则表示有环路出现，过程返回 FAIL，必须回溯。
> 3. IF TERM（DATA），RETURN NIL；TERM 取真即找到目标，则过程返回空表 NIL。
> 4. IF DEADEND（DATA），RETURN FAIL；DEADEND 取真，即该状态不合法，则过程返回 FAIL，必须回溯。
> 5. IF LENGTH（DATALIST）＞ BOUND，RETURN FAIL；LENGTH 计算 DATALIST 的长度，即搜索的深度，当搜索深度大于给定值 BOUND 时，则过程返回 FAIL，必须回溯。
> 6. RULES：＝ APPRULES（DATA）；APPRULES 计算 DATA 的可应用规则集，依某种原则（任意排列或按启发式准则排列）排列后赋给 RULES。
> 7. LOOP：IF NULL（RULES），RETURN FAIL；NULL 取真，即规则用完未找到目标，过程返回 FAIL，必须回溯。
> 8. R：＝ FIRST（RULES）；取头条可应用规则。
> 9. RULES：＝ TAIL（RULES）；删去头条规则，减少可应用规则表的长度。
> 10. RDATA：＝ GEN（R，DATA）；调用规则 R 作用于当前状态，生成新状态。
> 11. RDATALIST：＝ CONS（RDATA，DATALIST）；将新状态加入到表 DATALIST 中。
> 12. PATH：＝ BACKTRACK1（RDATALIST）；递归调用本过程。
> 13. IF PATH ＝ FAIL，GO LO0P；当 PATH ＝ FAIL 时，递归调用失败，则转移调用另一规则进行测试。
> 14. RETURN CONS（R，PATH）；过程返回解路径规则表（或局部解路径子表）。

### 图搜索策略

#### 一般的图搜索算法

- 是图搜索算法的总框架，其他各种算法基于此框架
- s 为初始节点，t 为目标节点
- G：图，产生的连接关系
- OPEN 表：搜索过程中所有生成出来的但还未扩展的节点
- CLOSED 表：记录所有被扩展过的节点
- OPEN 表和 CLOSED 表没有交集，其合集为扩展出的所有节点
- 搜索主要是对这两个表进行处理
  - 判断 OPEN 表是否为空，失败结束
  - 否则取出第一个，判断是否为目标，是成功结束，不是对它进行扩展，修改 OPEN 表和 CLOSED 表，对 OPEN 表排序，继续判断

> 1. G=G0 (G0=s), OPEN:=(s);
> 2. CLOSED:=( );
> 3. LOOP: IF OPEN=( ) THEN EXIT(FAIL);
> 4. n:=FIRST(OPEN), REMOVE(n, OPEN),
>    ADD(n, CLOSED);
> 5. IF GOAL(n) THEN EXIT(SUCCESS);
> 6. EXPAND(n)→{mi}, G:=ADD(mi, G);子节点集合{mi}不包含 n 的父辈节点
> 7. 标记和修改指针：
>    ADD(mj, OPEN), 并标记 mj 到 n 的指针；
>    计算是否要修改 mk、ml 到 n 的指针；
>    计算是否要修改 ml 到其后继节点的指针；
> 8. 对 OPEN 中的节点按某种原则重新排序；
> 9. GO LOOP；

### 无信息图搜索过程

#### 深度优先搜索

> 1. G:=G0(G0=s), OPEN:=(s), CLOSED:=( );
> 2. LOOP: IF OPEN=( ) THEN EXIT (FAIL);
> 3. n:=FIRST(OPEN);
> 4. IF GOAL(n) THEN EXIT (SUCCESS);
> 5. REMOVE(n, OPEN), ADD(n, CLOSED);
> 6. EXPAND(n) →{mi}, G:=ADD(mi, G);
> 7. ADD(mj, OPEN), 并标记 mj 到 n 的指针;把不在 OPEN 表和 CLOSED 表的节点放在 OPEN 表最前面，深度大的节点优先扩展
> 8. GO LOOP;

#### 深度优先搜索的性质

- 问题有解，不能保证找到解，也不能保证找到最优解
- 问题状态空间有限，能保证找到解
- 问题状态空间无限，可能陷入“深渊”→ 加深度限制
- 深度限制不合理时，可能找不到解，可以将算法改为可变深度限制
- 最坏情况时，搜索空间等同于穷举
- 与回溯法的差别：深度优先搜索属于图搜索
- 是一个通用的与问题无关的方法

#### 改进算法

> 1. G:=G0(G0=s), OPEN:=(s), CLOSED:=( );
> 2. LOOP: IF OPEN=( ) THEN EXIT (FAIL);
> 3. n:=FIRST(OPEN);
> 4. IF GOAL(n) THEN EXIT (SUCCESS);
> 5. REMOVE(n, OPEN), ADD(n, CLOSED);
> 6. IF DEPTH(n)≥Dm GO LOOP;
> 7. EXPAND(n) →{mi}, G:=ADD(mi, G);
> 8. ADD(mj, OPEN), 并标记 mj 到 n 的指针;
> 9. GO LOOP;
