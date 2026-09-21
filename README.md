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
