---
layout: post
title: 数据结构之图的简介
category: 技术
tags: 技术,编程
keywords: 技术,编程
description: 数据结构之图的简介
---

## 什么是图（Graph）
表示多对多的关系，包含：

- 一组顶点：V（Vertex）表示顶点集合
- 一组边：E（Edge）表示边的集合

通过顶点对表示边：(v,w) 属于 E；有向边<v,w>表示v到w的边

## 怎么在程序中表示图

- 邻接矩阵G[N][N]--N个顶点从0到N-1编号
    + 若i到j的边，G[i][j]=1；否则 G[i][j]=0

- 邻接表（Adjacency List）是图的一种链式存储结构，对图的每个顶点建立一个单链表。每个结点有三个域组成：其中邻接点域（adjvex）指示与顶点v1邻接的点在图中的位置，链域(nextarc)指示下一条边与弧的结点；数据域（info）存储和边或弧相关的信息，如权值等。 

- 十字链表

- 邻接多重表

## 最小生成树

n个结点之间需要联通最少需要n-1个结点，最多需要n(n-1)/2个结点，如何构造联通网的最小代价生成树就是最小生成树的问题。其中有普里姆算法和克鲁斯卡尔算法。
