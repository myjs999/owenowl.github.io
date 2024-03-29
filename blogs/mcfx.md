# 【2018 集训队互测 Day 4】小修和小栋玩♂游戏

[链接](https://loj.ac/problem/2490)

## 毒瘤司司出题

我在[这个链接](http://www.research.ibm.com/haifa/ponderthis/challenges/March2018.html)找到的这题，原数据范围只有 $(6,5)$。

我不会于是拿给司，司第二天和我讨论了一个搜索过掉了。

于是司打算搞成集训队互测，自称说新加入的数据也许要用不同的方法过，还给我演示了如何退火。

最后范围是 $(6,5),(7,6),(8,7),(13,5),(13,6),(15,5),(16,5),(20,4)$。

## 冷静分析

一开始没想到，但后来突然发现了一个事实：

如果存在一个 $(n_1,m_1)$ 的答案，那么可以直接应用于所有 $(n,m)$ 上，其中 $n\ge n_1,m\le m_1$。

## 一个沙比的100分做法

全都退火。

## 一个优秀的76分构造

来自 cdsf。

cdsf 说这后面的数据是 IOI 练习赛题。

（cdsf 已经开始准备 IOI 了！）

本质上 cdsf 构造了一个 $(8,8)$ 的方案，给这 $8$ 个灯标号 $0\sim 7$，Alice将亮着的标号都异或起来，与目标数再异或一下就是需要调整的灯的编号。

把它应用于后 $6$ 个点，期望得分 $76$。

## 一个优秀的88分构造

很显然我们可以优化一下 cdsf 的做法。

$0$ 号灯显然可以使用“不进行操作”代替，所以需要的灯的数量变成了 $7$，本质上是一个 $(7,8)$ 的方案。

代码非常简洁。

下面给出一个 $n=2^k-1$，$m=2^k$ 的构造：

```cpp
for (int i = 0; i < 1 << n; i++) {
	int f = 0;
	for (int j = 0; j < n; j++) {
		if ((i >> j) & 1) {
			f ^= j + 1;
		}
	}
	printf("%d ", f & n);
}
```

可以过后 $7$ 个点，期望得分 $88$。

## 一个优秀的100分做法

当时刚拿到这道题的时候，司是如何快速地搜出第一个点的？

首先状压搜一下包含 $12$ 个 $[0,63]$ 的数的集合 $S$，满足 $\forall i\in [0,63]$，$i\in S$ 或 $i \oplus 2^j\in S$。

一共 $3413$ 种。

然后选 $5$ 个出来使得两两没有交就 OK 了。这一步搜索非常快。

## 一个优秀的100分构造

？？？

## 一个优秀的100分手玩

![0](78fed976760cc8baa5f673cda1d208e6.png)