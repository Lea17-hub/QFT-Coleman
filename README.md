# QFT-Coleman

## 导论：相对论与多粒子

### 问：为什么在洛伦兹对称性加持下，相对论量子力学反而变难了？

**答：** 因为多粒子的产生。  
更多对称性，但也因为更多粒子的产生而带来了更多自由度。

思考一个过程：**pion 散射**。

当相对论效应变得重要时，即

```math
E_{\text{kin}} \sim mc^2
```

同时 **pair production** 也会出现。

但即便在动能低于这个阈值时，也不能完全忽略多粒子态的效应。

---

## Perturbation theory

这时老师开始计算微扰下的能量修正。

二阶修正的一般形式为

```math
\Delta E_L^{(2)}
=
\sum_H
\frac{|\langle H|V|L\rangle|^2}
{E_L-E_H}
```

这里：

- $|L\rangle$：低能、少粒子态；
- $|H\rangle$：高能、多粒子态；
- $V$：把低能态和高能多粒子态耦合起来的 interaction；
- $\langle H|V|L\rangle$：对应的 coupling matrix element。

如果把问题极度简化成两个态，可以写成

```math
H=
\begin{pmatrix}
E_L & g\\
g^* & E_H
\end{pmatrix}
```

其中

```math
g=\langle H|V|L\rangle
```

表示低能态和高能态之间的耦合强度。

这里不是说真实系统只有两个态，而是用一个低能 sector 和一个代表性的高能多粒子 sector 来理解 mixing。

---

## 为什么看二阶修正？

一阶能量修正是

```math
\Delta E_L^{(1)}
=
\langle L|V|L\rangle
```

它描述的是：微扰对低能态本身产生的直接能量偏移。

但如果我们关心的是**低能态通过 interaction 与高能多粒子态发生 mixing 后，对低能能量造成的间接影响**，那么最先出现的是二阶：

```math
L \rightarrow H \rightarrow L
```

因此在最简单的两态模型里，

```math
\Delta E_L^{(2)}
=
\frac{|g|^2}{E_L-E_H}
```

描述的正是这种 mixing 带来的修正。

---

## 为什么多粒子态的效应会被抑制？

多粒子态通常比低能态高出一个很大的能量尺度，

```math
E_H-E_L \sim mc^2
```

因此二阶修正中有一个很大的分母：

```math
\Delta E_{\text{multi}}
\sim
\frac{|g|^2}{mc^2}
```

所以高能多粒子态对低能物理的影响会被压低。

老师给出了一个粒子对态的抑制尺度，大致为

```math
\frac{E_{\text{low}}}{mc^2}
```

需要注意的是，这里还隐含了一个额外假设：coupling matrix element 的典型尺度与低能系统的能量尺度相关。

这个量级关系并不是单靠二阶微扰公式自动得到的，而要依赖具体 interaction。

---

## 与 relativistic kinetic correction 的比较

相对论能量展开为

```math
E
=
\sqrt{p^2c^2+m^2c^4}
=
mc^2
+
\frac{p^2}{2m}
-
\frac{p^4}{8m^3c^2}
+\cdots
```

其中非相对论动能是

```math
T_{\text{NR}}
=
\frac{p^2}{2m}
```

第一个 relativistic kinetic correction 是

```math
\Delta T_{\text{rel}}
=
-\frac{p^4}{8m^3c^2}
```

因此相对修正量级为

```math
\frac{|\Delta T_{\text{rel}}|}{T_{\text{NR}}}
\sim
\frac{T_{\text{NR}}}{mc^2}
```

所以 relativistic kinetic correction 同样由类似的小参数控制：

```math
\frac{E_{\text{low}}}{mc^2}
```

这说明：

> 一般来说，当 relativistic kinetic correction 开始重要时，多粒子态的效应往往也会出现在相近的参数阶数。

---

## 一个特殊体系：Hydrogen atom

氢原子是一个特殊体系。

对于氢原子，**pair-production / multi-particle effect** 相较于 **kinetic relativistic correction** 小很多，因此 Dirac 的氢原子理论即便没有包含完整的粒子对效应，依然可以得到非常好的结果。

---

## 当前理解

- 微扰 $V$ 不一定是普通的位置势能 $V(x)$，它可以是任何小的 interaction term。
- 一阶修正看的是 diagonal matrix element：

```math
\langle L|V|L\rangle
```

- 二阶修正开始体现 off-diagonal mixing：

```math
\langle H|V|L\rangle
```

- 多粒子态之所以在低能下被抑制，是因为它们和低能态之间有很大的能量间隔。
- relativistic kinetic correction 和 multi-particle correction 会出现相近的低能展开参数。

# QFT-Coleman

## Lecture 1：Natural Units, Four-Vectors and Lorentz Invariance

Coleman 一开始先统一计量单位。

采用 natural units：

```math
c=1,
\qquad
\hbar=1.
```

有时还会进一步选择一个参考质量尺度

```math
m_{\mathrm{ref}}=1.
```

这样做以后，很多原本带有不同单位的物理量可以用同一个基本尺度表示。

其中，设

```math
c=1
```

意味着速度是以光速作为单位来衡量的，因此普通宏观运动通常满足

```math
v\ll 1.
```

而设

```math
\hbar=1
```

意味着角动量是以一个量子单位 $\hbar$ 来衡量的。宏观系统的角动量通常包含极大量的 $\hbar$，因此往往有

```math
L\gg 1.
```

所以在 natural units 下，经典宏观世界常表现为

```math
v\ll 1,
\qquad
L\gg 1.
```

---

## Four-vectors

在狭义相对论中，时间和空间不能再完全分开处理，而是统一写成一个 four-vector。

时空坐标写成

```math
x^\mu=(t,\mathbf{x})
```

或者显式地写成

```math
x^\mu=
(t,x^1,x^2,x^3).
```

四动量写成

```math
p^\mu=(E,\mathbf{p}).
```

在一般单位制下，四动量和四波矢之间满足

```math
p^\mu=\hbar k^\mu.
```

由于这里取

```math
\hbar=1,
```

因此直接得到

```math
p^\mu=k^\mu.
```

在狭义相对论中，一个非常重要的问题就是：

> 什么样的量在不同惯性参考系之间仍然保持不变？

这就引出了 four-vector 的 inner product。

---

## Minkowski inner product

对于两个 four-vectors

```math
A^\mu=(A^0,\mathbf A),
\qquad
B^\mu=(B^0,\mathbf B),
```

定义 Minkowski inner product：

```math
A\cdot B
=
A^0B^0-\mathbf A\cdot\mathbf B.
```

也就是说

```math
A\cdot B
=
A^0B^0
-
A^1B^1
-
A^2B^2
-
A^3B^3.
```

为了把这个写法压缩下来，引入 Minkowski metric：

```math
g_{\mu\nu}
=
\mathrm{diag}(1,-1,-1,-1).
```

显式地，

```math
g_{\mu\nu}
=
\begin{pmatrix}
1&0&0&0\\
0&-1&0&0\\
0&0&-1&0\\
0&0&0&-1
\end{pmatrix}.
```

于是内积可以写成

```math
A\cdot B
=
g_{\mu\nu}A^\mu B^\nu.
```

这里使用了 Einstein summation convention：重复出现的指标自动求和。

---

## 为什么这个和矩阵写法是同一个东西？

一开始我不太明白为什么还可以写成

```math
A\cdot B=A^TgB.
```

实际上，这和

```math
g_{\mu\nu}A^\mu B^\nu
```

完全是同一个运算，只是一个用 index notation，一个用 matrix notation。

把 four-vector 看成列向量：

```math
A=
\begin{pmatrix}
A^0\\
A^1\\
A^2\\
A^3
\end{pmatrix},
\qquad
B=
\begin{pmatrix}
B^0\\
B^1\\
B^2\\
B^3
\end{pmatrix}.
```

先让 metric 作用在 $B$ 上：

```math
gB
=
\begin{pmatrix}
B^0\\
-B^1\\
-B^2\\
-B^3
\end{pmatrix}.
```

再从左边乘

```math
A^T=
\begin{pmatrix}
A^0&A^1&A^2&A^3
\end{pmatrix},
```

就得到

```math
A^TgB
=
A^0B^0
-
A^1B^1
-
A^2B^2
-
A^3B^3.
```

因此

```math
\boxed{
A\cdot B
=
g_{\mu\nu}A^\mu B^\nu
=
A^TgB
}
```

这里的 metric $g$ 可以理解为：

> 它规定了 four-vector 之间的 inner product 应该怎样计算。

普通 Euclidean space 中，metric 是单位矩阵 $I$，所以

```math
\mathbf a\cdot\mathbf b
=
a^TIb
=
a^Tb.
```

而 Minkowski spacetime 的 metric 不是 $I$，而是

```math
g=
\mathrm{diag}(1,-1,-1,-1),
```

所以时间项和空间项之间出现了不同的符号。

---

## Lowering an index

既然 metric 可以作用在一个 four-vector 上，就可以定义 lowering operation：

```math
A_\mu
=
g_{\mu\nu}A^\nu.
```

对于

```math
A^\mu=
(A^0,A^1,A^2,A^3),
```

有

```math
A_\mu
=
(A^0,-A^1,-A^2,-A^3).
```

也就是说：

```math
A_0=A^0,
```

而空间分量满足

```math
A_1=-A^1,
\qquad
A_2=-A^2,
\qquad
A_3=-A^3.
```

因此 Minkowski inner product 还可以写成

```math
A\cdot B
=
A_\mu B^\mu
=
A^\mu B_\mu.
```

所以目前几种写法都是等价的：

```math
\boxed{
A\cdot B
=
g_{\mu\nu}A^\mu B^\nu
=
A_\mu B^\mu
=
A^\mu B_\mu
=
A^TgB
}
```

特别地，一个 four-vector 和自己的内积为

```math
A^2
=
A_\mu A^\mu
=
(A^0)^2-|\mathbf A|^2.
```

---

## 什么是惯性参考系？

在讨论 Lorentz transformation 之前，先明确什么叫 **inertial frame（惯性参考系）**。

一个参考系如果满足：

> 不受力的物体在其中保持静止或做匀速直线运动，

那么这个参考系就是惯性系。

也就是说，惯性系本身不加速、不转弯。

例如：

- 地面上的实验室，可以近似看成一个惯性系；
- 一列以恒定速度做直线运动的火车，也可以近似看成另一个惯性系；
- 如果火车开始加速、刹车或转弯，那么它就不再是惯性系。

狭义相对论主要讨论的，就是**不同惯性系之间的关系**。

设两个惯性系：

- $S$：站台上的观察者；
- $S'$：相对 $S$ 以恒定速度运动的火车上的观察者。

对于同一个事件，$S$ 中可能给出坐标

```math
(t,x,y,z),
```

而 $S'$ 中给出的坐标可能是

```math
(t',x',y',z').
```

这些坐标分量本身一般不同。

---

## Lorentz invariance 到底是什么意思？

所谓 Lorentz invariant，意思是：

> 不同惯性参考系中的观察者，虽然会给同一个事件不同的时间和空间坐标，但某些特定的物理量保持不变。

最重要的例子就是 spacetime interval：

```math
\Delta s^2
=
(\Delta t)^2
-
(\Delta x)^2
-
(\Delta y)^2
-
(\Delta z)^2.
```

这里使用了

```math
c=1.
```

如果在另一个惯性系中测得

```math
\Delta t',
\quad
\Delta x',
\quad
\Delta y',
\quad
\Delta z',
```

那么 Lorentz transformation 保证

```math
\boxed{
\Delta s'^2
=
\Delta s^2
}
```

也就是说：

```math
(\Delta t')^2
-
(\Delta x')^2
-
(\Delta y')^2
-
(\Delta z')^2
=
(\Delta t)^2
-
(\Delta x)^2
-
(\Delta y)^2
-
(\Delta z)^2.
```

所以“不变”的不是每一个 component，而是这个特定组合。

这和普通空间旋转非常类似。

二维空间中，一个点经过 rotation 后：

```math
(x,y)
\rightarrow
(x',y'),
```

虽然 $x$ 和 $y$ 都改变了，但

```math
x^2+y^2
```

保持不变。

狭义相对论中也是类似的：

> rotation 保持 Euclidean distance，  
> Lorentz transformation 保持 Minkowski spacetime interval。

因此，Lorentz transformation 可以理解为：

> 不同惯性参考系之间的坐标变换，同时保持 Minkowski geometry 不变。

## Lorentz invariance 到底是什么意思？

所谓 Lorentz invariant，意思是：

> 换到另一个惯性参考系以后，four-vector 的 components 会变，但 Minkowski inner product 不变。

设 Lorentz transformation 为

```math
A'=\Lambda A,
\qquad
B'=\Lambda B.
```

变换后的 inner product 是

```math
A'\cdot B'
=
(A')^TgB'.
```

代入

```math
A'=\Lambda A,
\qquad
B'=\Lambda B,
```

得到

```math
A'\cdot B'
=
(\Lambda A)^Tg(\Lambda B).
```

利用

```math
(\Lambda A)^T=A^T\Lambda^T,
```

于是

```math
A'\cdot B'
=
A^T\Lambda^Tg\Lambda B.
```

因此，如果希望对于任意 $A$ 和 $B$ 都满足

```math
A'\cdot B'
=
A\cdot B,
```

就必须有

```math
\boxed{
\Lambda^Tg\Lambda=g
}
```

这样：

```math
A'\cdot B'
=
A^T\Lambda^Tg\Lambda B
=
A^TgB
=
A\cdot B.
```

所以

```math
\boxed{
\Lambda^Tg\Lambda=g
}
```

并不是一个独立、莫名其妙的矩阵条件。

它表达的正是：

> Lorentz transformation 必须保持 Minkowski inner product 不变。

---

## 和普通 rotation 的类比

在普通 Euclidean space 中，

```math
\mathbf a\cdot\mathbf b
=
a^TIb.
```

如果做 rotation：

```math
a'=Ra,
\qquad
b'=Rb,
```

那么

```math
a'\cdot b'
=
a^TR^TIRb.
```

为了让 ordinary inner product 不变，需要

```math
R^TIR=I.
```

由于 $I$ 是单位矩阵，这就是

```math
R^TR=I.
```

而在 Minkowski spacetime 中，只是把 $I$ 换成了 $g$：

```math
R^TR=I
```

对应

```math
\Lambda^Tg\Lambda=g.
```

因此可以把 Lorentz transformation 看成 Minkowski spacetime 中对应于 rotation 的变换：

> rotation 保持 Euclidean inner product，  
> Lorentz transformation 保持 Minkowski inner product。

---

## 当前理解

这一部分最重要的逻辑是：

```math
g_{\mu\nu}
```

定义了 Minkowski spacetime 中如何计算 inner product。

因此

```math
A\cdot B
=
g_{\mu\nu}A^\mu B^\nu
=
A^TgB.
```

metric 还可以用来 lowering index：

```math
A_\mu=g_{\mu\nu}A^\nu.
```

而 Lorentz transformation 的核心条件

```math
\Lambda^Tg\Lambda=g
```

正是为了保证

```math
A'\cdot B'
=
A\cdot B.
```

所以这几个原本看起来分散的公式，其实是在描述同一件事：

> **Minkowski spacetime 有一种特殊的几何结构，而 Lorentz transformation 是保持这种几何结构不变的变换。**







