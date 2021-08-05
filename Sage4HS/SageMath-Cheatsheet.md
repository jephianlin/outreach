---
title: SageMath Cheatsheet
tags: tutorial
---

# SageMath Cheatsheet

![Sage4HS GitHub repo](https://raw.githubusercontent.com/jephianlin/outreach/master/Sage4HS/Sage4HS-qr.png "Sage4HS GitHub repo")


完整教學請參考 Sage4HS GitHub repo  
[https://github.com/jephianlin/outreach/tree/master/Sage4HS](https://github.com/jephianlin/outreach/tree/master/Sage4HS)  
（修課同學請點進連結，並先完成課前準備）

---
## 01. 數與多項式（Numbers and Polynomials）

### 運算
* 加 `+`
* 減 `-`
* 乘 `*`
* 除 `/` 
* 次方 `**` 或 `^`（後者在純 Python 環境不適用）
* 根號 `sqrt`
* 整數除法 `//`
* 餘數 `%` 

### 列表
* 建立列表 `a = [1, 2, 3]`
* 回傳第 `k` 個元表 `a[k]`
* 轉換資料型態為列表 `list`

### 多項式
* 展開 `expand`
* 因式分解 `factor`
* 化簡 `simplify`
* 將符號表達式轉成有理係數多項式 `p = (x+1).polynomial(QQ)`
* 將 $x$ 代入 $10$ `p.subs(10)` 或 `p(10)`
* 最小多項式 `sqrt(2).minpoly()`

### 定義函數 
```Python
def function_name(var1, ..., var2=0, ...):
    do something
    return something
```

### 代數系統
* 整數（環） `ZZ`
* 有理數（體） `QQ`
* 實數（體） `RR`
* 複數（體） `CC`

### 其它
* 執行當前的 cell `shift + enter` 
* 階層 `factorial`
* 質因數分解 `factor` 
* 回傳小數逼近 `N`
* 顯示資料型態 `type`

---
## 02. 數列與級數（Sequences and Series）

### 列表
* `0` 到 `n-1` 的列表 `range(n)`
* 計算列表中所有元素的總和 `sum`
* 在列表末項加入新元表 `a = [1,2]; a.append(3) `

### 迴圈與判斷式
```Python
for x in range(101):
    if is_prime(x):
        print(x^2)
```

### 列表推導式
```Python
[x^2 for x in range(1,101) if is_prime(x)]
```

---
## 03. 排列組合與離散機率（Combinatorics and Discrete Probability）

### 生成器
* 回傳所有的排列 `Permutations([1,2,3], 2)` 
* 回傳所有的組合 `Combinations([1,2,3], 2)`

### 多項式係數
* 係數 `p = expand((1+x)^5); p.coefficient(x^2)`
* 二項式係數 `binomial(n,k)`

### `random` 套件
```Python 
import random
```
* 會從輸入的列表 `a` 中隨機挑出一個元素 `random.choice(a)` 
* 隨機從 `a` 到 `b` 之間（包含兩端點）取出一個數 `random.randint(a,b)`

---
## 04. 函數與其圖形（Functions and Plotting）

### 字典
* 建立字典 `a = {'one':1, 'two':2}`
* 回傳索引為 `one` 的值 `a['one']`
* 所有的索引 `a.keys()`
* 所有的值 `a.values()`

### 變數
* Sage 中的預設變數 `x`
* 設立新變數 `w = var('w')`

### 函數
* 建立函數 `f(x) = x^2` 或 `f(x,y） = x^2 + y^2`
* 將函數中的 `x` 代入數值 `f(2)`
* 將函數中的 `x` 和 `y` 代數數值 `f(3,4)`

### `lambda` 運算式
```Python
f = lambda k: k^2
```

### 數學函數
* 三角函數 `sin`, `cos`, `tan`, `cot`, `sec`, `csc`
* 圓周率 `pi`
* 虛數 `I`

### 函數繪圖及設定參數
```Python
f(x) = x^2
f.plot(xmin=-3, xmax=3, 
       ymin=-1, ymax=10,
       color='red', 
       legend_label='$x^2$'，
       linestyle='--'
      )
```
* $x$ 軸邊界 `xmin`、`xmax`
* $y$ 軸邊界 `ymin`、`ymax`
* 曲線顏色 `color`
* 圖例文字 `legend_label`
* 曲線格式 `linestyle`

---
## 05. 向量與物件（Vectors and Objects）

### 向量
* 向量 $(a,b)$ `v = vector([a,b])`
* 以起點 $(c,d)$ 繪製向量 `v.plot(start=(c,d))`
* 伸縮 $k$ 倍 `k * v`
* 兩向量內積 `v1 * v2`

### 類別與物件
```Python
class fraction:
    def __init__(self,a,b): ## 注意：是兩個底線_
        self.numerator = a
        self.denominator = b
        
q = fraction(a,b)
```
* 判斷是否為某類別 `isinstance(q, fraction)`
* 定義如何顯示物件`__repr__ `
* 定義包含關係 `__contains__`
* 定義加法 `__add__`
* 定義減法 `__sub__`
* 定義乘法 `__mul__`
* 定義除法 `__div__` 
* 定義兩個物件相等的條件 `__eq__`
* 定義不等於 `__ne__`
* 列出所有屬性及函數 `dir`
* 列出所有的屬性 `vars`

---
## 06. 線性幾何（Linear Geometry）

### 向量運算
* 向量 `v` 的範數 `v.norm()`
* 向量 `v` 與向量 `w` 內積 `v.dot_product(w)`
* 向量 `v` 與向量 `w` 外積 `v.cross_product(w)`

---
## 07. 矩陣與 NumPy（Matrices and NumPy）

### 矩陣
```Python
A = matrix([
        [0, 1, 2],
        [1, 2, 3],
        [2, 3, 4]
    ])
    ##注意 Sage 裡列和行都是從 0 開始數
```
* 第 $i,j$-項 `A[i,j]`
* 子矩陣 `A[list of rows, list of columns]`
* 第 $i$ 列 `A[i,:]`
* 第 $j$ 行 `A[:,j]`

### NumPy
```Python
import numpy as np

A = np.array([
        [0, 1, 2],
        [1, 2, 3],
        [2, 3, 4]
    ])
    
v = np.array([1,1,1])
```
* 矩陣乘法 `np.dot(A, v)`
* 元素介在 $0\sim 1$ 的 $a\times b$ 隨機矩陣`np.random.rand(a,b)`
* 建立相同大小的全 $1$ 陣列 `np.ones_like(A)` 
* 元素總和 `np.sum(A)` 

### Magic Method
* 評估一個區塊的計算時間 `%%timeit`

---
## 08. 機率與統計（Probability and Statistics）

### 隨機抽樣
* 在 `A = [1,2,3]` 中隨機抽一個元素 `np.random.choice(A)` 

### matplotlib
```Python
import matplotlib.pyplot as plt
```
* 直方圖 `plt.hist`

---
## 09. 近似值與極限（Approximation and Limit）

### NumPy
* 建立陣列時指定資料型態 `np.array([1，2，3], dtype=float)`
* 在 `[a,b]` 區間等間隔分布 `k` 個點 `np.linspace(a,b,k)`
* 設定陣列顯示的精準度 `np.set_printoptions(precision=k)`

### matplotlib
* 散佈圖`plt.scatter`
* 強制 $x$-軸和 $y$-軸單位長一致 `plt.axis('equal')` 
* 顯示圖例 `plt.legend()`

---
## 10. 微積分（Calculus）

### 函數與變數
* 設定變數 `x = var('x')`
* 無限大 `oo`
* 定義函數 `f(x) = x^2` 或 `f = x^2`
* 將`x=a` 代入函數 `f.subs(x=a)`
* 取極限 `limit`
* 微分 `f.derivative`
* 積分`f.integral`

---
## 11. 矩陣理論（Matrix Theory）

### 矩陣
* 輸入矩陣 `A = matrix(2, [1,2,3,4])`
* 轉置 `A.transpose()`
* 反矩陣 `A.inverse()`
* 行列式值 `A.determinant()`
* 對角化 `A.eigenmatrix_right()`
* 右核 `ker =  A.right_kernel()`
* 基底 `ker.basis()`
* $n\times n$ 單位矩陣 `identity_matrix(n)`

###  linalg 
```Python
import numpy as np
import scipy.linalg as LA
```
* 隨機矩陣 `A = np.random.randn(3,3)`
* 解特徵值及特徵向量（一般矩陣） `LA.eig(A)`
* 解特徵值及特徵向量（一般矩陣） `LA.eigh(A)`

---
## 12. 圖論（Graph Theory）

### 輸入圖
```Python
V = [0,1,2,3,4,5]
E = [(0,1), (1,2), (1,4), (3,4), (4,5)]
g = Graph([V, E])
```

### 內建的圖
* `n` 點路徑圖 `graphs.PathGraph(n)`
* `n` 點圈圖 `graphs.CycleGraph(n)`
* `n` 點完全圖 `graphs.CompleteGraph(n)`
* `n` 點星圖 `graphs.StarGraph(n)`
* `d` 維超立方體 `graphs.CubeGraph(d)`
* 彼得森圖 `graphs.PetersenGraph()`
* $G(n,p)$ 隨機圖（`n` 點，每邊以獨立機率 `p` 出現) `graphs.RandomGNP(n,p)`
* `n` 點隨機樹 `graphs.RandomTree(n)`

### 圖性質
* 點 `g.vertices()`
* 邊 `g.edges(labels=False)`
* 點數 `g.order()`
* 邊數 `g.size()` 
* 度序列 `g.degree_sequence()`
* 是否連通 `g.is_connected()`
* 腰圍 `g.girth()`
* 相鄰矩陣 `g.adjacency_matrix()`
* 拉普拉斯矩陣 `g.laplacian_matrix()`

### 圖相關操作
* 加點 $v$ `g.add_vertex(v)`
* 加邊 $uv$ `g.add_edge(v,u)`
* 將兩張圖 $g_1$ 及 $g_2$ 合併 `g1.disjoint_union(g2)`

### 顯示圖
```Python
g.show(figsize=[2,2], 
       vertex_labels=False, 
       vertex_size=10, 
       vertex_colors={'red':[1,3], 'blue':[2,4], 'orange':[0]}, 
       edge_style='--')
```
* 畫布大小 `figsize`
* 是否顯示點的名稱 `vertex_labels`
* 點大小 `vertex_size`
* 點顏色 `vertex_colors`
* 邊格式 `edge_style`

### 設定點顯示的位置
```Python
graphs.CycleGraph(4)
pos = {0:(0,0), 1:(1,0), 2:(0,1), 3:(1,1)}
g.set_pos(pos)
g.show(figsize=[2,2])
```
* 回傳位置字典 `pos = g.get_pos()`
* 設置位置字典 `g.set_pos(pos)`
* 在建立圖時設定位置字典 `Graph([V, E], pos=pos)`








