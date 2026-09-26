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


## Lorentz transformations as matrices

一个 Lorentz transformation 可以用一个 $4\times4$ 矩阵

```math
\Lambda
```

来表示。

对于一个 four-vector

```math
A,
```

Lorentz transformation 的作用是

```math
A'=\Lambda A.
```

一般来说，一个任意的 $4\times4$ 矩阵都会定义某种 linear transformation。

但相对论中我们并不关心所有 linear transformations，而只关心那些保持 Minkowski inner product 不变的变换。

也就是说，如果

```math
A'=\Lambda A,
\qquad
B'=\Lambda B,
```

我们要求

```math
A'\cdot B'
=
A\cdot B.
```

由于

```math
A\cdot B=A^TgB,
```

所以

```math
A'\cdot B'
=
A^T\Lambda^Tg\Lambda B.
```

为了让这个等于

```math
A^TgB
```

对于任意 $A,B$ 都成立，必须满足

```math
\boxed{
\Lambda^Tg\Lambda=g
}
```

这就是 Lorentz transformation 的 defining condition。这里有一个容易产生的语言混淆：

如果已经称 $\Lambda$ 为 Lorentz transformation，那么再说“我们只考虑其中保持 inner product 不变的 Lorentz transformations”其实是重复的。

更准确的逻辑是：

```math
\text{general linear transformations}
\quad\supset\quad
\text{Lorentz transformations},
```

其中 Lorentz transformations 正是由

```math
\boxed{
\Lambda^Tg\Lambda=g
}
```

定义出来的那一类 linear transformations。

所以这里不是先有一个叫做 Lorentz transformation 的更大集合，再从中挑选保持 inner product 的部分；而是：

> **保持 Minkowski inner product 不变，本身就是 Lorentz transformation 的 defining property。**

因此：

> Lorentz transformations 是所有保持 Minkowski inner product 不变的线性变换。

---

# Lorentz Group and Poincaré Symmetry

这一部分的主线是：

```math
\text{Lorentz transformations}
\longrightarrow
O(3,1)
\longrightarrow
SO^+(3,1)
\longrightarrow
\text{timelike / spacelike / lightlike}
\longrightarrow
\text{Poincaré group}.
```

---

## 1. Lorentz transformations form a group

Lorentz transformations 满足

```math
\Lambda^T g \Lambda = g.
```

如果

```math
\Lambda_1^T g \Lambda_1 = g,
\qquad
\Lambda_2^T g \Lambda_2 = g,
```

那么它们的乘积满足

```math
(\Lambda_1\Lambda_2)^T g (\Lambda_1\Lambda_2)
=
\Lambda_2^T\Lambda_1^T g\Lambda_1\Lambda_2
=
\Lambda_2^T g\Lambda_2
=
g.
```

因此

```math
\Lambda_1\Lambda_2
```

仍然是 Lorentz transformation。

Lorentz transformation 也一定可逆。由

```math
\Lambda^T g\Lambda=g
```

可得

```math
\Lambda^{-1}=g^{-1}\Lambda^T g.
```

在我们的 convention 中

```math
g^{-1}=g,
```

因此

```math
\boxed{
\Lambda^{-1}=g\Lambda^T g
}
```

仍然是 Lorentz transformation。

所以这些变换构成一个 group，记作

```math
\boxed{O(3,1)}
```

或者根据 metric signature convention 写作

```math
O(1,3).
```

这里采用

```math
g=\mathrm{diag}(1,-1,-1,-1).
```

---

## 2. 为什么完整的 Lorentz group 太大？

完整的

```math
O(3,1)
```

不仅包含 rotations 和 boosts，也包含一些 discrete transformations，例如 parity 和 time reversal。

### 2.1 Parity 和 time reversal

Parity 把空间方向全部反过来：

```math
P:\qquad
(t,\mathbf x)
\longrightarrow
(t,-\mathbf x).
```

矩阵形式为

```math
P=
\begin{pmatrix}
1&0&0&0\\
0&-1&0&0\\
0&0&-1&0\\
0&0&0&-1
\end{pmatrix}.
```

它满足

```math
P^TgP=g,
```

所以数学上确实属于 Lorentz group。

Time reversal 为

```math
T:\qquad
(t,\mathbf x)
\longrightarrow
(-t,\mathbf x),
```

对应

```math
T=
\begin{pmatrix}
-1&0&0&0\\
0&1&0&0\\
0&0&1&0\\
0&0&0&1
\end{pmatrix},
```

并且同样满足

```math
T^TgT=g.
```

所以 $P$ 和 $T$ 都属于完整的 $O(3,1)$。

---

### 2.2 数学上的 Lorentz group 和自然界的 Lorentz symmetry

这里需要区分两个概念：

```math
\text{Lorentz transformation}
```

是数学概念，而

```math
\text{the world is Lorentz invariant}
```

是关于物理规律的 statement。

Lorentz transformation 只要求

```math
\Lambda^Tg\Lambda=g.
```

而“世界是 Lorentz invariant”意味着：

> **物理规律在 Lorentz transformations 下保持相同形式。**

对于 boosts 来说，这意味着：

> **所有 inertial frames 中的物理规律具有相同形式。**

一个静止的实验室和一个相对于它做匀速直线运动的实验室，没有谁是物理上特殊的“绝对静止系”。

不同 observers 测得的

```math
t,\quad x,\quad E,\quad p
```

可以不同；不变的是 physical laws 的形式，而不是每一个 measurement value。

---

### 2.3 为什么 weak interaction 会让 parity 成为问题？

Parity 做的是

```math
\mathbf x\rightarrow-\mathbf x,
```

因此 momentum 变成

```math
\mathbf p\rightarrow-\mathbf p.
```

spin 是 axial vector，所以在 parity 下不反号：

```math
\mathbf S\rightarrow\mathbf S.
```

因此 helicity

```math
h\propto\mathbf S\cdot\mathbf p
```

会反号：

```math
h\rightarrow-h.
```

这里 helicity 只表示：

> spin 和 momentum 是同向还是反向。

对于 massive particle，可以换到一个“超过粒子”的 inertial frame，使 momentum 方向翻转，因此 helicity 可以随 reference frame 改变。

对于 massless particle，粒子始终以光速运动，不可能通过合法 Lorentz boost 超过它，因此 helicity 不能通过换 inertial frame 翻转。

需要区分

```math
\boxed{
\text{helicity}\neq\text{chirality}
}
```

一般情况下二者不是同一个概念。

chirality 来自 Dirac spinor 本身的结构：

```math
\psi=\psi_L+\psi_R,
```

其中

```math
\psi_L
=
\frac{1-\gamma^5}{2}\psi,
```

```math
\psi_R
=
\frac{1+\gamma^5}{2}\psi.
```

这里的 left/right 不是普通空间中的“朝左/朝右”，而是 fermion field 的两种 chiral components。

Parity 会交换它们：

```math
\boxed{
\psi_L\leftrightarrow\psi_R
}
```

而 weak charged-current interaction 对左右 chirality 并不对称，因此 parity-transformed interaction 不再等于原来的 interaction。

所以：

```math
\boxed{
P\text{ is not a symmetry of the weak interaction}
}
```

这并不意味着 weak interaction 破坏 Lorentz invariance；它破坏的是 parity 这个 discrete symmetry。

---

### 2.4 Time reversal 的物理含义

Time reversal 不是简单地“把录像倒着播放”。

如果一个过程写成

```math
i\rightarrow f,
```

其中 $i$ 是 initial state，$f$ 是 final state，那么 time reversal 后比较的是

```math
\boxed{
Tf\rightarrow Ti
}
```

因为时间方向反过来以后，原来的 final configuration 成为新的“开始”，原来的 initial configuration 成为新的“结束”。

同时状态本身也要做 time-reversal transformation，例如

```math
\mathbf p\rightarrow-\mathbf p,
```

以及

```math
\mathbf L\rightarrow-\mathbf L.
```

所以 $Tf$ 不是简单的 $f$，而是 $f$ 的 time-reversed state。

---

## 3. Connected component 和 $SO^+(3,1)$

### 3.1 什么叫 connected to the identity？

identity transformation 是

```math
I=
\begin{pmatrix}
1&0&0&0\\
0&1&0&0\\
0&0&1&0\\
0&0&0&1
\end{pmatrix}.
```

一个 transformation 与 identity connected，意思是：

> 可以从 $I$ 出发，通过连续改变 transformation parameters，一点一点走到这个 transformation，并且整个过程中始终停留在 Lorentz group 内。

普通 rotation 是这样的：

```math
R_z(0)=I,
```

然后连续改变 angle $\theta$。

Lorentz boost 也一样：

```math
\Lambda(v=0)=I,
```

然后连续改变 velocity $v$，只要

```math
|v|<1.
```

但 parity 和 time reversal 不与 identity 连通。

---

### 3.2 为什么 parity 不能连续地从 identity 得到？

从 Lorentz condition

```math
\Lambda^Tg\Lambda=g
```

取 determinant：

```math
\det(\Lambda^T)\det(g)\det(\Lambda)
=
\det(g).
```

因为

```math
\det(\Lambda^T)=\det\Lambda
```

并且

```math
\det g\neq0,
```

所以

```math
(\det\Lambda)^2=1.
```

因此

```math
\boxed{
\det\Lambda=\pm1
}
```

identity 满足

```math
\det I=+1,
```

而 parity 满足

```math
\det P=-1.
```

这里不是 $\det g$ 在变化；$g$ 始终固定。

如果存在一条连续路径 $\Lambda(s)$ 从 $I$ 走到 $P$，那么

```math
\det\Lambda(s)
```

作为连续函数就必须从 $+1$ 连续变到 $-1$。

但在 Lorentz group 内，$\det\Lambda$ 只能取 $+1$ 或 $-1$，所以不存在这样一条始终留在 Lorentz group 内的连续路径。

因此 parity 和 identity 位于不同 connected components。

---

### 3.3 Proper orthochronous Lorentz group

Coleman 所说的 connected Lorentz group 通常记为

```math
\boxed{SO^+(3,1)}
```

其中 $S$ 表示 special / proper：

```math
\det\Lambda=+1.
```

上标 $+$ 表示 orthochronous，即保持 future time direction。

对于 proper orthochronous Lorentz transformation，

```math
\Lambda^0{}_0\ge1.
```

为什么？考虑时间基矢

```math
e_0=(1,0,0,0)^T.
```

经过 Lorentz transformation：

```math
e'_0=\Lambda e_0.
```

它的时间分量就是

```math
(e'_0)^0=\Lambda^0{}_0.
```

由于 Lorentz transformation 保持 norm，

```math
(e'_0)^2=e_0^2=1,
```

所以

```math
(\Lambda^0{}_0)^2
-
\sum_i(\Lambda^i{}_0)^2
=1.
```

因此

```math
|\Lambda^0{}_0|\ge1.
```

保持 future direction 选择的是

```math
\boxed{\Lambda^0{}_0\ge1}.
```

于是 $SO^+(3,1)$ 同时排除了 spatial reflection 和 future/past reversal。

---

### 3.4 和普通 rotation 的类比

三维 Euclidean space 中，所有保持 Euclidean inner product 的 transformations 构成

```math
O(3).
```

它既包含 rotations，也包含 reflections。

只保留

```math
\det R=+1
```

得到

```math
SO(3),
```

也就是真正的 proper rotations。

因此可以类比：

```math
O(3)
\supset
SO(3),
```

而

```math
O(3,1)
\supset
SO^+(3,1).
```

前者从所有 orthogonal transformations 中排除 reflections；后者从完整 Lorentz group 中保留与 identity 连通的 rotations 和 boosts。

---

## 4. Timelike, spacelike and lightlike four-vectors

Lorentz transformation 保持

```math
A^2=A_\mu A^\mu
```

不变。

对于

```math
A^\mu=(A^0,\mathbf A),
```

有

```math
A^2=(A^0)^2-|\mathbf A|^2.
```

所以 $A^2$ 的符号也是 Lorentz invariant，于是 four-vectors 自然分成三类。

### 4.1 一个统一的 boost 公式

先通过 ordinary spatial rotation，把 $\mathbf A$ 转到 $x$ 方向：

```math
A^\mu=(A^0,A^1,0,0).
```

沿 $x$ 方向做 Lorentz boost：

```math
\Lambda_x(\beta)
=
\begin{pmatrix}
\gamma&-\gamma\beta&0&0\\
-\gamma\beta&\gamma&0&0\\
0&0&1&0\\
0&0&0&1
\end{pmatrix},
```

其中

```math
\gamma=\frac{1}{\sqrt{1-\beta^2}}.
```

因此

```math
A'^0
=
\gamma(A^0-\beta A^1),
```

```math
A'^1
=
\gamma(A^1-\beta A^0),
```

而

```math
\boxed{
A'^2=A^2,
\qquad
A'^3=A^3
}
```

所以沿 $x$ 方向 boost 只混合 $t$ 和 $x$ components，不会产生新的 $y,z$ components。

---

### 4.2 Timelike

如果

```math
A^2>0,
```

即

```math
(A^0)^2>|\mathbf A|^2,
```

称为 timelike。

在上面的 frame 中，如果要求

```math
A'^1=0,
```

需要

```math
\beta=\frac{A^1}{A^0}.
```

由于 timelike condition 保证

```math
|\beta|<1,
```

所以这是合法 boost。

因此

```math
\boxed{
A^2>0
\quad\Rightarrow\quad
\exists\text{ frame such that }
A'^\mu=(A'^0,\mathbf0)
}
```

massive particle 的 four-momentum

```math
p^\mu=(E,\mathbf p)
```

满足

```math
p^2=E^2-\mathbf p^2=m^2>0,
```

所以是 timelike；对应的特殊 frame 就是 rest frame。

---

### 4.3 Spacelike

如果

```math
A^2<0,
```

即

```math
(A^0)^2<|\mathbf A|^2,
```

称为 spacelike。

如果要求

```math
A'^0=0,
```

需要

```math
\beta=\frac{A^0}{A^1}.
```

spacelike condition 同样保证

```math
|\beta|<1.
```

所以

```math
\boxed{
A^2<0
\quad\Rightarrow\quad
\exists\text{ frame such that }
A'^\mu=(0,\mathbf A')
}
```

---

### 4.4 Lightlike

如果

```math
A^2=0,
```

称为 lightlike 或 null。

此时

```math
(A^0)^2=|\mathbf A|^2.
```

如果想令 $A'^1=0$ 或 $A'^0=0$，都需要

```math
|\beta|=1.
```

但 inertial observer 的 boost 必须满足

```math
|\beta|<1.
```

所以不存在这样的 inertial frame。

因此

```math
\boxed{
A^2=0
}
```

的 vector 既不能变成纯 time direction，也不能变成纯 spatial direction。

photon 的 four-momentum 满足

```math
p^2=0,
```

所以是 lightlike。

---

### 4.5 三种类型为什么不能互相变？

因为

```math
A'^2=A^2,
```

所以 $A^2$ 的符号在任何 Lorentz frame 中都不变：

```math
\text{timelike}\rightarrow\text{timelike},
```

```math
\text{spacelike}\rightarrow\text{spacelike},
```

```math
\text{lightlike}\rightarrow\text{lightlike}.
```

这三类不是人为随便命名，而是 Lorentz symmetry 自然给出的分类。

---

## 5. Spacetime translations and Noether theorem

世界的 spacetime symmetry 不只包括 Lorentz transformations，还包括 spacetime translations：

```math
x^\mu
\longrightarrow
x'^\mu
=
x^\mu+a^\mu,
```

其中 $a^\mu$ 是固定 four-vector。

也就是说：

```math
t\rightarrow t+a^0,
```

以及

```math
\mathbf x\rightarrow\mathbf x+\mathbf a.
```

物理意义是：

> 同一个实验今天做和明天做，fundamental laws 应该相同；

> 同一个实验在这里做和移动到另一个位置做，fundamental laws 也应该相同。

这就是 spacetime translation invariance。

Noether theorem 给出：

```math
\text{time translation}
\longleftrightarrow
\text{energy conservation},
```

```math
\text{space translation}
\longleftrightarrow
\text{momentum conservation}.
```

因此 spacetime translations 整体对应 four-momentum conservation：

```math
\boxed{
p^\mu=\text{conserved}
}
```

Lorentz symmetry 本身也有对应的 Noether quantities：

- spatial rotations 对应 angular momentum；
- boosts 也有相应的 conserved generators。

所以不仅 translations，所有连续 spacetime symmetries 都可以和 Noether theorem 联系起来。

---

## 6. The Poincaré group

把 Lorentz transformations 和 spacetime translations 放在一起，最一般的 transformation 是

```math
\boxed{
x'^\mu
=
\Lambda^\mu{}_{\nu}x^\nu
+
a^\mu
}
```

或者矩阵记号

```math
\boxed{
x'=\Lambda x+a.
}
```

一个 Poincaré transformation 因此由

```math
(\Lambda,a)
```

共同标记。

所有这些 transformations 构成 Poincaré group：

```math
\boxed{
\mathcal P
=
\mathbb R^{1,3}
\rtimes
SO^+(3,1)
}
```

其中

```math
\mathbb R^{1,3}
```

表示 spacetime translation group，而

```math
SO^+(3,1)
```

表示 connected Lorentz group。

---

### 6.1 为什么是 semidirect product，而不是 direct product？

符号

```math
\rtimes
```

表示 semidirect product。

如果两个群只是普通 direct product，那么两部分的 group multiplication 会彼此独立。

但 Poincaré group 中，Lorentz transformation 会作用在 translation vector 上。

设第一个 transformation 为

```math
x'=\Lambda_1x+a_1,
```

第二个 transformation 为

```math
x''=\Lambda_2x'+a_2.
```

代入第一个：

```math
x''
=
\Lambda_2(\Lambda_1x+a_1)+a_2.
```

展开：

```math
x''
=
\Lambda_2\Lambda_1x
+
\Lambda_2a_1
+
a_2.
```

因此 group multiplication 是

```math
\boxed{
(\Lambda_2,a_2)(\Lambda_1,a_1)
=
(\Lambda_2\Lambda_1,\;\Lambda_2a_1+a_2)
}
```

关键是 translation 部分不是简单的

```math
a_1+a_2,
```

而是

```math
\Lambda_2a_1+a_2.
```

也就是说，前一个 translation vector $a_1$ 会先被后一个 Lorentz transformation $\Lambda_2$ 作用。

这正是 semidirect product 的含义：

> 一个 subgroup 会作用在另一个 subgroup 上，所以两部分并不是完全独立的。

一个直观的空间例子是：先平移，再旋转。

```math
x\rightarrow x+a
```

然后

```math
x\rightarrow Rx.
```

合起来得到

```math
x\rightarrow R(x+a)=Rx+Ra.
```

原来的 translation vector $a$ 也被旋转成了 $Ra$。

因此：

```math
\boxed{
\text{direct product: 两部分互不作用}
}
```

而

```math
\boxed{
\text{semidirect product: 一部分会作用在另一部分上}
}
```

所以 Poincaré group 写成

```math
\boxed{
\mathcal P
=
\mathbb R^{1,3}\rtimes SO^+(3,1)
}
```

而不是普通的 $\times$。

---

## 7. 这一部分的整体图景

今天这部分可以压缩成：

```math
\boxed{
O(3,1)
\supset
SO^+(3,1)
}
```

完整的 $O(3,1)$ 包含 rotations、boosts、parity、time reversal 等；课程主要使用与 identity 连通的

```math
SO^+(3,1).
```

Lorentz transformations 保持

```math
A^2
```

不变，因此 four-vectors 被自然分成 timelike、spacelike 和 lightlike 三类。

再加入 spacetime translations：

```math
x\rightarrow\Lambda x+a,
```

就得到 Poincaré symmetry：

```math
\boxed{
\text{Poincaré symmetry}
=
\text{Lorentz symmetry}
+
\text{spacetime translations}.
}
```

而更精确的 group structure 是

```math
\boxed{
\mathcal P
=
\mathbb R^{1,3}\rtimes SO^+(3,1).
}
```

所以 Coleman 这一段实际上是在建立 relativistic QFT 后面最基本的 spacetime symmetry framework。


## Relativistic notation: derivatives, integrals, delta functions and Fourier transforms

这一部分主要是在建立 relativistic field theory 里之后会反复出现的一套 notation。

核心思想是：

> 在相对论中，时间和空间应该尽可能统一地写成 four-dimensional objects，并且我们希望公式在 Lorentz transformations 下保持自然的形式。

---

### Four-dimensional derivative

定义四维导数：

```math
\partial_\mu
\equiv
\frac{\partial}{\partial x^\mu}.
```

如果

```math
x^\mu=(t,\mathbf x),
```

那么在 convention

```math
g_{\mu\nu}
=
\mathrm{diag}(1,-1,-1,-1)
```

下，

```math
\partial_\mu
=
\left(
\frac{\partial}{\partial t},
\nabla
\right).
```

这里

```math
\nabla
=
\left(
\frac{\partial}{\partial x},
\frac{\partial}{\partial y},
\frac{\partial}{\partial z}
\right).
```

$\partial_\mu$ 是一个 covariant object。

它之所以这样变换，可以从 chain rule 看出来。

Lorentz transformation 为

```math
x'^\mu
=
\Lambda^\mu{}_\nu x^\nu.
```

因此

```math
x^\nu
=
(\Lambda^{-1})^\nu{}_\mu x'^\mu.
```

所以

```math
\partial'_\mu
=
\frac{\partial}{\partial x'^\mu}
=
\frac{\partial x^\nu}{\partial x'^\mu}
\frac{\partial}{\partial x^\nu},
```

即

```math
\boxed{
\partial'_\mu
=
(\Lambda^{-1})^\nu{}_\mu
\partial_\nu.
}
```

这就是 covariant transformation law。

---

### Covariant 和 contravariant

这里顺便区分两个常见词。

upper-index object

```math
A^\mu
```

叫 contravariant vector，它按

```math
\boxed{
A'^\mu
=
\Lambda^\mu{}_\nu A^\nu
}
```

变换。

lower-index object

```math
A_\mu
```

叫 covariant vector，它按

```math
\boxed{
A'_\mu
=
(\Lambda^{-1})^\nu{}_\mu A_\nu
}
```

变换。

因此可以先简单记成：

```math
\text{contravariant}
\leftrightarrow
\text{upper index},
```

```math
\text{covariant}
\leftrightarrow
\text{lower index}.
```

metric $g_{\mu\nu}$ 负责在两者之间升降指标。

---

### Raising the derivative index

定义

```math
\partial^\mu
=
g^{\mu\nu}\partial_\nu.
```

由于

```math
g^{\mu\nu}
=
\mathrm{diag}(1,-1,-1,-1),
```

所以

```math
\partial^\mu
=
\left(
\frac{\partial}{\partial t},
-\nabla
\right).
```

升指标以后，$\partial^\mu$ 按 contravariant vector 的方式变换：

```math
\boxed{
\partial'^\mu
=
\Lambda^\mu{}_\nu
\partial^\nu.
}
```

本质上是因为 metric 与 Lorentz transformation 相容：

```math
\Lambda^Tg\Lambda=g.
```

所以 raising/lowering index 不会破坏 Lorentz transformation structure。

---

## The d'Alembert operator

定义 d'Alembert operator：

```math
\Box
\equiv
\partial_\mu\partial^\mu.
```

展开：

```math
\boxed{
\Box
=
\frac{\partial^2}{\partial t^2}
-
\nabla^2
}
```

其中

```math
\nabla^2
=
\frac{\partial^2}{\partial x^2}
+
\frac{\partial^2}{\partial y^2}
+
\frac{\partial^2}{\partial z^2}.
```

---

### 为什么 $\Box$ 是 Lorentz invariant？

因为

```math
\partial_\mu
```

按 covariant law 变换：

```math
\partial'_\mu
=
(\Lambda^{-1})^\nu{}_\mu
\partial_\nu,
```

而

```math
\partial^\mu
```

按 contravariant law 变换：

```math
\partial'^\mu
=
\Lambda^\mu{}_\rho
\partial^\rho.
```

因此 contraction 以后：

```math
\partial'_\mu\partial'^\mu
=
(\Lambda^{-1})^\nu{}_\mu
\Lambda^\mu{}_\rho
\partial_\nu\partial^\rho.
```

由于

```math
(\Lambda^{-1})^\nu{}_\mu
\Lambda^\mu{}_\rho
=
\delta^\nu{}_\rho,
```

得到

```math
\boxed{
\partial'_\mu\partial'^\mu
=
\partial_\nu\partial^\nu.
}
```

因此

```math
\boxed{
\Box'=\Box.
}
```

这和 four-vector inner product

```math
A_\mu B^\mu
```

Lorentz invariant 是完全相同的结构。

一个 lower index 带来 $\Lambda^{-1}$，一个 upper index 带来 $\Lambda$，contract 以后两者抵消。

---

### 为什么这个算符重要？

在 relativistic field theory 中，我们希望 field equation 在不同 inertial frames 中具有相同形式。

例如 Klein–Gordon equation：

```math
\boxed{
(\Box+m^2)\phi=0.
}
```

因为 $\Box$ 是 Lorentz scalar operator，$m$ 也是 scalar，所以这个 equation 天然具有 Lorentz-covariant form。

因此 $\Box$ 可以看成 relativistic theory 中非常自然的二阶 differential operator。

---

## Four-dimensional integration

定义

```math
d^4x
=
dt\,dx\,dy\,dz.
```

因此 spacetime integral 写成

```math
\int d^4x.
```

在 field theory 中 action 通常写成

```math
\boxed{
S
=
\int d^4x\,\mathcal L(x).
}
```

Lorentz transformation 下

```math
x'=\Lambda x.
```

积分测度通过 Jacobian 变换：

```math
d^4x'
=
|\det\Lambda|\,d^4x.
```

对于 proper Lorentz transformation，

```math
\det\Lambda=+1,
```

所以

```math
\boxed{
d^4x'=d^4x.
}
```

如果 Lagrangian density 是 Lorentz scalar：

```math
\mathcal L'(x')
=
\mathcal L(x),
```

那么 action 满足

```math
\boxed{
S'=S.
}
```

所以四维积分是 relativistic field theory 的自然语言。

---

## 为什么 $d^3x$ 没有同样简单？

三维积分

```math
\int d^3x
```

通常表示：

> 在某个固定时刻，对整个空间积分。

也就是在

```math
t=\text{const}
```

的三维 hypersurface 上积分。

但是 Lorentz boost 会把时间和空间混合：

```math
t'
=
\gamma(t-\beta x).
```

因此即使两个事件在一个 frame 中满足

```math
t_1=t_2,
```

只要

```math
x_1\neq x_2,
```

一般就会有

```math
t'_1\neq t'_2.
```

所以：

> 一个 observer 的“同时”并不是另一个 observer 的“同时”。

这就是 relativity of simultaneity。

因此 $d^3x$ 是某个特定 time slice 上的 measure，并不像 $d^4x$ 那样直接表现出 Lorentz invariance。

---

## Delta functions

三维 delta function 满足

```math
\int d^3x\,
\delta^{(3)}(\mathbf x-\mathbf a)
f(\mathbf x)
=
f(\mathbf a).
```

它的作用是从积分中挑出

```math
\mathbf x=\mathbf a
```

这一点。

四维版本为

```math
\delta^{(4)}(x),
```

满足

```math
\boxed{
\int d^4x\,
\delta^{(4)}(x-a)
f(x)
=
f(a).
}
```

并且

```math
\delta^{(4)}(x)
=
\delta(t)
\delta(x)
\delta(y)
\delta(z).
```

---

### 为什么四维 delta function 在 QFT 中重要？

在 spacetime 中，

```math
\delta^{(4)}(x-y)
```

表示：

```math
x^\mu=y^\mu.
```

也就是两个 spacetime points 完全重合。

因此它天然适合描述 locality。

而在 momentum space 中，经常出现

```math
\boxed{
(2\pi)^4
\delta^{(4)}
\left(
p_{\mathrm{in}}-p_{\mathrm{out}}
\right).
}
```

这等价于同时要求

```math
E_{\mathrm{in}}
=
E_{\mathrm{out}},
```

以及

```math
\mathbf p_{\mathrm{in}}
=
\mathbf p_{\mathrm{out}}.
```

所以四维 delta function 直接编码

```math
\boxed{
\text{four-momentum conservation}.
}
```

---

## Fourier transform

相对论中自然使用 four-dimensional Fourier transform。

一种常见 convention 是

```math
\boxed{
\phi(x)
=
\int
\frac{d^4p}{(2\pi)^4}
e^{-ip\cdot x}
\tilde\phi(p)
}
```

以及 inverse transform：

```math
\boxed{
\tilde\phi(p)
=
\int d^4x\,
e^{ip\cdot x}
\phi(x).
}
```

不同教材可能交换正负号，只要前后一致即可。

---

### 为什么 exponent 写成 $p\cdot x$？

因为

```math
p^\mu
```

和

```math
x^\mu
```

都是 four-vectors。

因此

```math
p\cdot x
=
g_{\mu\nu}p^\mu x^\nu
```

是 Lorentz invariant。

展开：

```math
\boxed{
p\cdot x
=
Et-\mathbf p\cdot\mathbf x.
}
```

Lorentz transformation 下

```math
p'=\Lambda p,
\qquad
x'=\Lambda x,
```

因此

```math
p'\cdot x'
=
p^T\Lambda^Tg\Lambda x.
```

由

```math
\Lambda^Tg\Lambda=g,
```

得到

```math
\boxed{
p'\cdot x'
=
p\cdot x.
}
```

所以 plane wave phase

```math
e^{-ip\cdot x}
```

是 Lorentz invariant。

这就是为什么 relativistic theory 中 plane waves 自然写成 four-dimensional inner product 的形式。

---

## Fourier transform 的另一个关键作用

在 momentum space 中，derivative 会变成 multiplication。

如果

```math
\phi(x)
\sim
e^{-ip\cdot x},
```

那么

```math
\partial_\mu
e^{-ip\cdot x}
=
-ip_\mu
e^{-ip\cdot x}.
```

因此可以写成对应关系

```math
\boxed{
\partial_\mu
\longleftrightarrow
-ip_\mu.
}
```

于是

```math
\Box
=
\partial_\mu\partial^\mu
```

变成

```math
\boxed{
\Box
\longleftrightarrow
-p_\mu p^\mu
=
-p^2.
}
```

所以 differential equation 在 momentum space 中经常会变成 algebraic equation。

例如：

```math
(\Box+m^2)\phi=0
```

Fourier transform 后变成

```math
(-p^2+m^2)\tilde\phi(p)=0.
```

因此

```math
\boxed{
p^2=m^2.
}
```

也就是

```math
\boxed{
E^2-\mathbf p^2=m^2.
}
```

所以 relativistic field equation 和 relativistic dispersion relation 在 Fourier space 中会非常直接地联系起来。

---

## Why these notations matter

这些符号并不是彼此独立的技巧，而是在表达同一套 relativistic structure：

```math
\partial_\mu
```

是 four-dimensional derivative；

```math
\Box
=
\partial_\mu\partial^\mu
```

是 Lorentz-invariant differential operator；

```math
d^4x
```

是 natural spacetime integration measure；

```math
\delta^{(4)}(x)
```

用于表示 spacetime coincidence / locality；

```math
\delta^{(4)}
(p_{\mathrm{in}}-p_{\mathrm{out}})
```

表示 four-momentum conservation；

而

```math
e^{-ip\cdot x}
```

使用 Lorentz-invariant phase。

Fourier transform 则连接

```math
\boxed{
\text{spacetime description}
\longleftrightarrow
\text{energy-momentum description}.
}
```

因此 Coleman 在这里补这些 notation，并不是单纯为了记号方便，而是在建立之后 QFT 中反复使用的 relativistic mathematical language。


## First relativistic quantum system: a free spinless particle

Coleman 考虑的第一个 relativistic quantum system 是：

> 无限空间中的一个自由、无内部结构、不发生相互作用的单粒子。

这里“无内部结构”意味着暂时没有：

- spin；
- internal excitation；
- 其他内部 quantum numbers。

因此描述这个单粒子状态时，最重要的自由度就是它的 momentum。

---

### Momentum eigenstates as a basis

选择 momentum eigenstates

```math
|\mathbf p\rangle
```

作为 Hilbert space 的 basis。

它们满足

```math
\hat{\mathbf P}|\mathbf p\rangle
=
\mathbf p|\mathbf p\rangle.
```

这里最开始我的疑问是：

> 是不是因为这个粒子没有内部结构，所以只用 momentum 就可以描述它？

更准确地说，并不是粒子“只有一个态”，而是所有不同的

```math
|\mathbf p\rangle
```

构成了一组 basis states。

一个一般的 quantum state 可以写成这些 momentum eigenstates 的线性叠加：

```math
\boxed{
|\psi\rangle
=
\int d^3p\,
\psi(\mathbf p)
|\mathbf p\rangle
}
```

其中

```math
\psi(\mathbf p)
=
\langle\mathbf p|\psi\rangle
```

是这个 state 在 momentum basis 中的 coefficients，也就是 momentum-space wavefunction。

---

## Wave packet

单独一个 definite-momentum state

```math
|\mathbf p\rangle
```

在 position representation 中对应 plane wave：

```math
\langle x|p\rangle
\propto
e^{-ip\cdot x}.
```

这样的 wave 并不 localized，而是铺满整个空间。

一个真实的 localized state 通常需要把很多不同 momentum 的 plane waves 叠加：

```math
\psi(x)
=
\int d^3p\,
f(\mathbf p)
e^{i\mathbf p\cdot\mathbf x}.
```

这样的 superposition 就叫做 wave packet。

因此可以先这样理解：

```math
\boxed{
\text{definite momentum}
\Rightarrow
\text{plane wave, delocalized}
}
```

而

```math
\boxed{
\text{superposition of momenta}
\Rightarrow
\text{wave packet, can be localized}
}
```

---

## Abstract state and wavefunction

这里还需要区分

```math
|\psi\rangle
```

和

```math
\psi(x).
```

真正的 quantum state 是 abstract Hilbert-space vector

```math
|\psi\rangle.
```

position-space wavefunction 是它在 position basis 下的 components：

```math
\boxed{
\psi(x)
=
\langle x|\psi\rangle.
}
```

同样，在 momentum basis 中：

```math
\boxed{
\tilde\psi(\mathbf p)
=
\langle\mathbf p|\psi\rangle.
}
```

所以

```math
|\psi\rangle,
\qquad
\psi(x),
\qquad
\tilde\psi(\mathbf p)
```

不是三个不同的 physical states。

它们是同一个 state 在不同 representation / basis 下的表示。

因此

```math
e^{-ip\cdot x}
```

也不是说“quantum state 本身就是一个 exponential function”，而是 momentum eigenstate

```math
|p\rangle
```

在 position basis 中的 representation。

---

## Energy and the mass shell

对于 invariant mass 为

```math
\mu
```

的自由粒子，

```math
p^\mu=(E,\mathbf p).
```

four-momentum 的 Minkowski norm 是

```math
p^\mu p_\mu
=
E^2-\mathbf p^2.
```

对于这个粒子：

```math
\boxed{
p^\mu p_\mu=\mu^2.
}
```

也就是

```math
\boxed{
E^2-\mathbf p^2=\mu^2.
}
```

因此

```math
E^2
=
\mathbf p^2+\mu^2,
```

取正能量 branch：

```math
\boxed{
E_{\mathbf p}
=
\sqrt{\mathbf p^2+\mu^2}.
}
```

这里一开始我的疑问是：

> Minkowski norm 明明是 $E^2-\mathbf p^2$，为什么 energy formula 里面变成了加号？

原因只是把

```math
E^2-\mathbf p^2=\mu^2
```

移项：

```math
E^2=\mathbf p^2+\mu^2.
```

没有出现新的物理量。

---

### What is the mass shell?

```math
\boxed{
p^2=\mu^2
}
```

不是在定义一种新的质量，而是在说：

> 对一个 invariant mass 固定为 $\mu$ 的粒子，允许的 four-momenta $(E,\mathbf p)$ 必须满足这个条件。

所有满足

```math
E^2-\mathbf p^2=\mu^2
```

的 four-momenta 在 momentum space 中形成一个 hypersurface，叫做 mass shell。

因此：

```math
\mu
```

是粒子固定的 Lorentz-invariant mass；

而

```math
E,\mathbf p
```

会随着 particle state 和 observer 改变。

但无论如何，

```math
\boxed{
E^2-\mathbf p^2=\mu^2
}
```

保持不变。

在 rest frame：

```math
\mathbf p=0,
```

所以

```math
E_{\mathrm{rest}}=\mu
```

因为这里使用

```math
c=1.
```

恢复单位就是

```math
E_{\mathrm{rest}}=\mu c^2.
```

以后这里的 mass 都理解为 invariant mass。

---

## What does rotational invariance mean in quantum mechanics?

经典空间中的 rotation 用

```math
R
```

表示。

它可以直接作用在 ordinary vectors 上：

```math
\mathbf p
\longrightarrow
R\mathbf p.
```

但是 quantum state

```math
|\psi\rangle
```

不属于 ordinary three-dimensional physical space，而属于 Hilbert space。

因此不能简单把同一个 matrix $R$ 直接作用在

```math
|\psi\rangle
```

上。

我们需要在 Hilbert space 中找到一个 operator

```math
\boxed{
U(R)
}
```

来实现 physical rotation $R$。

所以：

```math
R
```

描述 physical space 中的 rotation；

而

```math
U(R)
```

描述同一个 symmetry 在 Hilbert space 上怎样作用。

---

## Why is $U(R)$ linear?

Quantum mechanics 的 states 可以 superpose：

```math
|\psi\rangle
=
a|\psi_1\rangle
+
b|\psi_2\rangle.
```

rotation 不应该破坏这种 superposition structure。

因此必须要求

```math
\boxed{
U(R)
\left(
a|\psi_1\rangle+b|\psi_2\rangle
\right)
=
aU(R)|\psi_1\rangle
+
bU(R)|\psi_2\rangle.
}
```

所以 symmetry transformation 在 Hilbert space 上由 linear operator 实现。

这里的 linearity 和后面的 group multiplication property 是两个不同的要求：

- linearity 描述 $U$ 如何作用在 quantum states 上；
- representation property 描述不同 rotations 之间的 group structure 如何被保存。

---

## Unitarity

rotation 是 physical symmetry，所以不应该改变 transition probabilities。

因此要求 inner product 保持不变：

```math
\langle U(R)\psi|U(R)\phi\rangle
=
\langle\psi|\phi\rangle.
```

而

```math
\langle U\psi|U\phi\rangle
=
\langle\psi|
U^\dagger U
|\phi\rangle.
```

所以必须有

```math
\boxed{
U^\dagger(R)U(R)=I.
}
```

也就是

```math
\boxed{
U^{-1}(R)=U^\dagger(R).
}
```

因此 $U(R)$ 是 unitary operator。

物理意义：

> symmetry transformation 必须保持 quantum inner products，从而保持 probabilities。

---

## Preserving the group structure

如果 physical rotations 满足

```math
R_1R_2=R_3,
```

那么它们在 Hilbert space 上的 operators 也应该实现相同的 composition：

```math
\boxed{
U(R_1)U(R_2)
=
U(R_1R_2).
}
```

也就是说：

> 先做 $R_2$ 再做 $R_1$，应该和直接做 combined rotation $R_1R_2$ 对应。

因此 map

```math
\boxed{
R\longmapsto U(R)
}
```

保留了 rotation group 的 multiplication structure。

这就是一个 group representation。

所以：

> $U(R)$ 是 rotation group 在 Hilbert space 上的 unitary representation。

---

## Overall phase and projective representations

Quantum mechanics 中，

```math
|\psi\rangle
```

和

```math
e^{i\alpha}|\psi\rangle
```

代表同一个 physical state。

这里

```math
\alpha
```

不是 rotation angle，而是 quantum state 的 overall phase。

因为

```math
|e^{i\alpha}|=1,
```

所以例如 transition probability：

```math
|\langle\phi|\psi\rangle|^2
```

在

```math
|\psi\rangle
\rightarrow
e^{i\alpha}|\psi\rangle
```

以后不会改变。

因此 physical state 更准确地说是 Hilbert space 中的一条 ray：

```math
\boxed{
|\psi\rangle
\sim
e^{i\alpha}|\psi\rangle.
}
```

所以 representation law 在 quantum mechanics 中可以稍微放宽。

不一定严格要求

```math
U(R_1)U(R_2)
=
U(R_1R_2),
```

而可以允许：

```math
\boxed{
U(R_1)U(R_2)
=
e^{i\omega(R_1,R_2)}
U(R_1R_2).
}
```

其中

```math
\omega(R_1,R_2)
```

是由这两个 group elements 决定的 phase function。

因为两边作用到 state 上以后只差一个 overall phase，所以代表相同的 physical state。

这叫做 projective representation。

---

## Why half-integer spin makes this important

这一点在 spin-$\frac12$ 中尤其重要。

spin-$\frac12$ 的 rotation operator 具有形式

```math
U(R(\theta))
=
e^{-i\theta\,\mathbf n\cdot\boldsymbol\sigma/2}.
```

因此 exponent 中出现

```math
\frac{\theta}{2}.
```

对于 ordinary spatial rotation：

```math
R(2\pi)=I.
```

但对于 spin-$\frac12$ state：

```math
U(2\pi)=-I.
```

所以

```math
|\psi\rangle
\longrightarrow
-|\psi\rangle
=
e^{i\pi}|\psi\rangle.
```

它与原来的 state 只差一个 overall phase，因此仍然代表同一个 physical state。

而

```math
U(4\pi)=I.
```

Coleman 在这里暂时忽略 projective representation 的细节，是因为当前讨论的是 spinless particle，不需要马上进入 half-integer spin 和 $SU(2)$ 的结构。

---

## Current understanding

这一部分真正建立的是：

```math
\boxed{
\text{physical spacetime symmetry}
\longrightarrow
\text{unitary operators on Hilbert space}
}
```

对于 rotations：

```math
R
\longmapsto
U(R).
```

其中：

```math
U^\dagger(R)U(R)=I
```

保证 quantum probabilities 不变；

而

```math
U(R_1R_2)
=
U(R_1)U(R_2)
```

保证 rotation group 的 algebraic structure 被保留下来。

自由 spinless particle 则用

```math
|\mathbf p\rangle
```

作为 momentum basis，并满足 mass-shell condition

```math
\boxed{
p^2=\mu^2.
}
```

因此 Coleman 这里开始真正把前面讨论的 spacetime symmetry 和 quantum Hilbert space 接到一起：

```math
\boxed{
\text{Lorentz / rotation group}
\quad\longrightarrow\quad
\text{representations on quantum states}.
}
```
