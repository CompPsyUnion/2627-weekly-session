# Segment Tree

## The problem & core concept

### The baseline problem

(RMQ problem) Given an array of size $N$, support 2 ops:

1. Update single / range element(s).
2. Query single / range statistic.

1, 2, 3, 4, 5, 6, 7, 8, 9, 10

### Why Naive Fails

- Static array: $O(1)$ update, $O(N)$ query.
- Prefix sums: $O(1)$ range sum query, but $O(N)$ update.

## Usage

### Compare with other commonly used

- Sparse Table
- BIT

### Using in more advanced algorithm

- Persistent Segment Tree
- HLD
- scanline
- segment tree optimize dp
- 2d tree
- ...

## Basic

### core member preview
- val, lazy;
- **pushup()** child -> father [detail](#pushup)
- **pushdown()** father -> child; passdown modification (recursively, lazy tag) (cover later) [detail](#pushdown)
- build() initialization [detail](#build)
- modify() [detail](#modify)
    - single: binary search
    - range (cover later)
- query()
    - stage 1 [detail](#query1)
    - stage 2 [detail](#query2)

### build

Segment tree is a **full binary tree**:
to use the index property between father and child nodes:

- father = child / 2;
- lc = father * 2;
- rc = father * 2 + 1;

d&c recursively to build the tree.

1-indexed  
space: 4*N

### pushup

Using child info to update father info;

The efficiency and availabity of `pushup()` decides whether the info can be maintained by segment tree

- $O(1)$, $O(k)$
- maintainable
- [l, r] -> [left, mid] / [mid + 1, r]

### query1

$4\log N$

case analysis:

define, $q = [ql, qr], c = [l, r]$

- $\emptyset$
- $intersect$
- $[l, r] \subset [ql, qr]$
- $[ql, qr] \subset [l, r]$
    - mid?
    - left / right / both

traverse on tree, max = height(tree);

---

### pushdown

If I modify range elements (n), what you will do?

- brute force: repeat single update * n?
- rebuild segment tree?
- imitate query?

Using lazy tag to store the update actions;

> def: the operation pending to the nodes on the child tree (exclude itself)

pushdown to children only when they are needed;

### query2

The special case is this:

- $[ql, qr] \subset [l, r]$
    - mid?
    - left / right / both

trigger pushdown(); Make sure the lazy tag of ancestor has been released

### modify

same as query2

## Problem solving

### template

[luogu P3372: Segment Tree 1](https://www.luogu.com.cn/problem/P3372)

AC code example:

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
typedef long long int64;

const int MAXN = 1e5 + 5;
int n, m, op, x, y;
int64 a[MAXN], k;

struct Seg {int64 sum, lazy; } t[MAXN << 2];

void pushup(int idx) { t[idx].sum = t[idx << 1].sum + t[idx << 1 | 1].sum; }

void build(int idx, int l, int r)
{
    if (l == r) {
        t[idx].sum = a[l];
        return;
    }
    int mid = (l + r) >> 1;
    build(idx << 1, l, mid);
    build(idx << 1 | 1, mid + 1, r);
    pushup(idx);
}

void pushdown(int idx, int l, int r)
{
    if (t[idx].lazy) {
        int64& lazy = t[idx].lazy;
        int mid = (l + r) >> 1;
        t[idx << 1].sum += (mid - l + 1) * lazy;
        t[idx << 1].lazy += lazy;
        t[idx << 1 | 1].sum += (r - mid) * lazy;
        t[idx << 1 | 1].lazy += lazy;
        lazy = 0;
    }
}

int64 query(int idx, int l, int r, int ql, int qr)
{
    if (ql <= l && qr >= r) return t[idx].sum;
    int mid = (l + r) >> 1;
    int64 ans = 0;
    pushdown(idx, l, r);
    if (ql <= mid) ans += query(idx << 1, l, mid, ql, qr);
    if (qr > mid) ans += query(idx << 1 | 1, mid + 1, r, ql, qr);
    return ans;
}

void modify(int idx, int l, int r, int ml, int mr, int64 k)
{
    if (ml <= l && mr >= r) {
        t[idx].sum += (r - l + 1) * k;
        t[idx].lazy += k;
        return;
    }
    int mid = (l + r) >> 1;
    pushdown(idx, l, r);
    if (ml <= mid) modify(idx << 1, l, mid, ml, mr, k);
    if (mr > mid) modify(idx << 1 | 1, mid + 1, r, ml, mr, k);
    pushup(idx);
}

int main()
{
    cin >> n >> m;
    for (int i = 1; i <= n; i++) cin >> a[i];
    build(1, 1, n);
    while (m--) {
        cin >> op;
        if (op == 1) {
            cin >> x >> y >> k;
            modify(1, 1, n, x, y, k);
        }
        else {
            cin >> x >> y;
            cout << query(1, 1, n, x, y) << '\n';
        }
    }

    return 0;
}
```


### variant

[AtCoder ABC473.F: A/AB Insertion](https://atcoder.jp/contests/abc473/tasks/abc473_f)

AC code example:

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

const int MAXN = 5e5 + 5;
int n, q, pre[MAXN];
string s;
struct Seg { int mn, lazy; } t[MAXN << 2];

void pushup(int idx) { t[idx].mn = min(t[idx << 1].mn, t[idx << 1 | 1].mn); }

void build(int idx, int l, int r)
{
    if (l == r) {
        t[idx] = { pre[l], 0 };
        return;
    }
    int mid = (l + r) >> 1;
    build(idx << 1, l, mid);
    build(idx << 1 | 1, mid + 1, r);
    pushup(idx);
}

void pushdown(int idx)
{
    if (t[idx].lazy) {
        int& lazy = t[idx].lazy;
        t[idx << 1].mn += lazy;
        t[idx << 1].lazy += lazy;
        t[idx << 1 | 1].mn += lazy;
        t[idx << 1 | 1].lazy += lazy;
        lazy = 0;
    }
}

void modify(int idx, int l, int r, int ml, int mr, int v)
{
    if (ml <= l && mr >= r) {
        t[idx].mn += v;
        t[idx].lazy += v;
        return;
    }
    int mid = (l + r) >> 1;
    pushdown(idx);
    if (ml <= mid) modify(idx << 1, l, mid, ml, mr, v);
    if (mr > mid) modify(idx << 1 | 1, mid + 1, r, ml, mr, v);
    pushup(idx);
}

int query(int idx, int l, int r, int ml, int mr)
{
    if (ml <= l && mr >= r) return t[idx].mn;

    int mid = (l + r) >> 1, ans = 1e9;
    pushdown(idx);
    if (ml <= mid) ans = min(ans, query(idx << 1, l, mid, ml, mr));
    if (mr > mid) ans = min(ans, query(idx << 1 | 1, mid + 1, r, ml, mr));
    return ans;
}

int main()
{
    cin >> n >> s >> q;
    s = " " + s;
    for (int i = 1; i <= n; i++) pre[i] = pre[i - 1] + (s[i] == 'A' ? 1 : -1);
    build(1, 0, n);
    while (q--) {
        int op, pos, l, r;
        char c;
        cin >> op;
        if (op == 1) {
            cin >> pos >> c;
            if (s[pos] == c) continue;
            s[pos] = c;
            if (c == 'A') modify(1, 0, n, pos, n, 2);
            else modify(1, 0, n, pos, n, -2);
        }
        else {
            cin >> l >> r;
            puts(query(1, 0, n, l, r) < query(1, 0, n, l - 1, l - 1) ? "No" : "Yes");
        }
    }

    return 0;
}
```

### More

- [luogu P3373: Segment Tree 2](https://www.luogu.com.cn/problem/P3373)
- [luogu P3870 (^)](https://www.luogu.com.cn/problem/P3870)
---
- [luogu P2572 (Advanced statistics)](https://www.luogu.com.cn/problem/P2572)
- [ABC468.F (Segment Tree + DP)](https://atcoder.jp/contests/abc468/tasks/abc468_f)
- [ABC477.F (Segment Tree + Scanline)](https://atcoder.jp/contests/abc477/tasks/abc477_f)

## End

Teammate recruitment (personal only; not CPU official)

if you are interested in further cp studying and contest:  
[qrcode](/images/qrcode.jpg)

bio/practice:

- [all](/images/practice.png)
- [nowcoder](/images/nowcoder.png)
- [atcoder](/images/atcoder.png)
- [codeforces](/images/codeforces.png)

bio/contest:

- [Prefecture / Country awards in some competitions](/images/competition.png)


Thanks for listening