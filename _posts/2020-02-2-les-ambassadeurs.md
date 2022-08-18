---
layout: post
title:  "Les Ambassadeurs, the first Restaurant we Visited in Paris"
author: sal
categories: [ Lifestyle ]
tags: [ France ]
image: assets/images/2.jpg
rating: 4.5
---
# 测试
$\KaTeX$

$\KaTeX$

$$\TeX$$

$$\sum_{i=1}^n i^2$$

># test
>>sdqd
>
>dsasd

 ```cpp
 #include <iostream>
#include <cstdio>
using namespace std;

#define PROBLEM_NAME "network"
#define FILE_IN freopen(PROBLEM_NAME".in", "r", stdin)
#define FILE_OUT freopen(PROBLEM_NAME".out", "w", stdout)
#define USE_FILE_IO FILE_IN; FILE_OUT;

int n, m;

struct UnionFind {
    int dad[100005];

    // 初始化
    void init() {
        for(int i = 1; i <= n; i++)
            dad[i] = i;
    }

    // 查找祖先
    int anc(int x) {
        if(dad[x] == x) return x;
        return dad[x] = anc(dad[x]);
    }

    // 将 x 与 y 连通
    void uni(int x, int y) {
        x = anc(x);
        y = anc(y);

        dad[x] = y;
    }

    // 查询 x 与 y 是否连通
    bool ask(int x, int y) {
        return anc(x) == anc(y);
    }
} s;

struct EdgeInfo {
    int u, v;
} e[200005];

void input() {
    scanf("%d%d", &n, &m);
    s.init();
    for(int i = 1; i <= m; i++)
        scanf("%d%d", &e[i].u, &e[i].v); // 连通网线的 u,v 直接丢弃
    for(int i = 1; i <= m; i++)
        scanf("%d%d", &e[i].u, &e[i].v); // 保留剪断网线的 u,v
}

void work() {
    // 对于剪断网线的 u,v，从 m 到 1 处理，看作从 m 到 1 依次连通网线
    // 找到第一次能使 1 与 n 连通的那一天
    for(int i = m; i >= 1; i--) {
        s.uni(e[i].u, e[i].v); // 连通 e[i]

        if(s.ask(1, n)) {
            printf("%d\n", i);
            break;
        }
    }
}

int main() {
    // USE_FILE_IO;

    input();
    work();

    return 0;
}
```
