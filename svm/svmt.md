我们要推导 最大间隔分类器（Maximum Margin Classifier），目标是找到一个超平面 $w^T x + b = 0$，使得它到最近样本点的距离最大化。
## 1. 几何间隔的定义 (Geometric Margin)
给定一个超平面 $w^T x + b = 0$，空间中任意一点 $x_i$ 到该平面的垂直距离 $d$ 为：
$$d_i = \frac{|w^T x_i + b|}{\|w\|}$$ 
在 SVM 中，我们使用的标签是 $y_i \in \{+1, -1\}$。如果分类正确，则 $y_i(w^T x_i + b) > 0$，所以距离可以写成：
$$d_i = \frac{y_i(w^T x_i + b)}{\|w\|}$$ 
## 2. 目标函数 (Objective Function)
我们希望找到最大的间隔 $\gamma$，使得所有样本点到超平面的距离都至少为 $\gamma$：
$$\max_{w, b} \gamma \quad \text{s.t.} \quad \frac{y_i(w^T x_i + b)}{\|w\|} \ge \gamma, \quad i=1, \dots, n$$ 
## 3. 固定缩放 (Scaling)
注意，如果我们成倍改变 $w$ 和 $b$（例如变成 $2w$ 和 $2b$），超平面的位置不变，但上面的不等式会变得难以计算。
为了简化，我们令 $w^T x + b$ 的绝对值在最近的样本点（支持向量）上等于 1：
$$\min_{i} |w^T x_i + b| = 1$$ 
此时，间隔公式简化为：
$$\text{Margin} = \frac{1}{\|w\|}$$ 
## 4. 最终优化问题 (Final Optimization)
最大化 $\frac{1}{\|w\|}$ 等价于最小化 $\|w\|^2$。为了后续求导方便，我们加上系数 $\frac{1}{2}$。
这就是 SVM 的核心优化公式：
$$\min_{w, b} \frac{1}{2} \|w\|^2$$ $$\text{subject to: } y_i(w^T x_i + b) \ge 1, \quad i=1, \dots, n$$ 
## 总结

   1. 目标：把 $\|w\|$ 变小，从而让间隔 $\frac{1}{\|w\|}$ 变大。
   2. 约束：确保所有点都被正确分类，且都在“安全区”（即距离 $\ge 1$）之外。



为了求解 SVM 的约束优化问题，我们需要将原问题（Primal Problem）转化为对偶问题（Dual Problem）。这样做不仅方便求解，还能引入核函数（Kernel Trick）。
## 1. 构建拉格朗日函数 (Lagrangian)
我们的原目标是：
$$\min_{w, b} \frac{1}{2} \|w\|^2 \quad \text{s.t.} \quad 1 - y_i(w^T x_i + b) \le 0$$ 
引入拉格朗日乘子 $\alpha_i \ge 0$（每个样本点对应一个 $\alpha_i$），构建函数：
$$L(w, b, \alpha) = \frac{1}{2} \|w\|^2 + \sum_{i=1}^{n} \alpha_i [1 - y_i(w^T x_i + b)]$$ 
## 2. 求偏导并令其为 0 (KKT 条件)
为了找到最小值，我们对 $w$ 和 $b$ 分别求偏导：

* 对 $w$ 求导：
$$\frac{\partial L}{\partial w} = w - \sum_{i=1}^{n} \alpha_i y_i x_i = 0 \implies \mathbf{w = \sum_{i=1}^{n} \alpha_i y_i x_i}$$ 这说明最优的 $w$ 是样本点的线性组合。
* 对 $b$ 求导：
$$\frac{\partial L}{\partial b} = -\sum_{i=1}^{n} \alpha_i y_i = 0 \implies \mathbf{\sum_{i=1}^{n} \alpha_i y_i = 0}$$ 

## 3. 代入原式得到对偶问题 (Dual Problem)
将上述两个结论带回 $L(w, b, \alpha)$ 中，消去 $w$ 和 $b$，目标转化为只关于 $\alpha$ 的极大值问题：
$$\max_{\alpha} \sum_{i=1}^{n} \alpha_i - \frac{1}{2} \sum_{i=1}^{n} \sum_{j=1}^{n} \alpha_i \alpha_j y_i y_j (x_i \cdot x_j)$$ $$\text{s.t.} \quad \sum_{i=1}^{n} \alpha_i y_i = 0, \quad \alpha_i \ge 0$$ 
## 4. 为什么这个推导很重要？

   1. 只看内积 ($x_i \cdot x_j$)：公式中样本点仅以点积形式出现。这意味着如果我们想处理非线性问题，只需要把 $x_i \cdot x_j$ 替换成 核函数 $K(x_i, x_j)$。
   2. 稀疏性 (Sparsity)：根据 KKT 条件中的互补松弛性（Complementary Slackness），大部分 $\alpha_i$ 都会等于 0。
   * 如果 $\alpha_i > 0$，则该点满足 $y_i(w^T x_i + b) = 1$，这些点就是支持向量 (Support Vectors)。
      * 模型最终只由这些极少数的支持向量决定。
   
KKT 条件（Karush-Kuhn-Tucker conditions）是数学优化领域的“终极判别标准”。
在 SVM 中，我们把一个带约束的难题（要在不越界的情况下找最小 $w$）转化为了拉格朗日函数。KKT 条件就是告诉我们：在这个函数的最低点，必须满足以下 4 个条件。
## 1. 驻点条件 (Stationary)
$$\nabla_w L = 0 \quad \text{和} \quad \nabla_b L = 0$$ 这就像在平滑的山谷寻找最低点。导数为 0 意味着你已经走到了最优解的候选位置。这就是为什么我们可以推导出 $w = \sum \alpha_i y_i x_i$。
## 2. 原始可行性 (Primal Feasibility)
$$y_i(w^T x_i + b) \ge 1$$ 这很简单：它要求你的解必须满足原本的规则。即所有数据点必须被正确分类，且在间隔（margin）之外。
## 3. 对偶可行性 (Dual Feasibility)
$$\alpha_i \ge 0$$ 拉格朗日乘子 $\alpha$ 必须是非负的。你可以把它理解为每个样本点对决策边界施加的“压力”。压力不能是负的。
## 4. 互补松弛性 (Complementary Slackness) —— 最重要的点
$$\alpha_i [y_i(w^T x_i + b) - 1] = 0$$ 
这个等式是 SVM 的灵魂。要让乘积为 0，只有两种可能：

* 情形 A：$\alpha_i = 0$
该点的“压力”为 0。这意味着这个点对 $w$ 的计算没有贡献。它通常是那些离边界很远的、被轻松分类的点。
* 情形 B：$y_i(w^T x_i + b) - 1 = 0$
这意味着该点刚好落在间隔边界上（即 $y_i(w^T x_i + b) = 1$）。

------------------------------
## 💡 为什么 KKT 条件对 SVM 如此重要？
它解释了什么是 支持向量 (Support Vectors)：
只有那些满足“情形 B”（落在边界上）的点，其 $\alpha_i$ 才可能大于 0。因为最终的 $w$ 是由 $\alpha_i$ 加权计算的，所以：

SVM 的决策边界仅由极少数落在边界上的点决定，其他所有点即使被删掉，模型也不会改变。

这就是为什么 SVM 非常高效且节省内存的原因。
