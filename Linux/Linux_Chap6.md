## Chap6 内存管理
* 实模式、保护模式，如何进行模式切换(CRO的PE位)
* 如何启用分页机制(CRO的PG位)
* 段描述符的作用、组成
* 段选择符的作用、组成
* 保护模式下的地址转换过程
* 内核空间和用户空间
* 为什么采用三级分页模式
* 掌握虚拟地址空间和物理地址空间的管理方法
* Linux用户地址空间的分布
  * 为什么要划分一个个区VMA？VMA的查找、删除?
  * mm_struct， vm_area_struct的作用？
  * 描述task_struct,vm_area_struct、mm_struct、页目录表、物理内存之间的关系（结合图）
* Linux如何实现请求页
* 物理地址空间的页面的分配
  * 伙伴算法
  * free_area[],bitmap的作用
  * 结合free_area[],bitmap理解基于伙伴算法的物理页面的分配和回收，并能够会应用。
* 缺页异常处理过程
  * Do_page_fault()、handle_mm_fault(),handle_pte_fault()的作用
* Slab分配器的作用
* 掌握地址的变换。

* **地址变化**
* **伙伴系统**

### 1. Linux内存寻址




### 2. Linux页框管理





### 3. Linux进程地址空间管理







