# 系统结构复习
* 减少客观题，增加大题。
* 单选10'+填空10'+大题80'
* 全部作业都要会做，不会出作业原题
* 重新做一遍作业
* 剩下的客观题，PPT为主
## Chap1 系统结构基本概念
系统结构与组成实现的关系，什么是透明性，分类的几种方式，系统设计的三原则，定量定性程序局部性，系统程序结构，计算机不同的程序分类
### 1.2 计算机系统结构
#### 1.2.1 系统结构基本概念
* **系统结构**：从程序设计者的角度所看到的系统的属性，即概念性结构和功能特性。
* **计算机系统结构**：指**机器语言程序**的设计者或是**编译程序**设计者所看到的计算机系统的**概念性结构与功能特性**。 
* **透明性**：一种本来存在，有差异的事物和属性，从某种角度上看又好像不存在的现象，被称为是“透明性”。Exp：高级语言程序员看不到不同机器的差异性。
#### 1.2.2 计算机系统结构、组成与实现
* 计算机**系统结构**：**机器语言级**的程序员所了解的**计算机的属性**，即**外特性**。
  * 数据表示、寄存器定义、指令系统、中断系统、存储系统、I/O、及其工作状态、信息保护。
* 计算机**组成**：计算机**系统结构**的**逻辑实现**。
  * 数据通路宽度、专用部件的设置、各功能部件、控制机构组成方法、缓冲技术……
* 计算机**实现**：计算机**组成**的**物理实现**。
  * 逻辑设计的物理实现
* 计算机系统的结构、组成、实现**相互依赖相互影响**。
* 指令系统--结构，乘法指令--组成，主存系统--实现。
<div STYLE="page-break-after: always;"></div>

#### 1.2.3 系统机构分类
1. **弗林分类法(FLYNN)**：
  * **指令流**(指令传送序列)
  * **数据流**(数据传送、加工序列)
  * **多倍性**(系统瓶颈部件上同一阶段执行的指令或数据最大可能个数)。
* 单指令流，单数据流--**SISD**(传统顺序处理机)、
* 单指令流，多数据流--**SIMD**(阵列机，并行处理机)
* 多指令流，单数据流--**MISD**(RISC机，向量机)
* 多指令流，多数据流--**MIMD**(多处理机系统)
2. 冯氏分类法
   * 最大并行度：计算机单位时间内能处理的最大二进制位数。
   * 一个字中同时处理二进制的位数&一个位片或功能部件中能同时处理的字数
3. 汉德勒法
   * 硬件设备结构的并行级和流水线的程度分类。
   * 程序控制部件个数，算数逻辑运算部件，基本逻辑线路套数。
### 1.3 计算机系统设计
#### 1.3.1 设计原则
##### 1. 加速使用频率高的部件--提高整个计算机性能
##### 2. Amdahl定律
* **Amdahl定律**：衡量系统性能提升的指标--**加速比**
* **加速比** = 采用改进措施**后的性能** / 采用改进措施**前的性能**
* **加速比**($S_p$) = 采用改进措施**前的耗时** ($T_e$)/ 采用改进措施**后的耗时**($T_0$)
* $f_e$：可改进部分在原系统计算时间中占比，<1;
* $r_e$：性能提高倍数，可改进部分的改进前耗时 / 改进后耗时，>1。
* $f_e/r_e$：改进后改进部分时间 / 改进前整个任务时间
$$
S_p = T_e/T_0
\\T_0 = T_e(1-f_e + f_e/r_e)
\\S_p = \frac{1}{(1-f_e + f_e/r_e)}
\\ \lim_{r_e \to \inf}S_p = \frac{1}{1-f_e}
$$
* 为获取较高的加速比，功能性增强的部分需要**占有较大的比例**($f_e$尽量大)。
##### 3. 程序访问局部性原理
* 局部性:程序往往重复使用**刚使用过的数据和指令**。
    * 时间局部性：近期被访问的代码，不就将再次被访问
    * 空间局部性：地指上相邻的代码可能被连续访问。
#### 1.3.2 设计方法
* 软硬件**功能的分配**，考虑：功能要求、性能要求、成本要求。
* **设计方法**：自下而上、自上而下(专用机)、**由中间开始**(最好)
#### 1.3.3 设计步骤
* 需求分析、需求说明、概念性设计、具体设计、优化和评价
* 获得尽可能高的性能价格比。
### 1.4 计算机性能评价
* 计算机性能以及系统评价的目标都指：**系统速度的性能**(通常用**响应时间**衡量)
* **响应时间**：任务送入计算机--得到结果。受磁盘速度，内存速度，CPU运算速度等影响。
#### 1.4.1 CPU性能
* $T_{CPU}$：CPU执行用户程序所用时间
* $I_N$：INS number
* CPI：每条指令所需**平均周期数**= 总周期数 / 总指令数
* $T_C$：时钟周期
$$
T_{CPU} = I_N\times CPI\times T_C
$$
#### 1.4.2 MIPS & MFLOPS
* MIPS：每秒执行指令条数（百万）
$$
MIPS = \frac{指令总数}{执行时间 \times 10^6} = \frac{时钟频率}{CPI\times 10^6} 
$$
* MFLOPS：每秒浮点操作次数（百万）
$$
MFLOPS = \frac{浮点操作次数}{执行时间\times 10^6}
$$
<div STYLE="page-break-after: always;"></div>

### 1.5 计算机系统层次结构
1. 运算器中心，除了完成运算以外，机器内部的数据传送都经过运算器，控制器集中控制。
2. 存储器是字长固定的、顺序线性编址的一维结构。 
3. 程序存储，指令和数据都存放在存储器中。 
4. 指令在存储器中按其执行顺序存放，由一个顺序控制器指定即将被执行的指令地址。
5. 指令由操作码和地址码组成。 
6. 数据以二进制表示。  
* 改进：
1. 数据类型增加
2. 指令种类、寻址方式增加
3. 以存储器为中心
4. 处理器采用新技术——堆栈、流水等


## Chap2 指令系统
 大题：霍夫曼编码相关，概念比较零碎，RISC&CISC
### 2.1 引言
* **指令系统**：又称**指令集**，计算机体系结构设计的核心，是**计算机软、硬件接口**，是机器语言汇编语言编写程序的用户看到的计算机基本属性。
* 指令系统设计确定指令格式、数据类型、操作功能及操作数访问方式。
#### 2.1.1 指令系统设计要求
* **软件兼容性**：继承软件资产，保证**向后兼容**(旧的)和**向上兼容**(新的)
* 可扩性：保留一定余量的操作码空间，为以后扩展准备。
* 指令码高密度性：对频率高的指令串进行优化，设计新指令代替，提高指令码密度。
#### 2.1.2 CISC & RISC
1. **CISC**复杂指令集计算机
   * 执行通过**微程序控制技术**
   * 控制器复杂，占用大量CPU芯片面积，有些复杂指令很少用
   * 执行效率不高
   * 指令系统与软件间语义差别大，设计繁重。
* **缺点**：指令系统庞大、硬件复杂、执行速度低、编译程序复杂，长、部分指令使用效率低。
2. **RISC**精简指令系统计算机
   * **减少**指令**总数**和**简化**指令的**功能**来**降低硬件设计的复杂程度**，提高指令执行速度，使指令简单，有效可行。
### 2.2 数据类型和数据表示
#### 2.2.1 数据类型
* 三类：用户定义的数据、系统数据、指令数据(指令系统能处理的数据)
* **数据类型**：指一组数据值的集合，以及可作用于这个集合上的操作集
  * 分类：基本数据类型、结构数据类型、抽象数据类型和访问指针。
#### 2.2.2 基本数据表示
* **数据表示**：在计算机中能**由硬件直接辨认**，**指令系统直接调用**的数据类型。
* **数据结构**：结构化数据的组织方式，通过软件映像变换成机器中所具有的各种数据表示实现。
#### 2.2.3 自定义数据表示
* **目的**：缩短机器语言同高级语言对数据属性说明间的语义差异
* **自定义数据表示**：由数据本身来表明数据类型，使计算机内的数据具有自定义能力。
* **分类**：带标志符的数据表示、数据描述符。
  * **带符号的数据表示**：描述**简单**数据，和数据值**相连**，储存在**同一存储单元**内
    * **优点**：简化了指令系统、容易检出程序编制中的错误、简化了编译程序、支持数据库系统、简化了程序设计、便于软件测试，支持应用开发
    * **缺点**：数据字长增加、降低了指令的微观执行速度、与其他计算机的兼容性差，硬件复杂。
  * **数据描述符**：描述**复杂**和多维数据，描述了所要访问数据的特性，和数据字**分开存储**，**增加一级以上寻址**。是程序的一部分不是数据的一部分。数据字本身是带标志符数据表示。
### 2.3 指令系统设计原理
#### 2.3.1 指令系统中指令编码方法
1. **正交**：每个分段相互独立。优点：适用于流水机，微程序控制数量减少。
2. **整体**：各个分段译码时相互有关，操作码与操作数和地址分界线不清晰。
   * 优点：可以缩短使用频度高的指令长度，频率低的指令长，节省储存空间；
   * 缺点：用微程序控制时微程序数量多，需要有较大的微程序存储器。
3. **混合**：结合以上两点。
#### 2.3.2 指令系统及结构的分类
* 基本思想：计算机系统的一些基本操作应由硬件实现还是软件实现；某些复杂操作是由一条还是一系列指令实现。
* 分类：
  * 每条指令中显示指明操作数个数
  * 操作数的类型及长度的确定
  * 数据类型和数据表示
  * 操作数的位置--堆栈、寄存器、存储器。
#### 2.3.3 寻址技术
寻址技术指指令**按什么方式寻找**所需的操作数或信息。影响主存规模、速度及存取方法。寻址方法**对程序员透明**。
* 访问方式：按地址访问(串行)、按内容访问(并行，小容量)。
* 编址方式：
  1. **统一编址**：各部件统一编成一个从0开始的一维线性地址空间，对不同部件的访问反映在对这个空间中不同地址的访问。**优**：有利简化指令系统；**缺**：使地址形成更复杂。
  2. **局部编址**：每个部件各自从0开始单独编码，形成多个一维线性地址空间。**优**：指令字长较短，地质形成简单，主存编址范围大；**缺**：指令中需要有对每类存储信息加以区分的标志或使用约定。
  3. **隐含编址**：不进行地址计算，隐含在操作码中。多数**事先约定好**编址方式进行隐式寻址。**缺**:导致指令系统设计缺乏规范。
* **程序定位方式**：指令和数据中的逻辑地址转变成主存的物理地址的过程。
  1. 直接定位：直接用物理地址变成(一般不用)
  2. 静态地址：专门的装入程序完成，装入后不可变。**优**：实现简单，不用增加硬件地址。**缺**：不灵活，内存利用率不高，无法实现共享。
  3. 动态定位：主存起始地址装入对应寄存器，指令地址不需全部修改。**优**：执行时由硬件形成物理地址，内存利用率高，多用户可以实现共享，支持实现虚拟存储器。**缺**：需要硬件支持，算法复杂。
#### 2.3.4 指令格式的优化
* 指令的优化通过**操作码**优化和**地址码**优化进行。
* **操作码的优化：哈夫曼压缩**
* **操作码的信息源熵**：信息源所包含的平均最短信息量。
* $P_i$:第i个信息源的频度。
$$
H = - \Sigma P_i \log_2P_i
\\ 信息冗余量 = \frac{1-H}{操作码平均长度}
$$
* 霍夫曼编码定长扩展：2/4/6，每次留最后一组用于下一长度的扩展
* 15/15/15编码法：几类数量一样。
  * 0000 ~ 1110
  * 1111 0000 ~ 1111 1110
  * 1111 1111 0000 ~ 1111 1111 1110
* 8/64/512编码法：高频少，低频多。
  * 0000 ~ 0111 :8
  * 1000 0000 ~ 1111 0111 :8 * 8
  * 1000 1000 0000 ~ 1111 1111 0111 :8 * 8 * 8
* 地址码的优化：
    1. 操作数地址码长度可在很宽的范围内变化，可与变长操作码合成定长指令；
    2. 改变指令字中的**地址数**和**地址码**的**长度**，使单、双、三地址都可以在指令中使用；
    3. 若操作数存在寄存器内，或经寄存器间接寻址，则指令地址码的宽度能指明寄存器号即可；
    4. 设法利用空白处存放立即操作数或常数。
### 2.4 RISC计算机
#### 2.4.1 RISC计算机的设计原理
1. **起源**：
   1. **二八定律**
   2. 系统设计中硬件和软件间的折中。
   3. VLSI工艺技术发展。
2. **设计原则**：
   1. 选择**使用频率高**的指令，增加少量支持操作系统和高级语言实现及其他功能的有用指令。**寻址方式**取最基本的一两种。使指令**条数少**，**格式简单**，**长度相同**。
   2. 提高处理速度，使用**流水技术**（使每条指令可以在一个周期内完成）。大部分指令操作在**寄存器**间进行，采用硬件逻辑控制实现操作，只有少量使用微程序实现。
   3. **简化编译**工作，一个周期完成一条指令操作，编译器易于调整指令流。
3. **RISC的CPI**：

|类型|$I_N$|CPI|$T_c(ns)$|
|---|---|---|---|
|CISC|1|2~15|33~5|
|RISC|1.3~1.4|1.1~1.4|10~2|
<div STYLE="page-break-after: always;"></div>

   * RISC结构的$T_{cpu}$值远小于CISC结构
     * RISC通过减少CPI值简化结构来减少$T_{cpu}$
     * CISC通过减少$I_N$来减少$T_{cpu}$
#### 2.4.2 RISC主要技术
1. **流水小结构和调度指令**：RISC主要特点之一是充分提高流水线效率
2. **寄存器窗口重叠**：RISC芯片上有大量通用寄存器
   * **寄存器窗口技术**：寄存器分成很多小组，每个过程分配一个小组。发生过程调用时，把CPU转换到不同的小组使用，无需保存和恢复的操作。此小组称为寄存器窗口。相邻的窗口间有部分重叠，便于调用参数传送。
   * **RISC有八个寄存器窗口**：窗口转换通过改变硬件指针实现。超过八个过程调用时，将一个窗口内容传送到内存。
 * **优点**：显著减少过程调用和返回执行时间、执行的指令条数和访问存储器的次数。
3. **优化编译技术**
   1. 如何最佳分配寄存器堆中的寄存器，使数据有效地减少对存储器的访问
   2. 在保持原来语义的基础上对指令序列重新排序和调度，进行并行性的开发。
* **优点**：
  * RISC指令系统条数少，简单对称，减轻编译程序负担；
  * RISC寻址方式简单，只有LOAD和STORE指令访问存储器。其它操作均在通用寄存器中进行，简化寻址方式和访存操作；
  * 大多数指令在一个周期内完成，为优化编译器进行调整指令流序列，减少相关，提高并行度带来了方便。


## Chap3 储存系统
* CACHE大题--15'
* 目的：存放计算机系统中所需处理的程序与数据
* 存储系统：两个或两个以上的速度、容量、价格不同的存储器采用硬件，软件或软硬结合的方法联接成一个系统。
### 3.1 概述
* 三个基本参数：**容量S**、**速度T**、**价格C**
* Reg-Cache-Ram-Rom(HDD)-移动硬盘。层级越来越高，速度越来越满，容量越来越大。
* **特性**：
  * 局部性：局部性原理；
  * 包含性：容量大的存储器中，一定**能找到上层存储信息的副本**。
  * 一致性：副本修改，保持**同一信息的一致性**。
### 3.2 并行存储器
* **频带宽度**：单位时间内所能访问的**数据量**。
* 提高方法：
    1. 多存储器并行，用并行访问和交叉访问的方法
    2. 设置各种缓冲存储器
    3. 采用Cache存储系统。
#### 3.2.1 多体并行访问存储器
* 地址：a(体号，用于选择)b(体内地址)
* 每个存储器读出b对应的内容，通过a选择送出哪个值到数据总线上。
* **优点**：简单，容易。**缺点**：访问冲突大
  * 冲突：条件转移、需要的多个操作数不一定在同一个存储字中、需要凑齐n个数才能一起写入存储器、读写发生在同一存储字内时，无法在一个存储周期内完成。
#### 3.2.2 多体并行交叉访问存储器
* 分为M个存储体的主存储器
* 同时访问：同时启动，完全并行工作
* 交叉访问：多个访问源，同时向多个体重的任何一个发出访问请求
* 分时访问：每个体分时启动，启动时间相互错开。
1. 高位交叉访问：a(选择体)+b(体内)
   * 每个体：0~n
   * 优：扩容方便，适用于多任务或多用户状态。不同任务存放在不同体内。
   * 缺：不符合局部性原理(临近指令在同一体内)**并行访问冲突**。
2. 高位交叉访问：a(体内)+b(选择体)
   * 每个体:0, m, 2m, 3m
### 3.3 高速缓冲存储器CACHE
#### 3.3.1 CACHE功能，结构与原理
* CACHE：位于主存与CPU间，使用SRAM。容量小，速度快，接近CPU。
* **功能**：存放近期需要的指令与数据
* **目的**：提高CPU对存储器的访问速度。
#### 3.3.2 地址影响与转换
* 三种映像：全相联、直接相联、组相联
* 数据由主存调入缓存时**建立映像表**；访问数据时，按映像表进行**地址转换**。
1. **全相联**：
   * **规则**：
     * 主存与缓存分成**相同大小的数据块**
     * 主存的某一数据**可以装入任意一块缓存**中
   * **地址转换**：
     * 从映像表中用**主存块号查Cache块号**
     * **映像表**：主存块号B，Cache块号b，有效位
   * **优点**：命中率高，Cache利用率高
   * **缺点**：效率复杂，成本高，速度低(要与映像表所有项对比)。
2. **直接相联**
   * **规则**：
     * 相同块大小
     * 主存容量时Cache容量**整数倍**。主存按Cache大小分区。
     * 主存中某区的一块存入Cache时**只能存入相同块号**的位置。
   * **地址转换**：
     * 主存地址：区号，块号，块内地址
     * Cache地址：块号，块内地址
     * 映像表：区号，有效位
     * 根据主存块号在映像表中查找对应块号的Cache存储的是哪个区的数据。
   * **优点**：简单
   * **缺点**：命中率低。
3. **组相联**
   * **规则**：
     * 相同块大小
     * 分成相同大小的组
     * 主存是Cache的整数倍。按Cache大小分成区。每区的组数与缓存组数相同。
     * **组间直接相联，组内全相联。** 任意一个区的x组可以存入Cache的x组。x组内任意存放。
   * 组内块数=Cache块数--**全连接**；组内块数=1--**直接相联**。
   * **地址转换**：
     * 主存地址：区号，租号，组内块号，块内地址
     * Cache地址:租号，组内块号，块内地址
     * 映像表：(区号，组内块号)，Cache组内块号，有效位
     * 取主存块号，遍历映像表中对应此组号的几条记录。若区号和组内块号和记录的相等，取Cache组内块号，形成Cache地址。
   * **优点**：速度快，命中率高。
<div STYLE="page-break-after: always;"></div>

#### 3.3.3 替换策略
1. **RAND**
   * **优点**：简单，易于实现；**缺点**：没有考虑**局部性原理**，**命中率低**。
2. **FIFO**
   * **优点**：考虑了程序运行的历史状况，易于实现；**缺点**：没有考虑局部性原理，**命中率好于RAND**，但还不够。
3. 最近最少使用**LRU**
   * **缺点**：实现困难。
4. 最旧没有使用**LFU**：思想与LRU相同，实现不同
   * **优点**：实现容易；**缺点**：。
* **命中率与地址流、块大小和块数量有关**。
* LRU，LFU实现：
  * **计数法**：新调入和命中的块技术值清0，未被命中则+1，每次替换最大的。
  * **链表法**：新块位于表头，命中的块置于表头，每次淘汰链表尾
#### 3.3.4 Cache写操作
1. **全写法(WT)**：写Cache的同时也写主存。
  * **优点**：同时更新，一致性较好，可靠性高，操作简单。Cache出错时可以通过主存矫正；
  * **缺点**：写入速度 = 主存速度，慢。
    * **改进**：给主存一个小容量缓冲储存器。
2. **回写法(WB)**：只写Cache，替换时把修改过的块写回主存。
   * **优点**：Cache速度更快，命中率更高。与主存的通信量大大降低；
   * **缺点**：会存在Cache与主存内容不一致的情况，**可靠性差**，**控制复杂**。
     * **改进**：块写回主存时CPU无法访问Cache与主存。在Cache和主存间设置一个**高速缓存**，**存放写回数据和地址**。
3. 写不命中
   * 不按写分配(直接写入主存，不调入Cache)，按写分配(写入主存并调入Cache)。
#### 3.3.5 Cache性能分析
1. **透明性分析**：
   * Cache的地址变换和块替换算法由硬件实现
   * Cache-主存层次对应用和系统程序员透明
   * Cache对处理机和主存间的信息交往是透明的
2. **Cache命中率**：
   * **容量**：**容量越大命中率越高**。从容量很小开始增大时效果明显。当容量达到一定大小后，命中率改善不明显。
   * **块大小**：块大小与命中率的关系是一条**开口向下的抛物线**。块大小大过顶点后进入块的数据**已不符合局部性原理**。块越大，块数越少，命中率越低。
   * **映像方式**：全连接命中率高，难以实现；直接相联命中率低；组相联的**分组数目对命中率影响明显**。**分组数增加，命中率下降**；组数少时不明显，组数大到一定程度后影响很大。
3. **Cache系统加速比**
* $T$：等效访问周期
* $T_c$：Cache访问周期
* $T_m$：主存访问周期
* $H_c$：Cache命中率
* $e$：存储系统的访问效率--高一级存储器的访问速度与系统等效的访问速度之比
$$
T = H_cT_c+(1-H_c)T_m
\\S_p = \frac{T_m}{T}=\frac{1}{H_c\frac{T_c}{T_m}+(1-H_c)}
\\ \lim_{H_c \to 1}S_p = \frac{T_m}{T_c}
\\e = \frac{T_c}{T}=\frac{1}{H_c+(1-H_c)\frac{T_m}{T_c}}
$$
* **$T$ 越接近 $T_c$访问效率越高**
* **$e$不变时，$T_m/T_c$越大，$H_c$越大**
#### 3.3.6 Cache实例
1. 分体--数据(R/W)与指令(R)Cache分体。
2. 分级--L1&L2
### 3.4 虚拟存储器
* 主存+辅存。软硬件支持。主存的速度+辅存的容量。
* 虚实地址转换
* 程序局部性原理
### 3.5 存储保护
* **原因**
  1. 防止一个程序出错破坏主存中其他用户的程序或系统软件
  2. 防止用户程序不合法的访问不是分配给它的主存区域。
1. **加界保护**
   * 用于**段式管理**中，设置**界限寄存器**，地址越界时报越界错误。
2. **键保护**
   * 用于**页式管理**中，每个程序的所有页有一个相同的键号。每次访问时对比键号，一致时可以访问。
3. **环保护**
   * 把系统程序和用户程序按功能分级。一个程序可以访问比他低级的，不可以访问比他高级的。
* 访问方式保护：读，写，执行。

## Chap4 流水线技术
* 三个作业大题都考
* 先写后读相关：
* 加快指令执行速度：1.更快的原件，指令更少的算法；2.提高指令间的并行性。
* 提高处理速度和系统使用效率：1.资源重复；2.**时间重叠**(流水)；3.**资源共享**(流水)
### 4.1 概述
CPU工作方式：**顺序、重叠、流水**
* 顺序执行。优点：**控制简单**。缺点：速度**慢**，部件**利用率低**。
### 4.2 流水工作方式
#### 4.2.1 概念和特点
* **概念**：讲一个重复的时序过程分成若干子过程，每个子过程都可有效的在其专用功能段上**和其他子过程同时执行**。
* **基本构成**：锁存器，时钟，功能站。
* **建立时间**：第一条指令从流入到流出的时间。**正常流动**：各功能段不断满载的阶段。**排空时间**：最后一条指令**流入后**到流出的时间。
#### 4.2.2 分类分级
* **分级**：
  * **操作部件级**(将复杂的算术逻辑运算作为一站)
  * **指令级**(一条指令解释过程分成多个子过程)
  * **处理机级或宏流水线级**(两个以上处理机串行对同一数据流处理)
* **分类**：
  * **功能角度**：单功能、多功能
  * **工作方式**：静态(同一时间只能进行一种运算，**切功能先排空**)、动态(同一时间允许多种不同运算)
  * **连接方式**：线性流水(不存在反馈回路)，非线性流水(存在反馈回路)
#### 4.2.4 性能分析
* 技术指标：**吞吐率**、**加速比**、**效率**
1. **吞吐率**：**单位时间内能处理的指令条数**或能输出的数据量。
   * **最大吞吐率**：**达到稳定状态**后
   * **解决瓶颈**：瓶颈段**细分**、**重复设置并行**瓶颈段
$$
TP_{max}=1/\Delta t(理想)
\\ TP_{max}=1/max\{\Delta t_1,\Delta t_2,\Delta t_3,\Delta t_4\}(瓶颈任务)
$$
* 
   * $m$：指令流水线段数；$n$：指令条数；
   * $\Delta t_0$：各段经过的时间。**$\Delta t_j$：瓶颈端耗时**
   * 完成n条指令的解释共需$T=m\times\Delta t_0+(n-1)\times\Delta t_0$
   * **实际吞吐率**=任务数n / 从开始到最后一个任务流出的时间
$$
TP=\frac{n}{m\times\Delta t_0+(n-1)\times\Delta t_0}=\frac{1}{\Delta t_0(1+\frac{m-1}{n})}=\frac{TP_{max}}{1+\frac{m-1}{n}}(各段时间相同)
\\TP=\frac{n}{\Sigma_{i=1}^m\Delta t_i+(n-1)\times\Delta t_j}(各段时间不同)
$$
2. **效率**：设备利用率，运行时间中流水线设备有多少时间是真正用于工作的。**一般用时空图占用空间/总空间**
$$
\eta=\frac{n(\Sigma_{i=1}^m\alpha_i\times\Delta t_i)}{\Sigma_{i=1}^m\alpha_i[\Sigma_{i=1}^m\Delta t_i+(n-1)\Delta t_j]}
$$
   * **各$\Delta t$相等时**，$\eta = TP\times\Delta t$
3. **加速比**：m段**流水线的速度** / 等效的**非流水线的速度**；或**非流水的时间** / **流水的时间**。
$$
S_p=\frac{T_{非流水}}{T_{流水}}=\frac{m}{1+\frac{m-1}{n}}(各时间段相等)
\\S_p=\frac{n\Sigma_{i=1}^m\Delta t_i}{\Sigma_{i=1}^m\Delta t_i+(n-1)\times\Delta t_j}(各时间段不等)
$$
* **当n>>m时**，$TP才接近TP_{max}，\eta,S_p越高$
* **实例分析**
1. 实测法
2. 分析法：套公式计算
3. 时空图法：画图
* 只有**指令多**，**实际吞吐率和效率才会提高**。
* **消除瓶颈后**，**指令少**时，**效率可能下降**（但吞**吐量一定更高**)。
#### 4.2.5 流水的控制和设计
* 时序和缓冲：分段$\Delta t$**尽量小，尽量一致**，则TP越大
* **相关处理**
  * **定义**：相近的指令可能出现某种关联而使其不能同时执行。
  1. **资源相关**：**多条指令**在**同一机器周期**内征用**同一功能部件**。
     * Exp:IF/MEM同时访存。
     * **解决方法**：i+3指令停顿一拍进入流水线，解决访存相关；数据与指令分开存储。
  2. **数据相关**：一条指令需要用到之前指令的执行结果。前一条指令在流水线中重叠执行，还未产生结果。
     * RAW(先写后读)、WAR(先读后写)、WAW(先写后写)
     * **解决方法**：1.时间后推；2.旁路技术，定向技术(将一个计算结果直接传送到所有需要它的功能单元的输入端)
  3. **控制相关**：由无条件转移和条件转移引起。
     * **解决方法**：加快和提前形成条件码，静态转移预测(猜测法，预取转移目标，加快短循环程序处理)。
* 中断处理：
* **关键**：处理断点现场以及恢复问题。
* **不精确断点法**：不再允许还未进入流水线的后续指令再进入，已流入的指令执行完；现场是最后一条指令。
* **精确断点法**：不论第i条指令是在流水线中哪一段发的中断申请，给中断处理程序的现场全都是对应第i条的，在第i条之后进入流水线的指令的原有现场都能恢复。
### 4.3 先进的流水技术
#### 4.3.1 动态调度
* **静态调度**：借助软件对指令执行顺序进行调度，减少由于流水线中存在相关冲突而引起流水线的停顿时间。
* **动态调度**：通过硬件重新安排指令的执行顺序以减少流水的停顿。
* 优点:
  1. 能处理某些在编译时无法知道的相关情况
  2. 能简化编译程序设计
  3. 使代码有可移植性
* 缺点：相应的硬件较为复杂。
#### 4.3.2 非线性流水线的冲突及调度
* 由于反馈回路的存在，一个任务可能在流水中多次通过同一流水段。因此**不能每拍均向流水线送入新任务**，否则会出现啊**功能段的使用冲突**。
* **解决方法**：**间隔恰当拍数**再向流水线送下一任务
* **预约表**
* **禁止表**：F={1,6,8,5}。两个任务的间隔**不能是**禁止表中的值。
* **冲突向量**:最大进制间隔数n。**最右侧对应1**。
  * Exp:F={1,3,6}。n=6 C = (100101)。
  * 下一拍的冲突向量：原始向量**右移n拍(等待拍数)**。与原始冲突向量**按位或**。
* **状态转移图**：每一个回路都是一个调度策略。
  * Exp：调度策略-非等间隔(2,2,7)，平均间隔拍数(2+2+7)/3=3.67
  * -等间隔(7)，平均间隔拍数7
  * 调度策略-(3,5)，6个任务：耗时：3+5+3+5+3+7=26。最后一个为流水长度，需要走完全部流水。吞吐率TP=6/26=0.23
### 4.4 流水中指令级并行性的进一步开发
* **粗粒度**并行性：多个**处理机并行**合作完成一个程序。
* **细粒度**并行性：一个进程中进行**操作一级或指令一级的并行**处理
* **单发射结构的RISC**：RISC机的体系结构关键技术是精心的流水线设计和优化的编译技术，使得**每个周期能够发射一条指令**。$CPI\geq 1$(由于有相关等影响)。
1. **超级标量**计算机：每个时钟周期内能**同时发射多条指令**
   1. 硬件负责指令调度
   2. 硬件是不能重新安排指令的前后次序，在编译里优化。
   3. 适合于求解象稀疏矩阵这样的复杂标量问题
   * 同时发射x条指令
   * **花费时间：m+n/x-1**
   * **超标量流水调度**--Cyclone计算机
     * 按序发射按序完成--Pentium
     * 按序发射无序完成--Pentium II/III
     * 无发射无序完成--
2. **超长指令字**计算机(VLIW)：编译时找出指令间潜在的并行性，把多个能并行执行的操作**组合**在一起，成为一条具有多个操作段的**超长指令字**。
   * **时长同超级标量**。
   * 采用多个独立的功能部件，以一条长指令（利用其中每个操作段）控制实现多个操作的并行执行（相当于同时执行多条指令），减少存储器访问。
   * 单一的控制流。只有一个控制器，每个周期启动一条指令。
   * 超长指令字被分成多个控制字段，每个字段直接独立地控制每个功能部件。
   * 含有大量的数据通路和功能部件，由于编译器在编译时间已考虑可能出现的数据相关和资源相关，故控制硬件较简单
   * 在编译阶段完成超长指令中多个可并行执行操作的调度
<div STYLE="page-break-after: always;"></div>

3. **超级流水线**计算机：每个时钟周期能**分时发射多条**指令。
   * 把一个时钟周期分为多个子流水级。每个子流水级中只取一条指令。
   * 每个周期发射x条。
   * **花费时间：m+(n-1)/x**
   * 通过**提高流水线运行速度**来增强机器性能。为提高运行速度，必须**要加深流水深度**，既**增加流水段数**，以**减少每一段的延迟时间**，这样就可加快流水线的运行频率。
4. **超标量超流水**计算机：在一个时钟周期内要**发射指令n次**，**每次发射指令m条**
### 4.5 向量的流水处理
#### 4.5.1 向量处理方法
1. 水平处理法 $d_i=a_i\times (b_i+c_i)$(来回切换+*)
2. 垂直处理法(适合流水)
   * $B_i+C_i\rightarrow E_i(i=1\cdots n)$
   * $A_i\times E_i\rightarrow D_i(i=1\cdots n)$
3. 分组纵横处理法
   * **分k组, 每组长m，组内垂直处理，组间水平处理。**
   * **n=k*m+r**(r为第k+1组剩余分量)
   * $B_i+C_i\rightarrow E_i(i=1\cdots m)$
   * $A_i\times E_i\rightarrow D_i(i=1\cdots m)$
   * $\downarrow$
   * $B_i+C_i\rightarrow E_i(i=m+1\cdots 2m)$
   * $A_i\times E_i\rightarrow D_i(i=m+1\cdots 2m)$

#### 4.5.2 向量处理机构
* 由向量数据表示和流水线技术相结合构成的向量流水处理机。
1. **存储器**：多存储模块结构，**多体交叉访问**
2. **寄存器**：运算部件中**设置多个向量寄存器**，进行向量处理时，**先将向量数据传送至向量寄存器中**，流水线运算部件由向量寄存器提供数据、处理后的结果也送至向量寄存器中。
#### 4.5.3 增强向量处理性能方法
1. **向量指令类型**：
   * **操作数**与**运算结果都是向量**，**都存放在向量寄存器$V_i$中**。
   * 操作数**一个**来自**向量**寄存器$V_i$**一个**来自**标量**寄存器$S_i$，**结果**存放在**向量**寄存器$V_j$中。
   * **存取指令**，由主存取数经过固定延迟时间传送到向量寄存器$V_i$中。
2. **向量的并行处理**
   * **特点**：只要**无**$V_i$**冲突**和**功能部件冲突**，$V_i$之间及各个功能部件之间**可并行工作**。
   * $V_i$**冲突**：**并行**工作的各**向量指令**的**源向量或结果向量**，使用了相同的$V_i$。
   * **功能部件冲突**：同一个功能部件被**多条**要求**并行**工作的向量指令所**使用**。
3. **链接技术**
   * 利用向量指令间的RAW特性，将$V_i$**同时作为源和结果寄存器**，**将多条向量指令链接**来加快执行速度、提高向量操作的并行性和功能部件流水效能。
   * **只要不发生功能部件冲突和操作数寄存器$V_i$冲突**，都可以通过全链接机构使数据相关指令功能并行处理。
   * 适用于第1条指令的结果是第2条指令的操作数时。从一个流水线部件得到的结果直接送入下一个功能流水线部件的向量寄存器$V_i$中，形成两条指令的链接。

## Chap5 并行处理机和多处理机
### 5.1 概念
* 并行技术包括：并行**结构**、并行**软件**、并行**算法**
* 并行性概念：在信息处理过程中存在某些能够同时进行运算或操作的部分。
  * 同时性：两个或多个事件在**同一时刻发生在多个资源中**
  * 并发性：两个或多个事件在**同一时间间隔内发生在多个资源内**
### 5.2 并行处理技术发展
* 三条路径：
  1. **时间重叠**：引入**时间**因素。多个处理过程在**时间上相互错开**，**轮流重叠使用同一套硬件**设备的各个部分(**指令流水线**)。
  2. **资源重复**：引入**空间**因素。**重复设置硬件资源**来提高系统可靠性或其他性能。(例：通过多台完全相同的计算机完成同样的任务提高可靠性)
  3. **资源共享**：利用软件方法让多个用户**按一定时间顺序轮流使用同一套资源**。(例：**多道程序分时系统**)
### 5.3. 阵列处理机原理
#### 5.3.1 基本构成
* **基本思路**：**重复设置大量相同的处理单元PE**，按一定方式互连，在统一的控制部件(CU)控制下，对各自分配来的不同数据并行地完成同一条指令所规定的的操作。**依靠操作一级的并行**处理来提高系统速度。
* **单指令流多数据流**，指令基本上是**串行执行**，最多加上使用指令重叠或流水线的工作方式。
  * 指令重叠：将指令分两类
    1. **自己执行**：只适合串行处理的控制和标量类指令；
    2. **处理单元**：适合并行处理的向量类指令。
  * 是标量控制类指令和向量类指令重叠执行。
#### 5.3.2 分类
1. 分布储存的阵列处理机
   * 各个处理单元有设置只能被他访问的处理单元(**PEM**)
   * 控制部件(CU)内有一个存放程序的主存储器(**CUM**)
   * 整个系统在CU同一控制下运行系统程序和用户程序。
   * 把用户程序指令发送给各PE，控制PE并行执行。
   * PE之间的通信通过ICN实现，ICN受CU控制。
   * **特点**：处理器阵列通过CU连接到一台**通用计算机SC上管理系统**。

2. 集中共享存储的阵列处理机
   * 没有PEM，存储模块($MM_0$~$MM_{k-1}$)以集中的形式**通过ICN为所有PE共享**，ICN被CU控制。
   * ICN令各PE可高速领活的连接到不同MM上。
#### 5.3.3 阵列处理机的特点
* **共有特点**：通过各种途径**转换为对数组或向量的处理**。利用多个PE单元同时运算，易于获得很高的处理速度。
* **并行**处理机的特点：
  1. **利用资源重复**(非时间重叠)
  2. 利用**同时性**(非并发性)。每个PE在同一时刻同等担负各种运算功能。
  3. **靠增多处理单元格式提速**。比依靠缩短时钟的向量流水机提速潜力更大。
  4. 使用ICN确定多处理单元间的连接模式。
  5. 并行处理机研究必须**与并行算法研究密切结合**。
#### 5.3.4 互联网络
* **概念**：一种**开关原件**，按一定**拓扑结构**和**控制方式**构成，用来实现计算机系统内部的**多功能部件**(SIMD机器)或**多个处理机**之间的相互连接。
1. **互联函数**：互联网络出端号和入端号一一对应关系。
   * **输出输出表示法，循环表示法，函数表示法**
   * 循环表示法：f(x)=(x0,x1,x2,x3,……,xk-1)$X_{j+1}$是前一个元素$X_j$的输出。
   * 函数表示法，编号用二进制表示。$E(b_2b_1b_0)=b_2b_1\overline{b_0}$
   1. **恒等置换**：**相同编号**输入输入一一对应。
   2. **交换置换**：二进制地址中第0位值不同的输入输出端之间连接
      * $E(b_2b_1b_0)=b_2b_1\overline{b_0}$
   3. **方体置换**：二进制地址中第k位不同的I/O连接。
      * $Cube_0(b_2b_1b_0)=b_2b_1\overline{b_0}$
      * $Cube_1(b_2b_1b_0)=b_2\overline{b_1}b_0$
      * $Cube_2(b_2b_1b_0)=\overline{b_2}b_1b_0$
   4. **均匀洗牌**(shuffle)输入端分成数目相等的两半，前一半和后一半按序一个隔一个地从头至尾依次与输出端相连。$\sigma(b_2b_1b_0)=b_1b_0b_2$。(0)(1,2,4)(3,6,5)(7)
   5. **蝶式置换**(Butterfly)：最高位和最低位交换。$\sigma(b_2b_1b_0)=b_0b_1b_2$。(0)(2)(1,4)(3,6)(5)(7)
   6. **移数置换**：一致向上/下移固定位。a(X)=(X+k) mod N。 
   7. **加减$2^i$（PM2I）置换**：
      * $PM2_{+i}(j) = j+2^i (mod N)$
      * $PM2_{-i}(j) = j-2^i (mod N)$
2. **互联网结构**
   * **多级互连网**：将多套单级互连网串联使用，组成多级互连网。
   * **优点**：缩短通过时间，**提高速度**。**灵活性好**，用各种单级网络组合，产生具有各种特性和连接模式的多级网络。
   * **缺点**：增加设备和成本。
   * **最基本**的多级互联网络：多级**立方体**、**混洗**、**PM2I**。
   * 各种多级网络的**区别**：**开关模块、控制方式和拓扑结构**不同
     * **开关模式**：直连、交换、上播、下播。
     * **控制方式**：级控制(每级状态相同)、单元控制(每个单元自己控制)、部分级控制(第i级所有开关分别用i+1个信号控制)。
     * **拓扑结构**：指各级之间出端和入端相互连接的规则或连接模式。
   * **多级立方体网**
     * 第i级控制信号为1时，实现$CUBE_i$互联函数；为0时，直连。单元只有两个功能(交换，直连)。**级控制**
     * 输入-(恒等置换)-第0级-(子洗牌置换)-第1级-(蝶式置换)-第2级-(逆均匀洗牌置换)-输出
   * **多级混洗交换网**
     * **又称omega网络**，由n级相同的网络组成。每一级都包含一个全混拓扑和随后一列$2^{n-1}$个**四功能**交换单元，(**直连、交换、上播、下播**)，采用**单元控制**方式。







