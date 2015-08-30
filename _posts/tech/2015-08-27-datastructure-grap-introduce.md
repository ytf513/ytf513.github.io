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

- 
