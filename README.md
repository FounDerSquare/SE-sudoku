# 软工个人项目-数独

##### 博客地址：

https://www.cnblogs.com/FounDerSquare/p/12130905.html

 

##### 一、任务

- 实现一个能够生成数独终局并且能求解数独问题的控制台程序。
- 提交的代码要求经过代码质量分析工具的分析并消除所有的警告。
- 对项目的首个版本使用性能分析工具找出性能瓶颈并改进。
- 及时维护仓库与博客。

##### 二、PSP表格

| **PSP2.1**                                 | **Personal Software Process  Stages** | **预估耗时**  **（分钟）** | **实际耗时**  **（分钟）** |
| ------------------------------------------ | ------------------------------------- | -------------------------- | -------------------------- |
| **Planning**                               | 计划                                  | 30                         |                            |
| l **Estimate**                             | 估计任务需要时间                      | 30                         |                            |
| **Development**                            | 开发                                  | 2820                       |                            |
| l **Analysis**                             | 需求分析（与技术学习）                | 60                         |                            |
| l **Design Spec**                          | 生成设计文档                          | 60                         |                            |
| l **Design Review**                        | 设计复审（同行评审）                  | 180                        |                            |
| l **Coding Standard**                      | 代码规范                              | 30                         |                            |
| l **Design**                               | 具体设计                              | 120                        |                            |
| l **Coding**                               | 具体编码                              | 1260                       |                            |
| l **Code Review**                          | 代码复审                              | 90                         |                            |
| l **Test**                                 | 测试                                  | 1020                       |                            |
| **Report**                                 | 报告                                  | 300                        |                            |
| l **Test Report**                          | 测试报告                              | 120                        |                            |
| l **Size Measurement**                     | 计算工作量                            | 60                         |                            |
| l **Postmortem& process improvement plan** | 事后总结并提出改进计划                | 120                        |                            |
|                                            | 合计                                  | 3150                       |                            |

##### 三、解题思路描述

​    分析具体任务需求可以将任务分为三部分。

​    第一部分，生成各不相同的，最多1,000,000个空行隔开的9×9数独终局。一个数独终局的生成可以用第一行的平移来形成。第一行很容易做到1~9不重复，只要下面几行在平移的时候每一行平移错开的位数不同，就可以保证9个行9个列都是不包含重复数字。为了让3×3方格也满足规则，平移时，每三行一组，组内每行间平移错开的位数相差3。这样每三行每三列存在逻辑关系，就能保证3×3方格满足规则。（感觉很像密码学里的凯撒密码）

​    大致算法思路是这样，再加上命令行参数的设置和导出到文件的设置就可以了。

​    第二部分，求解数独。参考网上一些方法打算采用dfs。

​		①检查从1到9哪个可以被放在当前的空位；

​		②找到一个暂时可行的数就先放进去，挪到下一个空位进行操作①；

​		③如果遇到一个空位填不进去数，返回上一层dfs的递归，重新操作①；

​		④直到所有的位置都填满了数，递归结束。

​	第三部分，性能优化（如果有余力尝试搞GUI）。