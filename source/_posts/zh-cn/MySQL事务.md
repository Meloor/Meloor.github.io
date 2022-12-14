---
title: MySQL事务
date: 2020-11-14 22:16:35
tags: [MySQL]
categories:
  - web
  - 数据库
---

[参考博客](https://blog.csdn.net/w_linux/article/details/79666086)讲的非常清楚，下面是补充的笔记

## 事务定义

事务(Transsction)

- 事务：**一个最小的不可再分的工作单元**；通常一个事务对应一个完整的业务(例如银行账户转账业务，该业务就是一个最小的工作单元)
- 一个完整的业务需要批量的 DML(insert、update、delete)语句共同联合完成 **(也有说法包含 selecet?)**
- 事务只和 DML 语句有关，或者说**DML 语句才有事务**。这个和业务逻辑有关，业务逻辑不同，DML 语句的个数不同

* DDL：
  数据库模式定义语言 DDL(Data Definition Language)，是用于描述数据库中要存储的现实世界实体的语言。主要由 create（添加）、alter（修改）、drop（删除）和 truncate（删除）  四个关键字完成。
* DML(Data Manipulation Language)数据操纵语言命令使用户能够查询数据库以及操作已有数据库中的数据。　　如 insert,delete,update,select(插入、删除、修改、检索)等都是 DML.

## 事务四大特征(ACID)

它这里原子性和一致性讲错了，下面为更正过的：
[参考博客](https://blog.csdn.net/liuskyter/article/details/81948310)

- **原子性(A)** ：
  原子性是指事务包含的所有操作**要么全部成功，要么全部失败回滚**，这和前面两篇博客介绍事务的功能是一样的概念，因此事务的操作如果成功就必须要完全应用到数据库，如果操作失败则不能对数据库有任何影响。
- **一致性(C)** ：
  一致性是指事务必须使数据库从一个一致性状态变换到另一个一致性状态，也就是说一个事务**执行之前和执行之后都必须处于一致性状态**。
  > 拿 **转账** 来说，假设用户甲和用户乙两者的钱加起来一共是 5000，那么不管甲和乙之间如何转账，转几次账，事务结束后两个用户的钱相加起来应该还得是 5000，这就是事务的一致性。
- **隔离性(I)** ：事务 A 和事务 B 之间具有隔离性, **隔离级别** 有四个：

  - 读未提交：read uncommitted
  - 读已提交：read committed
  - 可重复读：repeatable read
  - 串行化：serializable
    - 吞吐量太低，用户体验差，事务串行，而不是并发
  - 看下面这两篇，讲的非常好
  - [快速理解脏读、不可重复读、幻读](https://blog.csdn.net/qq_33591903/article/details/81672260)
  - [事务隔离级别](https://blog.csdn.net/qq_33591903/article/details/82079302)

- **持久性(D)** ：是事务的保证，事务终结的标志(内存的数据持久到硬盘文件中)
- **在我的理解中，原子性、隔离性、持久性都是为了保障一致性而存在的，一致性也是最终的目的**

## 事务与数据库底层数据

在事物进行过程中，未结束之前，DML 语句是不会更改底层数据，**只是将历史操作记录一下，在内存中完成记录**。只有在事物结束的时候，而且是成功的结束的时候，才会修改底层硬盘文件中的数据

## 提交与回滚

- 在 MySQL 中，默认情况下，事务是自动提交的，也就是说，只要执行一条 DML 语句就开启了事物，并且提交了事务
