# 矩阵微积分（Matrix Calculus）

本项目整理了 Jan R. Magnus《A Gentle Introduction to Matrix Calculus》的核心内容，面向需要进行矩阵求导、优化推导、统计与计量应用的读者。

## 项目简介

该仓库提供一份系统化的矩阵微积分参考，重点覆盖：

- 矩阵导数的正确定义
- 微分法与识别定理
- 一阶与二阶导数（Hessian）
- 约束/无约束优化
- Kronecker 积、vec 算子、交换矩阵、复制矩阵等常用工具

适用场景：

- 手推矩阵求导公式
- 机器学习/统计模型中的目标函数优化
- 计量经济学中的矩阵微分计算

## 仓库结构

```text
matrix-calculus/
├─ README.md
├─ SKILL.md
└─ references/
   └─ magnus_matrix_calculus.md
```

## 核心内容速览

### 两大支柱

1. 矩阵导数的严格定义  
2. 微分（differential）方法

### 六个基础工具

1. Trace（迹）  
2. 线性/二次型  
3. Kronecker 积  
4. vec 算子  
5. 交换矩阵（Commutation Matrix）  
6. 复制矩阵（Duplication Matrix）

## 推荐阅读路径

1. 先读 `references/magnus_matrix_calculus.md` 中关于导数定义与微分规则的部分  
2. 再学习一阶导数与常见公式推导  
3. 最后阅读二阶微分、Hessian 与优化应用章节

## 参考资料

- Jan R. Magnus, *A Gentle Introduction to Matrix Calculus*
- 本仓库完整整理版：`references/magnus_matrix_calculus.md`

## 说明

当前仓库以教程与参考资料为主，不包含独立可执行代码模块。后续可按需补充示例推导脚本、练习题与答案索引。
