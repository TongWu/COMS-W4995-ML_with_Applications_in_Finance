# ML With Application In Finance

## 1 - Capital Allocation to Risky Assets

**风险资产的资本配置**

> 

### 1.1 - Real and Nominal Rates of Internet
- The nominal interest rate is the growth rate of your money
- The real interest rate is the growth rate of your PP (purchasing power)
  $$
  r_{real}=\frac {r_{nom}-i} {1+i} \\
  r_{real} \approx r_{nom} -i
  $$

  - $i$​ is the inflation rate
  - $r_{nom}$ = nominal interest rate
  - $r_{real}$ = real interest rate
- Which means that the growth rate of the money should higher than the inflation rate. In this case your purchasing power is increasing. 
  - 即，跑赢通胀

- We expect higher **nominal** interest rate when the inflation is higher.
- If $E(i)$ denotes for current expectations of inflation, the **Fisher Hypothesis** is:

$$
r_{nom}=r_{real}+E(i)
$$

> **Real interest rate：真实利率，考虑通货膨胀下，此利率是对购买力PPP的增长**
>
> **Nominal interest rate：名义利率，不考虑通胀，此利率仅代表货币的增长（即你账上的数字）**
>
> **在通胀的情况下，我们希望有高名义利率。如果$E_i$表示通胀的期望值，那么名义利率应该是比实际利率高的，因为名义利率包含了实际利率和对通胀的预期**

### 1.2 - Effective Annual Rate (EAR) and Annual Percentage Rate (APR)
- EAR explicitly account for compound interest.
- APR are annualized using simple rather than compound interest

> EAR（有效年利率）和APR（年百分率）都是衡量贷款成本的方式，但计算方式和包含的成本有所不同。
>
> EAR，也称为年化复利率或有效利率，是一种更为准确的利率计算方式。它考虑了贷款或投资的复利效应。这是因为它假设你会在一年的时间内将已获得的利息重新投资，从而产生更多的利息。所以，如果银行或金融机构经常计算利息（例如，每月或每天），EAR通常会高于表面上的名义利率。
>
> APR，也称为年百分比率或名义利率，是一个年度化的利率，它不包括复利的影响。它仅表示在不考虑复利的情况下，贷款的年度利息成本。APR通常被用于信用卡，汽车贷款，抵押贷款等贷款产品。在某些情况下，APR可能还包括一些非利息费用，例如贷款申请费或服务费。
>
> 因此，比较EAR和APR时，EAR通常会更高，因为它考虑了复利的影响。这也就意味着，如果你想要全面了解贷款的真实成本，你应该看EAR而不是APR。

EAR explicitly account for compound interest:
$$
1+\text{EAR} = (1+\frac {\text{APR}} n)^n
$$
APR are annualized using simple rather than compound interest.
$$
APR = n \times [(1+EAR)^{1/n}-1]
$$

> $n$代表复利次数。先将APR除以n是为了计算每一期的复利。即假设每一个季度复利一次，则n为4。

### 1.3 - Risk and Risk Premiums

#### **Holding Period Return (HPR)**

Investment risk is coming from:
1. Macroeconomic fluctuations 宏观调控
2. Changing fortunes of various industries 行业变化
3. Firm-specific unexpected development 特定公司的意外发展

- Holding period return is based on the price per share at year’s end and any cash dividends collected
  - 持有期的回报是基于年末的每股价格和收取的任何现金红利。

$$
HPR = \frac {\text{Ending price of a share - Beginning price + Cash dividend}} {\text{Beginning price}}
$$

#### **Expected Return and Standard Deviations**

- Expected returns:

- $$
  E(r) = \sum_s p(s)\times r(s)
  $$

  - $p(s)$: probability of each scenario
  - $r(s)$: HPR in each scenario
  - $s$: scenario

> Expected return (预期收益) 指投资者预期从一个投资项目中得到的收益。预期收益的计算是将可能结果的每一个收益率$$r(s)$$乘以相应的概率$p(s)$
>
> - 有20%的概率，收益率为-5%（亏损）
> - 有50%的概率，收益率为10%
> - 有30%的概率，收益率为20%
>
> 那么，预期收益就是： (-5% * 20%) + (10% * 50%) + (20% * 30%) = 1% + 5% + 6% = 12%

- Variance (VAR)

$$
\sigma^2 = \sum_s p(s)\times[r(s)-E(r)]
$$

- Standard Deviation (STD)

$$
STD = \sqrt {\sigma^2}
$$

#### Excess Returns and Risk Premiums

- Risk premium 风险溢价 is the difference between the expected HPR 持有期回报 and the **risk-free rate**
- **Risk-free rate** is the rate of interest that can be earned with certainty 肯定能赚取的利率（如短期国债 T-bills)
- The difference between actual rate of return and risk free rate is called **excess return**
- **Risk aversion** 风险厌恶/风险规避 dictates the degree to which investors are willing to commit funds to stocks

> - 风险溢价是投资者为承担额外的风险所要求（期望）的额外收益。投资者往往希望高风险高回报，这个额外的回报就是风险溢价
> - 风险溢价是期望收益与无风险利率之间的差值。无风险利率指违约风险几乎为零的投资，例如美国政府的短期国库债券。期望收益指投资者期望从风险中取得的额外回报
>   - 例如，如果一个投资的期望收益率是8%，而同期无风险利率是2%，那么风险溢价就是6%（即8%-2%）。这意味着投资者期望从这个投资中获得比无风险投资多6%的回报，以补偿承担的额外风险。
> - 风险厌恶（风险规避）是一种程度，其代表着人们（投资者）在面临风险选择时，更愿意选择风险较小或无风险的投资，即使这意味着可能获得的回报会更低。

#### Learning from historical returns

**Expected returns and the arithmetic average 预期回报和算术平均值**

- When using historical data, each observation is treated as an equally likely “scenario”
- Expected return $E(r)$ is estimated by arithmetic average of sample rates of return

$$
E(r) = \sum_s p(s)\times r(s) = \frac 1n \sum_{s=1}^n r(s)
$$

**Geometric (Time-weighted) average return 预期回报的几何平均值**

- Intuitive measure of performance over the sample period is the (fixed) annual HPR that would compound over the period to the same terminal value obtained from the sequence of actual returns in the time series.

$$
(1+g)^n = \text{Terminal value} \\
g = \text{Terminal value}^{1/n} - 1
$$

> - 算术平均收益率：算术平均收益率是所有年度收益的简单平均值。也就是将所有年度收益加起来，然后除以年份数。
> - 几何平均收益率：几何平均收益率是每年收益率的连乘积的n次方根（n为年份数），这个指标考虑了投资的复利效应。
>
> 在投资收益波动的情况下，几何平均收益率通常会小于算术平均收益率。这是因为几何平均收益率反映了收益的波动对投资的负面影响。如果投资收益稳定（无波动），则算术平均收益率和几何平均收益率会相等。

#### Risk and Risk Aversion

**Risky portfolios**

Investors are willing to consider:

- Risk-free assets
- Speculative positions 投机头寸 with positive risk premiums 即在承担风险时有正回报

Portfolio attractiveness: 投资组合吸引力

- Increases with expected return
- Decrease with risk

![image-20230606211423972](https://images.wu.engineer/images/2023/06/06/image-20230606211423972.png)

Each portfolio receives a **utility score** to assess 评估 the investor’s risk/return trade off

**Utility Function**

> Utility通常指的是某个选项或结果的主观满意度或价值。这是一个用来量化个体偏好的度量标准。
>
> 当谈到风险规避（Risk Aversion）时，人们通常会根据不同的结果分配不同的效用值（Utility Values）。例如，如果一个人对风险感到厌恶，他们可能会赋予确定性高的结果更高的效用值，即使那个结果的期望收益可能会较低。
>
> 举个例子，一个人可能更喜欢保证得到100美元（给这个结果较高的效用值），而不是有50%的机会得到200美元和50%的机会得到0美元，尽管这两种情况的期望收益是相同的。这就是因为他们是风险厌恶的，所以对确定性的结果赋予了更高的效用值。

$$
U = E(r) - \frac 12 A \sigma^2
$$

- U = Utility
- E(r) = Expected return on the asset or portfolio
- A = Coefficient of risk aversion
- $\sigma^2$ = Variance of returns
- $\frac 12$ = A scaling factor

![image-20230606211924569](https://images.wu.engineer/images/2023/06/06/image-20230606211924569.png)

**Investor Types**

- Risk averse investor 风险厌恶投资者者
  - $A \gt 0$
- Risk-Neutral Investors 风险中性投资者
  - $A=0$
- Risk lover 风险投资者
  - $A\lt 0$

**Risk-Return Tradeoff**

![image-20230606212652054](https://images.wu.engineer/images/2023/06/06/image-20230606212652054.png)

> "Risk and return tradeoff"是投资理论中的一个基本概念，它表明投资者在追求更高的收益时，必须接受更高的风险。
>
> 这个权衡的理念基于这样的观察：更高的收益的投资通常伴随着更高的风险。例如，股票投资可能提供比债券投资更高的预期收益，但它也带来了更大的价格波动和潜在损失的风险。换句话说，如果投资者想要获得更高的回报，他们就必须愿意承受更高的风险。
>
> 反之，如果投资者风险厌恶，他们可能会选择低风险的投资，如政府债券或定期存款。然而，这些投资的收益率通常较低。

**Estimating Risk Aversion**

Ways to estimate risk aversion:

1. Use questionnaires
2. Observe people’s decision when facing risk
3. Observer how much people are willing to pay to avoid risk

**Mean-Variance (M-V) Criterion 平均-方差标准**

- Only consider two elements: mean (expected return) and variance (risk)
  - Expected return calculated by arithmetic average
  - Risk calculated by STD or VAR of the return
- Portfolio X dominates portfolio Y if:
  - $E(r_x)\ge E(r_u)$, and
  - $\sigma_x \le \sigma_y$

**Indifference Curve**

![image-20230606213854244](https://images.wu.engineer/images/2023/06/06/image-20230606213854244.png)

> - 在indifference curve图中，横轴代表风险（$\sigma$），纵轴代表收益（预期回报$E(r)$）
> - 在曲线上，每一个点都具有相同的utility value
>   - 每个在indifference curve上的投资组合portfolio都对投资者具有相同的utility
> - 投资者对曲线上的任何一点都具有相同的偏好，他们对这些组合的选择是‘不确定的’
> - Indifference curve的形状取决于投资者的风险厌恶程度。
>   - 如果投资者更厌恶风险，那么他们的indifference curve会更加的陡峭，即对风险的增加要求更高的收益增加
>   - 如果投资者更能接受风险，那么他们的indifference curve会变得更平缓

### 1.4 - Capital Allocation Across Risky and Risk-Free Portfolios

The simplest way to control risk is to manipulate the ratio of risky assets to risk-free assets

**Risk-free Asset**

- Only the government can issue default-free securities 无违约风险债券
  - A security is a risk-free in real world only if:
    - Its price indexed
    - Maturity 到期期限 is equal to investor’s holding period
- T-bills 短期国库券 viewed as “the” risk-free asset
- Money market funds 货币市场基金 are also considered risk-free

> 证券在实际（即考虑了通货膨胀）上被视为无风险的条件。即，它的价格必须是指数化的，且它的到期期限必须等于投资者的持有期。
>
> 1. 价格指数化：指数化是指证券的价格或收益与某个指数（如消费者价格指数，CPI）挂钩，以便根据通胀率进行调整。这样，如果通胀率上升，证券的支付也会相应地增加，从而保护投资者的购买力不受通胀的侵蚀。例如，美国的通胀保护债券（TIPS）就是这样的一种证券，其利息和本金支付都与CPI挂钩。
> 2. 到期期限等于投资者的持有期：这是因为，如果证券的到期日期超过了投资者计划持有证券的时间，那么投资者就需要在证券到期前将其出售。然而，证券的市场价格可能会因为市场利率的变化而波动，这就产生了再投资风险和市场风险。另一方面，如果证券的到期日期早于投资者计划持有证券的时间，那么投资者在证券到期后需要再次投资，这也会面临再投资风险，即可能无法在同样的条件下再次投资。因此，为了避免这些风险，证券的到期期限应该刚好等于投资者的持有期。

**Example 1 for asset allocation**

y = Portion allocated to risky portfolio $P$

(1-y) = Portion to be invested in risk-free asset $F$

![image-20230606221801280](https://images.wu.engineer/images/2023/06/06/image-20230606221801280.png)

> 无风险资产的回报率为7%, 风险资产的预期回报为15%
>
> 无风险资产没有风险，风险资产的风险为22%

- Expected return

$$
E(r_c) = 7\times(1-y) + 15\times y = 7+y\times(15-7)
$$

- Risk

$$
\sigma_c = y\times \sigma_P = 22\times y
$$

- 将y的表达式更换为两个风险的百分比 $y = \frac {\sigma_c} {\sigma_P}$, 重写预期回报方程

$$
E(r_c) = 7+y\times(15-7) = r_f + \frac {\sigma_c} {\sigma_P} [E(r_P)-r_f]
$$

- Sharpe ratio: risk adjusted return

$$
\text{Sharpe ratio} = \frac {E(r_P)-r_f} {\sigma_P} = \frac 8 {22}
$$

> Sharpe比率测量的是投资者每承担一单位总风险，可以得到多少风险溢价。这个比率是投资收益的度量，对于风险的考虑使得我们可以比较不同风险等级的投资。
>
> Sharpe比率的计算公式为：
>
> （投资组合的预期收益率 - 无风险收益率）/ 投资组合的标准差
>
> 这里的标准差是投资组合收益率的波动性，被用作风险的度量。
>
> 在这个公式中，分子表示投资的超额回报（即投资的预期收益超过无风险收益的部分），分母表示投资的风险。因此，Sharpe比率提供了一个评价投资的风险调整后收益的方法。

### 1.5 - Investment Opportunity Set

> 投资机会集合（Investment Opportunity Set）是指投资者在特定时期内可用于投资的所有可能的投资组合。每个投资组合由不同的资产构成，如股票、债券、现金、商品等，这些资产的不同组合方式就形成了不同的投资机会。
>
> 这个概念有助于投资者根据他们的风险承受能力、投资目标和预期回报率来选择最佳的投资组合。例如，对于风险厌恶的投资者，他们可能会选择那些预期回报较稳定、风险较低的投资组合。而对于风险承受能力较高的投资者，他们可能会选择那些预期回报率较高、但风险也较高的投资组合。
>
> 投资机会集合的概念在现代投资组合理论中扮演了关键角色，这个理论帮助投资者理解如何最有效地分散风险并优化预期回报。

#### **Capital Allocation Line **CAL 资本配置线

> 资本配置线（Capital Allocation Line, CAL）是一个在现代投资组合理论中使用的概念，用于描述风险资产组合和无风险资产之间的投资组合的可能性。CAL显示了投资者可以通过在风险资产和无风险资产之间进行不同的投资配置而获得的预期收益和风险。
>
> 在一个标准的风险与收益图中，CAL是一条线，其纵轴表示预期收益，横轴表示风险（通常以标准差表示）。CAL的起点是无风险利率（因为这代表投资全部资金在无风险资产上的情况，没有风险，所以收益率是固定的），然后斜向上延伸到最优风险组合的点（也就是资本市场线上的切线点）。
>
> CAL的斜率代表了每单位风险所带来的超额收益，也被称为Sharpe比率。在给定的无风险利率下，投资者的目标是找到最大化Sharpe比率的风险资产组合，因为这代表了单位风险带来的最大超额收益。这个风险资产组合被称为切线组合或最优风险组合。
>
> 通过调整在无风险资产和风险资产组合之间的投资比例，投资者可以选择在CAL上的任何点，从而在风险和收益之间做出权衡。根据他们的风险偏好，一些投资者可能会选择更靠近无风险利率的点（低风险，低收益），而其他投资者可能会选择更靠近最优风险组合的点（高风险，高收益）。

![image-20230606222955469](https://images.wu.engineer/images/2023/06/06/image-20230606222955469.png)

#### Leveraged Capital Allocation Line LACL 有杠杆的资本配置线

> 有杠杆的资本配置线（Leveraged Capital Allocation Line，LCAL）是当投资者使用杠杆（即借款）来购买更多的风险资产时形成的资本配置线。
>
> 在有杠杆的情况下，投资者不仅可以使用自己的资金，还可以借用其他人的资金来购买风险资产。这样，他们可以购买超过自己原有资金量的风险资产，因此可能获得更高的预期收益，但同时也面临更大的风险。
>
> 在风险与收益图中，有杠杆的资本配置线的起点仍然是无风险利率，但它通过的点不再是无杠杆的最优风险组合，而是在这个点的右边，表示通过借款购买更多的风险资产。
>
> LCAL的斜率（即Sharpe比率）可能高于无杠杆的资本配置线，因为预期收益可能更高。然而，这也意味着风险更大，因为如果风险资产的价格下跌，投资者可能需要以更低的价格出售资产来偿还借款，从而可能导致资本损失。
>
> 因此，使用杠杆可以增加收益的潜力，但也增加了风险。投资者在使用杠杆时，需要谨慎考虑他们是否能承受可能的风险。

- Lend at $r_f = 7\%$ and borrow at $r_f = 9 \%$
  - Lending range slope = 8 / 22 = 0.36
  - Borrowing range slop = 6 / 22 = 0.27
  - CAL kinks at P

![image-20230606224152669](https://images.wu.engineer/images/2023/06/06/image-20230606224152669.png)

> "放贷的利率为7%，而借入资金的利率为9%" 这句话描述的是投资者面临的借贷利率不同。在金融市场中，投资者通常可以以一定的无风险利率（$r_f$）将资金存入银行或购买无风险证券（例如国库券），这种情况下，投资者是资金的提供者，他们是在放贷。
>
> 另一方面，如果投资者想要借款，例如使用杠杆来购买更多的风险资产，他们通常需要支付的利率会高于他们作为放贷方能得到的利率。这是因为借款存在违约风险，而且金融机构需要通过收取更高的利率来获得利润。
>
> 因此，在这个例子中，“Lend at $r_f = 7%$ and borrow at $r_f = 9 %$”指的是投资者将自己的资金放贷（例如存入银行或购买无风险证券）可以得到7%的利率，而如果他们想要借款（例如使用杠杆购买风险资产），他们需要支付9%的利率。
>
> 这种借贷利率的不对等会影响投资者在使用杠杆时的决策，因为他们需要评估借款的成本（即借款利率）和可能获得的额外收益之间的关系。如果可能的额外收益超过了借款的成本，那么使用杠杆可能是有利的。否则，投资者可能会选择不使用杠杆，而是将他们的资金放贷，或者直接投资于风险资产。

### 1.6 - Risk Tolerance and Asset Allocation

- The investor must choose one optimal portfolio $C$ from the set of feasible choices

  - Expected return of the complete portfolio:

  $$
  E(r_c) = r_f+y\times[E(r_P)-r_f]
  $$

  - Variance:

  $$
  \sigma_c^2 = y^2 \times \sigma_P^2
  $$

#### Calculate Utility

**Utility levels for various positions in risky assets**

![image-20230606225656391](https://images.wu.engineer/images/2023/06/06/image-20230606225656391.png)

![image-20230606225712045](https://images.wu.engineer/images/2023/06/06/image-20230606225712045.png)

**Utility as a Function of Allocation to the Risky Asset, y**
$$
Max_yU = r_f + y[E(r_P)-r_f]-\frac 12 Ay^2\sigma_P^2
$$

- To find max, take derivative w.r.t. y and set equal to 0

$$
[E(r_P)-r_f-\frac 12 Ay\sigma_P^2] = 0
$$

- Then solve for y:

$$
y^* = \frac {E(r_P)-r_f} {A\sigma_P^2}
$$

#### Calculate indifference curve

![image-20230606230114130](https://images.wu.engineer/images/2023/06/06/image-20230606230114130.png)

**Indifference curve for U=0.05 and U=0.09 with A=2 and A=4**

![image-20230606230156880](https://images.wu.engineer/images/2023/06/06/image-20230606230156880.png)

**Finding the optimal complete portfolio**

![image-20230606230301187](https://images.wu.engineer/images/2023/06/06/image-20230606230301187.png)

**Expected return on four indifference curves and the CAL**

![image-20230606230347163](https://images.wu.engineer/images/2023/06/06/image-20230606230347163.png)

> 最优投资组合是CAL与投资者的无差异曲线（indifference curve）相切的点。无差异曲线代表了投资者对风险和收益的偏好：沿着同一条无差异曲线的所有点，投资者的效用是相同的。无差异曲线的形状取决于投资者的风险厌恶程度：风险厌恶程度越高的投资者，其无差异曲线越弯曲。
>
> 关于最优投资组合的预期收益和方差的计算，我们需要知道投资者在无风险资产和风险资产之间的配置比例。设风险资产的预期收益为μ，无风险资产的预期收益为r_f，投资者在风险资产上的配置比例为w，那么最优投资组合的预期收益E[R_p]可以计算为：
>
> E[R_p] = w * μ + (1 - w) * r_f
>
> 而最优投资组合的方差Var(R_p)可以计算为：
>
> Var(R_p) = (w^2) * Var(R)

#### Non-Normal Returns 非正态回报

- Above analysis implicitly assumes normality
- VaR and ES* assess exposure to extreme losses
- “Black swan” events should concern investors

> 首先，我们需要理解在金融领域，许多理论和模型，包括现代投资组合理论和资本资产定价模型（CAPM），都基于假设资产回报服从正态分布（也称为高斯分布）。正态分布具有对称的钟形曲线，大部分观察值集中在平均值附近，极端值（正的或负的）的出现概率较小。
>
> 然而，在现实中，资产回报常常表现出**非正态的特征**，比如倾斜（skewness，即分布的不对称性）和厚尾（kurtosis，即尾部比正态分布更“厚”、即出现极端值的概率更大）。这就是“非正态回报”。
>
> “VaR”（Value at Risk）和“ES”（Expected Shortfall，也被称为条件VaR或CVaR）是两种**风险度量方法**，用于评估在极端情况下可能遭受的损失。VaR表示在给定的置信水平和时间范围内，投资组合可能出现的最大预期损失。ES则进一步考虑了损失超过VaR值时的预期损失。这两种方法都专门用于处理非正态分布下的风险，尤其是极端损失的风险。
>
> “黑天鹅”事件（Black Swan events）是由Nassim Nicholas Taleb提出的概念，用于描述那些**出乎意料、影响巨大且在发生后才能合理解释的事件**。这些事件在正态分布假设下几乎不可能发生，但在现实中却有可能出现，因此它们是投资者需要关注的风险。
>
> 所以，当这段文本说“以上分析隐含地假设了正态性，但VaR和ES评估了对极端损失的暴露，‘黑天鹅’事件应该引起投资者的关注”，它的含义是，虽然许多金融理论和模型基于资产回报服从正态分布的假设，但在实际应用中，投资者需要考虑到资产回报可能表现出非正态特性，特别是极端损失的风险。这就是VaR、ES和关注“黑天鹅”事件的重要性。

#### Passive Strategies

- The passive strategy avoids security analysis
- Supply/demand forces may make this strategy reasonable for many investors
- A natural candidate for a passively held risky asset would be the S&P 500
- The Capital Market Line (CML) is a capital allocation line formed investment in two passive portfolios:
  1. Virtually risk-free short term T-bills (or a money market fund)
  2. Fund of common stocks that mimics a broad market index

> 被动投资策略是一种投资方法，投资者根据某种基准（通常是市场指数，如S&P 500）配置他们的投资组合，而不是尝试通过证券分析来选出可能表现优异的个别股票或其他资产。这种策略的优点在于，它避免了对个别证券进行深入分析的需要，从而降低了管理费用和交易成本。
>
> 这种策略有可能对许多投资者是合理的，原因是市场供需力量通常会推动资产价格向其公允值靠近。在这种情况下，尝试通过证券分析来找出被低估或高估的股票可能是困难的，而且可能不值得所需的额外成本和努力。
>
> S&P 500指数是一个常见的被动投资策略的目标。这是一个包含了美国500家大型上市公司的股票市值加权指数，代表了美国股市的广泛性和多样性。通过投资一个追踪S&P 500指数的指数基金或交易所交易基金（ETF），投资者可以获得与这个指数相匹配的回报，同时避免了选股的需求。
>
> 资本市场线（Capital Market Line, CML）是投资者在两个被动投资组合之间进行配置时形成的资本配置线。这两个被动投资组合是：几乎无风险的短期国库券（或货币市场基金）和一个模仿广泛市场指数的股票基金。在这种情况下，投资者可以根据他们的风险厌恶程度在这两个组合之间进行配置，而无需进行个别证券的分析。


## 2. Introduction to Credit Risk

### 2.1 - Introduction
- Credit Risk is defined as a risk of financial loss due to counterparty’s inability to meet obligations 义务.
- Also can be defined as the risk that a debater will be unable to meet its obligations towards its creditors.

> 信用风险（违约风险default risk）是指借款方或对方在合约规定的时间内无法按照约定履行还款义务，导致债权方财物损失的风险。

**Why speak of credit risk?**

- Credit risk is the major cause for **serious banking problems.**
	- Lax credit standard for borrowers and counterparties.
	- Poor portfolio risk management
	- Lack of attention to changes in economic or other circumstances
- Innovations in the financial markets like complicated sales contracts and derivatives contracts create credit risk.
- National and global expansion by businesses has given rise to credits emerging from ties with new governments and new clients.
> - 信用风险是造成严重银行问题的主要原因。
>
>   - 对借款人和交易方的信用标准不严。
>
>   - 投资组合风险管理不善
>
>   - 对经济或其他情况的变化缺乏关注
>
> - 金融市场的创新，如复杂的销售合同和衍生品合同，造成了信用风险。
>
> - 企业在国内和全球的扩张引起了与新政府和新客户的联系而出现的信贷。

### 2.2 - Credit Losses
Credit losses: potential amount at loss if the counterpart defaults 违约.

Distribution of these losses can be viewed as a compound process driven by the following three varibles:

- Probability of default: likehood that the counterparty will default on its obligation either over the life of the obligation or over some specificed horizon, such as a year. Calculated for a one-year horizon, this may be called the expected default frequency.
- Credit exposure, which is the economic value of the claim on the counterparty at the time of default.
- Loss given default (LGD), which represents the fractional loss due to default:

$$
LGD = 1-RR
$$

- RR: recovery rate. The fraction of the exposure may be recovered through bankruptcy proceedings or some other form of settlement.

> 信用损失：当债务人违约时，债权人可能遭受的损失。
>
> 信用损失的分布可以由以下三个变量组成：
>
> - 违约概率：债务人在债务期限内，或在某个特定的期限内（如一年）违约的可能性。如果这个概率是为一年期限计算的，那么他被称为**预期违约概率**。
> - 信用敞口：债务人在违约时，债权人对债务人的经济价值索赔。通俗的说，如果债务人违约，债权人在得到索赔之后还可能会损失多少被称为信用敞口。信用敞口更多地是关注在债务人违约时，债权人可能会遭受的总体经济损失，包括未偿还的本金、未支付的利息以及可能的市场价值损失。
> - 违约损失(LGD)：表示由于违约而导致的损失比例。可以通过公式‘LGD=1-RR’计算。RR是恢复率，表示通过破产程序或其他形式的和解可能恢复的债券比例。

> 恢复率(RR)指在债务人违约之后，债权人能够从债务人那里收回的债务金额占原始债务金额的比例。恢复率度量的是债权人在债务人违约后能够收回多少债权。
>
> 而信用敞口则是指在任何特定时间点，债权人可能由于债务人违约而面临的潜在经济损失，包含未偿还的本金，利息和可能的市场价值损失。它反映的是债权人在债务人违约时可能会损失的资金。

For an instrument, the credit loss is:
$$
\text{Credict Loss} = b \times \text{Credict Exposure} \times LGD \\
$$
$b$ is a Bernoulli random variable that takes the value of 1 if default occurs and 0 otherwise, with probability $p$

For a portfolio of $N$ counterparties, the loss is:
$$
\text{Credict Loss} = \sum_{i=1}^N b_i \times CE_i \times LGD_i \\
$$

### Distribution of Credit Loss

![image-20230607222337774](https://images.wu.engineer/images/2023/06/07/image-20230607222337774.png)

Highly skewed to the left and is fat tailed, i.e., there is a large probability of small losses and a small probability of large losses.

> 信用损失的分布（Distribution of Credit Loss）是一个统计模型，用于描述和预测债务人违约导致的信用损失的可能范围和概率。
>
> 信用损失的分布是由三个主要因素决定的：
>
> 1. **违约概率**（Probability of Default，PD）：这是债务人在特定时期内违约的概率。
> 2. **损失违约率**（Loss Given Default，LGD）：如果债务人违约，债权人将损失的债务的比例。LGD通常用 `1 - RR` 表示，其中 RR 是恢复率，表示债务人违约后，债权人通过法律程序或其他形式的和解能够收回的债务的比例。
> 3. **信用敞口**（Exposure at Default，EAD）：这是债务人在违约时，债权人可能面临的潜在经济损失。
>
> 这三个因素共同决定了信用损失的分布，也就是说，它们决定了债权人可能遭受的信用损失的范围和概率。通过研究和模拟信用损失的分布，债权人（如银行和其他金融机构）可以更好地评估和管理自己的信用风险。

> 信用损失分布图（Credit Loss Distribution）通常会在一个图表上展示，横轴表示信用损失的数量或比例，纵轴表示这些损失发生的概率或频率。
>
> 这样的分布通常是一个非对称的图形，因为信用损失通常有一个下限（即没有损失，也就是0），但上限可能是非常大的（如果所有债务人都违约，那么损失就可能等于所有债权的总额）。因此，信用损失分布图可能会向右倾斜，表示较大的损失虽然可能性不大，但还是有可能发生。
>
> 在具体的形状上，信用损失分布图可能会受到很多因素的影响，包括违约概率的分布、信用敞口的大小、损失违约率等等。不同的债权组合可能会有不同的信用损失分布，这就需要具体的数据和模型来分析。

### Unexpected credit loss (UCL)

The unexpected credit loss represents the loss that will not be exceeded at some level of confidence

- It is the deviation from the expected loss
- Economic capital should cover the unexpected credit loss

$$
UCL = CL_{99\%}-ECL
$$

$CL_{99\%}$: portfolio’s 99% VAR quantile

Marginal Contribution to risk: The distribution of credit losses can also be used to analyze the incremental effect of a proposed trade on the total portfolio risk

For the same expected return, a trade that lowers risk should be preferable over one that adds to the portfolio risk

> 在信用风险管理中，信用损失通常分为两种：预期信用损失（Expected Credit Loss，ECL）和非预期信用损失（Unexpected Credit Loss，UCL）。
>
> 预期信用损失是基于债务人违约概率（PD）、损失违约率（LGD）和信用敞口（EAD）计算出的信用损失的平均值或预期值。换句话说，预期信用损失是在正常情况下，根据债权人的信用风险模型预计可能会发生的信用损失。
>
> 然而，实际的信用损失可能会高于或低于这个预期值，这就是非预期信用损失。非预期信用损失可以看作是信用损失的不确定性或波动性，它反映了信用损失可能偏离预期值的程度。一般来说，如果债权人的信用风险管理较好，那么非预期信用损失应该会较小；反之，如果信用风险管理不佳，那么非预期信用损失可能会较大。

> 非预期信用损失代表了在某一置信水平下不会超过的损失。换言之，UCL反映的是信用损失的不确定性或可能偏离预期的程度。
>
> 置信水平（Confidence Level）是统计学中的一个概念，通常用于描述统计估计的不确定性。
>
> 具体来说，如果我们说一个统计估计具有95%的置信水平，那么这意味着如果我们无限次地重复相同的研究，并且每次都计算一个新的估计值，那么预期有95%的估计值会包含在我们指定的置信区间（Confidence Interval）内。
>
> 举例来说，如果我们基于样本数据计算了一个平均值，并且报告说这个平均值的95%置信区间是（10,20），那么这意味着如果我们无限次地重复这个研究，并且每次都计算一个新的平均值，那么预期有95%的平均值会在10到20之间。
>
> 同样的，在金融风险管理中，我们经常会看到99%的置信水平。例如，如果我们说一个投资组合的99%的值风险（Value-at-Risk，VaR）是1百万美元，那么这意味着在99%的情况下，投资组合的损失不会超过1百万美元。这个99%就是置信水平，表示我们对这个估计的信心程度。
>
> **所以，非预期信用损失指的是超出了置信水平时的信用损失。**
>
> “$$CL_{99\%}$$”表示信用损失在99%置信水平下的值，也就是说，有99%的概率，实际的信用损失不会超过这个值。这个值也常被称为信用损失的99%的值风险（Value-at-Risk，VaR）分位数。如果我们从这个值中减去预期信用损失（Expected Credit Loss，ECL），我们就得到了非预期信用损失。
>
> 经济资本应当足以覆盖非预期信用损失。在金融风险管理中，经济资本是一种资本，目的是为了吸收可能发生的未预期损失，这就包括了信用损失的非预期部分。
>
> 最后，这段话还提到了边际风险贡献（Marginal Contribution to Risk）的概念。这是一种分析工具，用于评估一个新的交易可能对整个投资组合风险的影响。如果一个交易可以在预期回报不变的情况下降低投资组合的风险，那么这个交易就应当优于增加风险的交易。这是一种基于风险-收益权衡（trade-off between risk and return）的投资策略。

### Short and long position

在股票交易市场中，"long position"（多头头寸）和"short position"（空头头寸）是两个基本概念，它们描述了投资者对股票未来价格走向的预期。

1. Long Position（多头头寸）：当一个投资者买入一支股票并持有，他被认为持有该股票的多头头寸。持有多头头寸的投资者预期股票的价格会上涨，以便在未来以更高的价格卖出股票，从而获得利润。

2. Short Position（空头头寸）：当一个投资者预期一支股票的价格会下跌时，他可能会选择建立空头头寸。空头操作包括借入股票并立即将其卖出，然后等待股票价格下跌后再买回股票，归还给原借方，并从中获得利润。这是一个更为复杂且风险较高的策略，因为如果股票价格反而上涨，投资者可能需要以高于他卖出价格的价格买回股票，这将导致损失。

简而言之，多头头寸是投资者买入股票，预期价格上涨，而空头头寸是投资者借入并卖出股票，预期价格下跌。

## 3 - Markowitz Model

### 3.1 - Investment Decision

- The investment decision is a top-down process

  1. Capital allocation (risky versus risk-free)

  2. Asset allocation

  3. Security allocation

- Optimal risky portfolio construction 最佳的风险投资组合构建

- Efficient diversification 高效的多元化经营

- Long-term vs. short-term investment horizons 长期与短期的投资视野

> 投资决定是一个自顶向下的过程：
>
> 1. 首先确定资本的分配(capital allocation)。这是投资组合管理中最基础的层面，涉及到风险资产和无风险资产之间的分配。这种决策取决于投资者的风险承受能力和投资目标。例如，一个保守的投资者可能会将大部分资金投资在无风险资产（例如，政府债券）上，而只将少部分资金投资在风险资产（例如，股票）上。反之，一个愿意接受更高风险以获取更高回报的投资者可能会将更多资金投资在风险资产上。
> 2. 其次是资产分配(asset allocation)。在确定了风险资产和无风险资产的比例之后，投资者需要进一步决定如何在各种风险资产之间进行分配。这涉及到各种不同类型的风险资产，如股票、债券、商品、房地产等。资产分配的决策通常基于投资者对未来市场表现的预测，以及对风险和回报之间权衡的理解。
> 3. 最后是证券分配(security allocation)。在确定了各类资产的比例之后，投资者需要进一步决定在每一类资产内部，各种具体证券的比例。例如，在决定投资股票之后，投资者还需要决定具体投资哪些公司的股票，以及各公司股票的比例。证券分配的决策通常基于对各公司财务状况、业务前景、市场定价等因素的研究和评估。
>
> 总的来说，投资者需要先确定在风险资产和无风险资产上面的投资比例，然后再确定风险资产中投资哪几个类型的资产。最后，再对投资的风险资产进行细分，例如投资哪种股票，期货，债券。

### 3.2 - Portfolio diversification and risk

#### Portfolio risk type

- Market risk
  - Attributable to market-wide risk sources
  - Remains even after diversification
  - Also called **systematic** or **non-diversifiable risk**
- Firm-specific risk
  - risk that can be eliminated by diversification
  - also called diversifiable or non-systematic risk

> 投资组合的风险可以分为两个类别：市场风险和公司特定风险
>
> - 市场风险(Market risk)又可以称为系统性风险（不同于经济学上的系统性风险）或不可分散风险，是由全球或全市场的风险源引起的。这类风险包括如经济周期，政策利率，通货膨胀，政治不稳定等。这类风险会影响到**所有的投资者**和**所有的资产类型**（仅对风险资产）。因此不能透过分散投资来消除。例如，如果全球经济进入衰退，那么所有的股票可能都会受到影响，因此，投资者不能通过在多个股票之间分散投资来避免这种风险。
> - 公司特定风险(Firm-specific risk)又可以称为非系统性风险或可分散风险，是由特定公司或者行业的特定情况引起的风险。这类风险可以透过分散投资来减少或消除。例如，如果一个公司的CEO突然辞职，那么这可能会对该公司的股票价格产生负面影响，但是这不太可能影响到其他公司。因此，如果投资者在多个公司的股票之间分散投资，那么他们就可以降低这种风险。

![image-20230609203006836](https://images.wu.engineer/images/2023/06/09/image-20230609203006836.png)

- In panel A, all risk is firm-specific. In this case, with the number of stock in the portfolio $n$ increasing, the risk $\sigma$ decrease.
- In panel B, there is market risk and firm-specific risk. The market risk effects all stocks, so it directly increase all risk in terms of the number of stock.

**Portfolio diversification**

![image-20230609203341229](https://images.wu.engineer/images/2023/06/09/image-20230609203341229.png)

> 投资组合多样化（Portfolio Diversification）是一种风险管理策略，其主要思想是在多个不同的投资项目之间分散投资，以减少单一投资所带来的风险。
>
> 多样化的概念建立在一个基本的统计原理之上，即不完全相关的资产组合会有较低的总风险。也就是说，如果你的投资组合中包含的资产彼此之间的价格变动没有强烈的相关性，那么一个资产价格下跌不一定导致其他资产的价格也下跌，这样可以减少整体风险。
>
> 在实践中，投资者通常通过在多个不同的资产类别（如股票、债券、商品等）、不同的地理区域（如不同的国家或地区）、不同的行业或公司之间分散投资来实现投资组合多样化。通过这种方式，投资者可以降低公司特定风险或行业特定风险，也就是可以降低非系统性风险。

### 3.3 - Portifolio of two risky assets

- Expected return
  - Weighted average of expected returns on the component securities
- Portfolio risk
  - Variance of the portfolio is a weighted sum of covariances, and each weight is the product of the portfolio proportions of the pair of assets

> - 预期回报：预期回报是指组成投资组合的每个资产的预期回报与其在投资组合中的权重的加权平均数。例如，如果资产A的预期回报是10%，资产B的预期回报是15%，并且在投资组合中，资产A的权重为50%，资产B的权重为50%，那么投资组合的预期回报就是（10% * 50%）+ (15% * 50%) = 12.5%。
> - 投资组合风险：投资组合的风险是由组成投资组合的资产的风险共同决定的，具体来说，是由他们的协方差和各自在投资组合中的权重决定的。协方差是一个衡量两个随机变量（在这里是资产回报）联动性的度量，如果两个资产的回报趋势相似，那么他们的协方差就会大；反之，如果两个资产的回报趋势不同，他们的协方差就会小。投资组合的方差（即风险）是协方差的加权求和，其中每个权重是由投资组合中各对资产的权重之积得到的。
>
> 这就是为什么我们说投资组合的风险并不是组成投资组合的各个资产风险的简单加和，而是由它们的协方差决定的。这也是投资组合多样化能够降低风险的原因，即通过合理选择彼此回报不完全正相关的资产，可以降低投资组合的整体风险。

#### **Expected return**

- Consider a portfolio made up of equity (stocks) and debt (bonds)…

$$
r_p = w_D r_D + w_E r_E
$$

- $r_p$ = rate of return on portfolio
  - $w_D$ = proportion invested in the bond fund
  - $w_E$ = proportion invested in the stock fund
  - $r_D$ = rate of return on the bond fund
  - $r_E$ = rate of return on the stock fund

$$
E(r_p) = w_D E(r_D) + w_E E(r_E)
$$

#### **Portfolio risk**

- Variance of $r_p$

$$
\sigma_p^2 = w_D^2\sigma_D^2 + w_E^2\sigma_E^2+2w_Dw_ECov(r_D,r_E)
$$

- $\sigma_D^2$ = bond variance
- $\sigma_E^2$ = equity variance
- $Cov(r_D,r_E)$ = covariance of returns for bond and equity

#### **Covariance**

- Covariance of returns on bond and equity

$$
Cov(r_D,r_E) = \rho_{DE}\sigma_D\sigma_E
$$

- $\rho_{DE}$ = correlation coefficient of returns
- $\sigma_D$ = standard deviation of bond returns
- $\sigma_E$ = standard deviation of equity returns

#### **Correlation Coefficients**

- Range of values for correlation coefficient
  $$
  -1.0 \le \rho \le 1.0
  $$

  - if $\rho = 1.0$, means perfectly positively correlated securities

  - if $\rho = 0$, means securities are uncorrelated

  - if $\rho = -1.0$, means perfectly negatively correlated securities

- When $\rho_{DE}=1$, there is no diversification
  $$
  \sigma_P = w_E\sigma_E+w_D\sigma_D
  $$

- When $\rho_{DE}=-1$, a perfect hedge is possible
  $$
  w_E = \frac {\sigma_D} {\sigma_D+\sigma_E} = 1-w_D
  $$

#### Case: 50%/50% split

![image-20230609205034094](https://images.wu.engineer/images/2023/06/09/image-20230609205034094.png)

- Expected return:

$$
\begin{aligned}
E(r_p) &= w_D E(r_D) + w_E E(r_E) \\
&= 50\% \times 8\% + 50\%\times13\% \\
&= 10.5\%
\end{aligned}
$$

- Variance

$$
\begin{aligned}
\sigma_p^2 &= w_D^2\sigma_D^2 + w_E^2\sigma_E^2+2w_Dw_ECov(r_D,r_E) \\
&= 50\%^2 \times 12\%^2 + 50\%^2\times20\%^2 + 2\times0.5\times0.5\times72 \\
\sigma_p&= 13.23\%
\end{aligned}
$$

**Graph: portfolio expected return**

![image-20230609205634081](https://images.wu.engineer/images/2023/06/09/image-20230609205634081.png)

> 这幅图是上面的表格的图像化。横轴是股票的占比，纵轴是预期回报率。当股票的占比是0时，意味着100%的资产为存款，此时的预期回报是8%。随着股票的占比逐渐增加，预期回报也会逐渐增加，直到100%的资产用于投资股票时，预期回报为13%。

**Computation of portfolio variance from the covariance matrix**

![image-20230609210121721](https://images.wu.engineer/images/2023/06/09/image-20230609210121721.png)

**Portfolio standard deviation vs. Weight**

![image-20230609211839904](https://images.wu.engineer/images/2023/06/09/image-20230609211839904.png)

> 总结一下$\rho$值的关系：
>
> - $\rho = 1$，表明两种资产呈正相关。这意味着它们的价格运动方向相同，整个投资组合的风险将随着某个资产的占比增加而增加。因为当其中一种资产价格下跌时，另一种资产价格也会下跌，投资组合的价值也会相应下跌。
> - $\rho=0$，表明两种资产没有明显的关联性，这意味着它们的价格运动彼此独立，整个投资组合的风险取决于每种资产的标准差。此时，一个资产的占比对整个组合的风险没有影响。
> - $\rho = -1$，表明两种资产正相关，这意味着当一种资产的价格上涨时，另一种资产的价格下跌，它们相互抵消，整个投资组合的风险可以降低。因此，当一个资产的占比增加时，整个组合的风险将会下降。
>
> 现在我们可以理解上面这幅图的含义：
>
> - 当$\rho = 1$时，两种资产呈正相关。所以在一种资产的占比增加时，风险（标准差）会没有干扰的持续增加。
> - 当$\rho$逐渐下降时，两种资产的关联度开始降低，这意味着另一种资产可以逐渐起到抵消风险的作用，所以线会逐渐弯曲。风险的最低点会在50%左右，但这并不是绝对的。
> - 当$\rho=-1$时，风险抵消呈现最大值，即在50%左右时出现风险完全抵消的情况。

#### Portfolio expected return vs. standard deviation (risk)

![image-20230609212816671](https://images.wu.engineer/images/2023/06/09/image-20230609212816671.png)

#### The minimum-variance portfolio

- The minimum-variance portfolio has a standard deviation smaller than that of either of the individual component assets
- Risk reduction depends on the correlation
  - if $\rho = 1$, no risk reduction is possible
  - if $\rho=0$, $\sigma_P$ may be less than the standard deviation of either component asset
  - if $\rho=-1$, a riskless hedge is possible

#### The oppounity set of the debt and equity funds and two feasible CALs

![image-20230609222124422](https://images.wu.engineer/images/2023/06/09/image-20230609222124422.png)

> 现在，我们把上一个部分求得的曲线放在两个资产组合的CAL中，CAL为资本配置曲线(Capital allocation line)。
>
> 对于两个资产组合A和B，其最佳的投资点为点A和B，因为他们在拥有最低风险的同时有着最大的预期回报率。
>
> 然而A和B都是最佳点，只不过是对于两个投资组合来说。此时我们应该如何判断具体选择哪一个投资组合呢？这里需要sharpe ratio

#### Sharpe ratio

- Objective is to find the weight $w_D$ and $w_E$ that result in the highest slope of the CAL
- Thus, our objective function is the Sharpe ratio:

$$
S_p = \frac {E(r_p)-r_f} {\sigma_p}
$$

> sharpe ratio计算的是风险溢价对于风险的比率。
>
> revision：
>
> - $E(r_p)$为预期回报率，不同于$r_p$回报率，预期回报率是回报率加上风险溢价。所以此处预期回报率减去回报率即为风险溢价。
>
> sharpe ratio越高，代表着风险能够带来更高的收益。

![image-20230609222811460](C:/Users/TedWu/AppData/Roaming/Typora/typora-user-images/image-20230609222811460.png)

#### Debt and Equity Funds with the Optimal Risky Portfolio

![image-20230610004126582](https://images.wu.engineer/images/2023/06/10/image-20230610004126582.png)

> 对于一个最佳的投资组合，其应该与先前计算出来的oppounity set of risky assets曲线相切，其切点即为最佳的投资点P

#### Determination of the optimal complete portfolio

![image-20230610004720627](https://images.wu.engineer/images/2023/06/10/image-20230610004720627.png)

> 对于最终选择，我们将无差异曲线加入到模型中，无差异曲线微调了最终的投资位置。最终点C为最终决定。

![image-20230610004821526](https://images.wu.engineer/images/2023/06/10/image-20230610004821526.png)

### 3.4 - Markowitz Portfolio Optimization Model

- Security selection
  - Determine the risk-return opporunities avaliable
    - Minimum-variance frontier of risky assets
  - All portfolios that lie on the minimum-variance frontier from the global minimum-variance portfolio and upward provide the best risk-return combinations
    - Efficient frontier of risky assets is the portion of the frontier that lies above the global minimum-variance portfolio.

> 马科维茨投资组合优化模型(Markowitz Portfolio Optimization Model)是一种在理论上用来找到给定预期收益率下风险最小的投资组合的方法。
>
> - **安全选择**：这一步是确定可用的风险-收益机会，即各种可能的投资组合。这些组合构成了被称为"最小方差前沿"的集合，即对于每一种可能的预期收益率，最小方差前沿上的投资组合具有最低的风险（方差）。
> - **最小方差前沿**：最小方差前沿上的投资组合提供了最佳的风险-收益组合。它们的风险最小，即方差最小。"全球最小方差组合"是风险（方差）最小的投资组合，不考虑收益率。
> - **有效前沿**：有效前沿是最小方差前沿上位于全球最小方差组合以上部分的投资组合集合。这些投资组合不仅风险最小，而且预期收益率高于或等于全球最小方差组合的预期收益率。有效前沿的概念是在风险和收益之间进行权衡的基础，理论上，投资者应该选择有效前沿上的投资组合，因为这些投资组合在给定风险水平下提供了最高的预期收益，或者在给定预期收益水平下提供了最低的风险。

#### Minimum-Variance Frontier 最小方差前沿

![image-20230610010329054](https://images.wu.engineer/images/2023/06/10/image-20230610010329054.png)

> 最小方差前沿（Minimum Variance Frontier）是马科维茨投资组合理论中的一个关键概念。该理论通过优化组合，寻找到在给定预期收益率下，风险（通常以方差或标准差度量）最小的投资组合。
>
> 最小方差前沿代表了在不同的预期收益率水平下，风险最小的投资组合。简单来说，你可以将其视为一个地图：在这个地图上，每一点都代表一个可能的投资组合，而最小方差前沿就是这些点中风险最小的那些点所形成的一条线或曲线。
>
> 在这个前沿上，任何一个点都代表一个特定的投资组合，该投资组合的特性是，在所有预期收益相同的投资组合中，它具有最小的风险。
>
> 最小方差前沿的上半部分通常被称为"有效前沿"（Efficient Frontier），有效前沿的投资组合不仅风险最小，而且预期收益也相对较高。理论上，理性的投资者会选择有效前沿上的投资组合，因为这些投资组合在给定的风险水平下能提供最大的预期收益，或者在给定的预期收益水平下具有最小的风险。

> "全局最小方差组合"（Global Minimum-Variance Portfolio）是指在所有可能的投资组合中，风险（以方差或标准差衡量）最小的投资组合。在马科维茨的投资组合理论中，这个组合被视为最小方差前沿的起点。
>
> 这个组合的关键特性是，它的风险最小，不论预期收益率如何。然而，正因为如此，这个组合的预期收益也可能不是最高的。因此，虽然这个组合的风险最小，但并不一定是所有投资者的最佳选择，特别是对那些愿意承担更多风险以获取更高收益的投资者来说。

- Security selection (continued)
  - Search for the CAL with the highest Shape ratio (that is, the steepest slope 最陡的线)
  - Individual investor chooses the appropriate mix between the optimal risky portfolio point $P$ and T-bills
  - Everyone invests in $P$, regradless of their degree of risk aversion
    - More risk averse investors put less in P 风险厌恶程度越高的投资者对 P 的投入就越少
    - Less risk averse investors put more in P

![image-20230610010935501](https://images.wu.engineer/images/2023/06/10/image-20230610010935501.png)

- Capital allocation and the separation property
  - Portfolio choice problem may be separated into two independent tasks:
    1. Determination of the optimal risky portfolio is purely technical
    2. Allocation of the complete portfolio to risk-free versus the risky portfolio depends on personal preference

> 分离性质是现代投资组合理论的一个重要组成部分，由詹姆斯·托宾（James Tobin）在1958年提出。这个理论表明，投资决策可以分解为两个独立的步骤：
>
> 1. 确定最佳风险投资组合：这是一个技术问题，涉及的是如何选择并配置风险资产，以达到最大化预期收益与风险的平衡。这一步骤通常需要对资产收益率的预测，以及对资产之间相互关系的理解。
> 2. 确定风险投资组合与无风险资产的配置比例：这是一个与个人风险承受能力和预期收益目标相关的决策。这一步骤通常需要投资者根据自己的风险厌恶程度，确定将多少资金投资于风险投资组合，以及多少资金投资于无风险资产。

![image-20230610011222721](https://images.wu.engineer/images/2023/06/10/image-20230610011222721.png)

> 如果投资者对风险非常厌恶，那么他们可能会倾向于选择全球最小方差投资组合，因为这个投资组合在所有可能的投资组合中具有最小的风险（即，最小的方差）。
>
> 然而，如果投资者愿意接受一些风险以获取更高的预期回报，那么他们可能会选择CAL和有效前沿的交点的投资组合。这个投资组合被认为是在给定的风险水平下能够提供最高预期回报的投资组合。

- The power of diversification

  - Recall: 

  $$
  \sigma^2_p = \sum_{i=1}^n\sum_{j=1}^n w_iw_jCov(r_i,r_j)
  $$

  - Assume we define the average variance and average covariance of the securities as:

  $$
  \sigma^2=\frac1n \sum_{i=1}^n\sigma^2_i \\
  Cov = \frac 1 {n(n-1)} \sum_{j=1}^n\sum_{i=1}^n Cov(r_i,r_j)
  $$

  - We cam then express portfolio variance as:

  $$
  \sigma^2_p = \frac1n \overline \sigma^2 + \frac {n-1}n Cov
  $$

  - Portfolio variance can be driven to zero if the average covariance is zero
  - The risk of a highly diversified portfolio depends on the covariance of the returns of the component securities.

> 回顾投资组合的方差公式，这个公式基于每种资产的权重（$w_i$），以及资产回报之间的协方差（$Cov(r_i, r_j)$）。这个公式表明，投资组合的整体风险（以方差表示）不仅取决于各个资产的风险，还取决于各个资产之间的相关性。
>
> 定义了平均方差（$\sigma^2$）和平均协方差（$Cov$）。平均方差是所有资产的方差的平均值，而平均协方差是所有资产对之间的协方差的平均值。
>
> 通过平均方差和平均协方差，将投资组合的方差表达成了一个更直观的形式：$\sigma^2_p = \frac1n \overline \sigma^2 + \frac {n-1}n Cov$。**这个公式表明，随着投资组合中的资产数量（$n$）的增加，投资组合的风险会降低，**这就是分散化的好处。
>
> 如果所有资产之间的平均协方差为零，那么投资组合的风险可以被完全消除。换句话说，如果所有资产的回报都完全不相关，那么通过充分分散化，我们可以将投资组合的风险降至最低。但实际上，市场中的资产回报往往具有一定的相关性，所以我们无法完全消除投资组合的风险，但通过分散化，我们可以显著降低这种风险。

![image-20230610172820849](https://images.wu.engineer/images/2023/06/10/image-20230610172820849.png)

- Optimal portfolio and non-normal returns
  - Fat-tailed distribution can result in extreme values of VaR and ES
    - Practice way to estimate values of VaR and ES in the presence of fat tails is called bootstrapping
  - If other portfolios provide sufficiently better VaR and ES values than the mean-variance efficient portfolio, we may prefer these when faced with fat-tailed distributions

> “胖尾”分布可以导致风险价值（VaR）和预期损失（ES）的极端值。这是因为胖尾分布比正态分布有更高的概率产生极端的大值或小值。这种情况下，通过计算均值和方差（或标准差）并不能充分地描述资产或投资组合的风险。
>
> 然后，介绍了一种实际的方法来估计在胖尾分布情况下的VaR和ES值，这种方法叫做自助法（Bootstrapping）。自助法是一种从原始数据中生成新的样本集的重采样方法，用于估计一个统计量的抽样分布。在这种情况下，自助法可以用于生成大量可能的资产回报率，从而更好地估计VaR和ES。
>
> 最后，如果其他投资组合的VaR和ES值比均值-方差有效的投资组合要好，那么在面对胖尾分布时，我们可能会更倾向于选择这些投资组合。这是因为，在非正态分布（尤其是胖尾分布）下，均值-方差优化可能无法充分地捕捉风险，所以我们可能需要考虑其他的风险度量（如VaR和ES）来选择最优的投资组合。

**Risk pooling, risk sharing and time diversification**

- Risk pooling vs. risk sharing

  - Variance of average insurance policy payoff decreases with the number of policies

  $$
  Var(\frac1n\sum_{i=1}^nx_i)=\frac1{n^2}\times{n}\sigma^2=\frac{\sigma^2}n
  $$

  - Variance of the total payoff becomes more uncertain

  $$
  Var(\sum_{i=1}^nx_i)=n\sigma^2
  $$

**Time diversification**

- True diversification
  - Requires holding fixed the total funds put at risk, and spreading the exposure across multiple sources of uncertainty

> 风险集中（Risk Pooling）、风险共享（Risk Sharing）和时间分散（Time Diversification）
>
> **风险集中（Risk Pooling）**和**风险共享（Risk Sharing）**是管理风险的两种常见方法。比如在保险业中，保险公司通过销售大量保单（风险集中）来降低每个保单的风险。因为虽然每个保单有可能引发大额赔付，但是只有少数保单真的会引发赔付，所以保险公司的总体风险（即所有保单赔付的平均值的方差）会随着保单数量的增加而降低。然而，如果考虑所有保单的总赔付（风险共享），那么总体风险是会随着保单数量的增加而增大的。
>
> 公式部分展示了这个观点，其中 $x_i$ 是每份保单可能的赔付额，$n$ 是保单的数量，$\sigma^2$ 是单份保单赔付额的方差。你可以看到，平均保单赔付的方差随着保单数量的增加而降低，而总赔付的方差则随着保单数量的增加而增大。
>
> **时间分散（Time Diversification）**是另一种管理风险的方式。它是指在一定的时间范围内，分散投资以降低风险。这种策略通常用于投资组合管理，投资者可以选择不同的投资机会，以减小单一投资失败带来的损失。注意，真正的时间分散需要在不增加总体投资风险的前提下，将投资分散到多个不确定性来源。

## 4 - Index Models

- Drawbacks to Markowitz procedure
  - Requires a huge number of estimates to fill the covariance matrix
  - Model does not provide any guidelines for finding useful estimates of these covariances or risk premiums
- Introduction of index model
  - Simplifies estimation of the covariance matrix
  - Enhances analysis of security risk premiums
- Optimal risky portfolios constructed using the index model

> **马科维茨模型的局限性**：
>
> 1. 需要大量的估计值来填充协方差矩阵：为了计算投资组合的风险（即投资组合的方差或标准差），我们需要知道所有投资组合中的资产之间的协方差。如果投资组合中有许多资产，那么这就需要大量的估计。这对于大型投资组合可能会非常困难和耗时。
> 2. 模型没有提供寻找这些协方差或风险溢价估计的有用指南：马科维茨模型主要关注的是风险和收益的权衡，但是如何得到这些风险和收益的预期值，模型并没有提供明确的指导。
>
> **指数模型的引入**：
>
> 1. 简化了协方差矩阵的估计：指数模型假设所有证券的回报都可以由一个共同的市场指数来解释，这大大减少了估计协方差的复杂性和需要的估计数量。
> 2. 提升了对证券风险溢价的分析：指数模型可以帮助我们更好地理解和分析证券的风险溢价，因为它将证券的回报分解为由市场指数和特定于公司的影响两部分。
>
> 最优投资组合是用指数模型构建的。这是因为在现实中，由于上述的限制，投资者往往会选择使用指数模型或其他一些更简单的模型，而不是直接使用马科维茨模型。

### 4.1 - A single-factor security market / Single index model

> 单因子证券市场(single-factor security market)是一种市场模型。该模型假设所有证券的回报都可以由单一的**共同因子**来解释，通常这个因子是**市场指数的回报**。这个模型可以看作是指数模型的一种形式。

- Advantages of the single-index model

  - Number of estimates required is a small fraction of what would otherwise be needed
  - Specialization of effort in security analysis

  $$
  r_i = E(r_i)+\beta_im+e_i
  $$

  - $\beta_i$ = sensitivity coefficient for firm $i$
  - $m$ = market factor that measures unanticipated developments in the macroeconomy
  - $e_i$ = firm-specific random variable

> "单因子模型"或"单指数模型"是一种简化的投资组合理论模型。这种模型的主要优势在于其简洁性和易于理解。单指数模型大大减少了需要估计的参数的数量。这是因为它只需要估计每个投资项目或证券的风险、收益率和与市场因子的相关性，而不是所有证券间的相关性。这大大减少了计算的复杂性。
>
> $r_i = E(r_i)+\beta_im+e_i$
>
> 此公式计算了某个证券 $i$ 的总回报，其中
>
> - $r_i$ 代表证券 $i$ 的回报率
>
> - $E(r_i)$ 代表证券 $i$ 的预期回报率
>
> - $\beta_i$ 代表证券 $i$ 的贝塔系数，这是一个度量指标，显示了证券 $i$ 的回报与市场因子的变动之间的关系，也就是证券 $i$ 的市场风险
>
> - $m$ 代表市场因子，也就是市场的超额回报或未预期的宏观经济变动
>
> - $e_i$ 代表特定于证券 $i$ 的随机误差项，也被称为证券 $i$ 的特异风险。

- **Regression equation**
  $$
  R_i(t) = \alpha_i+\beta_iR_M(t)+e_i(t)
  $$

- Expected return-beta relationship
  $$
  E(R_i) = \alpha_i+\beta_iE(R_M)
  $$

> 1. **回归方程**: 这个公式是描述资产i的收益$R_i(t)$与市场收益$R_M(t)$之间的关系。$\alpha_i$ 是资产i的截距项（也可以被解释为当市场回报为零时，资产i的预期回报），$\beta_i$ 是资产i对市场的敏感度（或者说，市场回报变化1%时，资产i的回报变化百分比），$e_i(t)$ 是资产i的误差项，反映了资产i的回报中无法通过市场回报解释的部分（也称为特异性风险或不可分散风险）。
> 2. **期望回报-beta关系**: 这个公式表达了资产i的期望回报$E(R_i)$与市场期望回报$E(R_M)$之间的关系。这里，$\alpha_i$ 和 $\beta_i$ 同样代表截距项和市场敏感度。这个公式是回归方程的期望值版本，表达了在平均或预期情况下，资产i的回报如何与市场回报关联。

- Total risk = systematic risk + firm specific risk

$$
\sigma^2_i = \beta_i^2\sigma_m^2 + \sigma^2(e_i)
$$

- Covariance = product of betas * market-index risk (市场指数风险)

$$
Cov(r_i, r_j) = \beta_i\beta_j\sigma^2_M
$$

- Corrleation = product of correlations with the market index

> **相关性 = 与市场指数的相关性之积**
>
> 这个公式描述的是两个资产回报的相关性可以由它们与市场指数的相关性之积来近似。这是在单索引模型（single-index model）中使用的近似，这个模型假设资产的回报主要由市场因素决定，而公司特定因素的影响可以忽略不计。然而，在实际中，这个近似可能并不总是精确的，因为可能还存在其他共同的影响因素。

### 4.2 - Index model and diversification

- Variance of the equally-weighted portfolio of firm-specific components:

$$
\sigma^2(e_p) = Var(\frac 1n \sum_{i=1}^n e_i)=\sum_{i=1}^n(\frac 1n)^2\sigma^2(e_i)=\frac 1n \sum_{i=1}^n \frac {\sigma^2(e_i)} {n} = \frac 1n \overline \sigma^2 (e)
$$

- When $n$ gets large, $\sigma^2(e_p)$ becomes negligible
- As diversification increases, the total variance of a portfolio approaches the systematic variance

> 当投资组合的多样性增加时，投资组合的总体方差会逐渐接近系统性方差，这一现象也被称为多样化的效果。以下是详细解释：
>
> 在这个例子中，我们考虑的是一个均等权重的投资组合，这个投资组合由n个资产构成，每个资产的权重都是1/n。对于每个资产，它的公司特定风险是$e_i$，并且它的方差是$\sigma^2(e_i)$。
>
> 1. $\sigma^2(e_p)$ 是这个均等权重投资组合的**公司特定风险的方差**。它是所有资产的公司特定风险的方差的加权平均。权重是每个资产在投资组合中的权重的平方，即 $(1/n)^2$。
> 2. $\frac 1n \overline \sigma^2 (e)$ 是**所有资产公司特定风险的方差的平均值**，然后再除以资产的数量n。这表示，当资产的数量n越来越大时，投资组合的公司特定风险的方差$\sigma^2(e_p)$将趋近于0。这是因为，当我们持有更多的资产时，这些资产的公司特定风险会通过多样化而被抵消。
> 3. "As diversification increases, the total variance of a portfolio approaches the systematic variance" 这句话意味着，**当我们持有更多的资产时，投资组合的总体风险（即投资组合的方差）将主要由系统性风险决定，而公司特定风险的影响将变得可以忽略不计。这是因为系统性风险是无法通过多样化来消除的，而公司特定风险可以通过持有多样化的投资组合来消除。**

![image-20230611010830986](https://images.wu.engineer/images/2023/06/11/image-20230611010830986.png)

> 这幅图描述的情景和上面的公式相同。即随着投资组合的多样性增加时，投资组合的总体方差会逐渐接近系统性方差。当$n$变大时，$\sigma^2(e_p)$逐渐变得不重要。

**Excess monthly returns on amazon and the market index** (not exam)

![image-20230611011019820](https://images.wu.engineer/images/2023/06/11/image-20230611011019820.png)

> "Excess return" 是指投资的回报超过某个基准或参考回报的部分。通常情况下，这个基准是一个无风险利率，例如短期国债的收益率。这个基准也可以是另一个投资的回报，例如一个市场指数。
>
> 因此，"excess monthly return" 是指投资在一个月内的回报超过无风险利率或者参考基准的部分。
>
> 例如，如果一个股票在一个月内的回报率是5%，同时无风险利率为1%，那么这个股票在这个月的超额回报（excess return）就是5% - 1% = 4%。这个超额回报反映的是这个股票在一个月内相对于无风险投资的额外收益。
>
> 超额回报是投资分析中的一个重要概念，因为它反映的是投资者为承担额外风险而获得的额外回报。根据资本资产定价模型（CAPM），一个投资的预期超额回报应该与它的系统性风险（beta）成比例。
>
> 风险溢价(risk premium)常被看作一种期望的超额回报(excess return)，但不是所有的超额回报都是风险溢价。例如，一项投资的实际超额回报可能会由于各种原因（如市场情绪、突发事件等）而高于或低于预期的风险溢价。

### 4.3 - Security characteristic line (SCL)

$$
R_i(t) = \alpha_i + \beta_i R_{S\&P500} (t) + e_i(t)
$$

- $R_i(t)$: Excess return of security $i$
- $\alpha_i$: Expected excess return when the market excess return is zero
- $\beta_i$: Sensitivity of security $i$ return to changes in the return of the market
- $R_{S\&P500}(t)$: Expected excess return of the market (S&P 500 index)
- $e_i(t)$: Zero-mean, firm-specific suprise in security $i$ return in month $t$

> 证券特性线（Security Characteristic Line, SCL）是用来描述一个特定证券的超额回报（Excess Return）与市场超额回报（这里是S&P 500的超额回报）之间关系的线性模型。
>
> - $R_i(t)$ 是证券 $i$ 在某一时间点 $t$ 的超额回报，这意味着它是该证券的回报率减去无风险利率。
> - $\alpha_i$ 是证券 $i$ 的截距项。当市场超额回报为零时，这是证券 $i$ 预期的超额回报。这个值应当是一个常数。
> - $\beta_i$ 是证券 $i$ 的斜率项，代表证券 $i$ 的回报对市场回报变化的敏感度。这个值反映了证券 $i$ 的系统性风险，值越大代表对市场变化的反应越敏感。
> - $R_{S\&P500}(t)$ 是在时间 $t$ ，S&P 500的预期超额回报。这通常被视为市场的预期回报。
> - $e_i(t)$ 是在时间 $t$ ，证券 $i$ 的特定公司的意外回报，它的均值为零。这一项捕获了那些不可预测并且特定于公司的事件对证券回报的影响，如公司财报、新产品发布等。
>
> 这个模型描绘了证券的超额回报如何依赖于市场的超额回报以及特定于公司的意外事件。特别地，$\alpha_i$ 和 $\beta_i$ 提供了一个关于证券 $i$ 的系统性风险和预期回报的度量。

![image-20230613010129453](https://images.wu.engineer/images/2023/06/13/image-20230613010129453.png)

#### The industry version of the index model

- Predicting betas
  - Betas tend to drift to 1 over time
- Rosenberg and Guy found the following variables to help predict betas
  1. Variance of earnings
  2. Variance of cash flow
  3. Growth in earnings per share
  4. Market capitalization (firm size)
  5. Dividend yield
  6. Debt-to-asset ratio

> 贝塔系数 $\beta$ 是一个衡量投资风险或系统性风险的统计度量，它表示了证券价格对整体市场变动的敏感度。贝塔系数趋向于1，意味着这只证券的价格变动会随着市场的变动而变动。
>
> Rosenberg 和 Guy 提出了以下可以用来预测贝塔系数的变量：
>
> 1. 收益的方差：收益的不稳定性可能影响贝塔系数，因为更高的收益波动性可能与更高的风险相关。
> 2. 现金流的方差：类似于收益的方差，现金流的不稳定性可能影响贝塔系数。
> 3. 每股收益的增长：这可能反映公司的增长潜力，从而影响贝塔系数。
> 4. 市值（公司规模）：较大的公司可能因为其经济规模和市场影响力，相比较小的公司具有较低的贝塔系数。
> 5. 股息收益率：更高的股息收益率可能暗示更低的风险，因此可能与较低的贝塔系数相关。
> 6. 资产负债率：更高的资产负债率可能表示更高的风险，因此可能与较高的贝塔系数相关。
>
> 这些变量可以帮助我们更好地理解和预测贝塔系数，从而更好地评估和管理投资风险。

> 方差($\sigma$)和贝塔系数($\beta$)都是用来衡量风险，但是他们衡量的风险不是同一个概念
>
> - 方差主要衡量的是一个投资的回报率的波动性或不稳定性。一个高方差的投资会有很大的价格波动，因此具有更高的风险。而一个低方差的投资则相对稳定，风险较低。
> - 贝塔系数（Beta）是衡量一个投资相对于整个市场的风险。它衡量的是一个投资的回报与市场总体回报之间的相关性。贝塔系数高于1表示该投资的价格波动性大于市场的平均水平，贝塔系数低于1则表示价格波动性低于市场平均水平。因此，贝塔系数可以被看作是衡量相对风险或系统性风险的指标，而方差则是衡量绝对风险或总体风险的指标。

### 4.4 - Portfolio Construction and the Single-Index Model 投资组合的构建和单一指数模型

- Alpha $\alpha$ and security analysis

1. Macroeconomic analysis used to estimate the risk premium and risk of the market index
2. Statistical analysis used to estimate beta $\beta$ coefficients and residual variances, $\sigma^2(e_i)$ of all securities
3. Establish expected return of each security absent any contribution from security analysis
4. Security-specific expected return forecasts are derived from various security-valuation models

> Alpha（α）通常被用来衡量一个投资或者投资策略相对于其基准的表现。具体来说，Alpha是投资实际产生的超额回报，超出了由其潜在的市场风险（通常用贝塔系数衡量）所预期的回报。换句话说，Alpha是投资的实际回报与按照市场风险调整后的预期回报之间的差额。
>
> Alpha代表的是当市场超额回报为零时，证券的预期超额回报。这可以被看作是证券的固有价值或者内在表现，不依赖于市场的整体表现。这个概念常用于评估投资经理或策略的性能，如果一个投资产生了正Alpha，那么它就是在超过了风险调整后的预期回报。
>
> 1. 宏观经济分析：这是估计市场指数的风险溢价和风险的方法。风险溢价是指投资者因投资风险而要求的额外回报，是预期回报率超过无风险利率的部分。市场风险可以通过市场指数的波动来度量。
> 2. 统计分析：这是用来估计每一种证券的贝塔系数（β）和残差方差（σ²(e_i)）的方法。贝塔系数是证券收益对市场变动的敏感度，残差方差则衡量证券收益的不确定性。
>    - 模型中的残差部分 $e_i(t)$ 就是指股票回报率与通过模型预测的回报率之间的差异。这个差异可能是由于公司特定的新闻、事件或其他无法通过市场回报率捕捉到的因素引起的。这部分的方差就是残差方差。
> 3. 建立每种证券的预期回报：这是在没有任何来自证券分析的贡献的情况下建立每种证券的预期回报的过程。这种预期回报通常基于市场数据和统计模型。
> 4. 证券特定的预期回报预测：这些预测是从各种证券估值模型中得出的。这些模型可以包括如股息贴现模型、现金流贴现模型、市盈率模型等，都可以用于预测证券的未来价格和回报。

- Single-index model input list:

1. Risk premium on the S&P 500 portfolio
2. Strandard deviation of the S&P 500 portfolio (measure risk)
3. n sets of estimates of:
   - Beta coefficients
   - Stock residual variances
   - Alpha values

- Optimal risky portfolio in the single-index model
  - Objective is to select portfolio weights to maximize the Sharpe ratio of the portfolio

$$
\begin{aligned}
E(R_P) &= \alpha_P + E(R_M) \beta_P = \sum_{i=1}^{n+1}w_i\alpha_i+ E(R_M)\sum_{i=1}^{n+1}w_i\beta_i \\
\sigma_P &= [\beta^2_P\sigma^2_M+\sigma^2{(e_P)}]^{1/2} = [\sigma^2_M(\sum_{i=1}^{n+1}w_i\beta_i )^2+\sum_{i=1}^{n+1}w_i^2\sigma^2(e_i)] \\
S_p &= \frac {E(R_P)} {\sigma_P} 
\end{aligned}
$$

> 投资组合的预期收益 = 超额回报 $\alpha$ + 指数预期回报 $E(R_M)$ * 敏感度 $\beta$
>
> ​	$\alpha$ 是潜在的市场风险所预期的回报（额定预期回报）和实际回报的差额

#### Portfolio Construction

-  Optimal risky portfolio in the single-index model is a combination of two components portfolios:
  - Active portfolio, denoted by A
  - Market-index portfolio (passive portfolio), denoted by M

> 1. 主动投资组合（Active Portfolio，标记为A）：这部分投资组合主要根据选股能力和市场定价错误来调整，试图赚取超出市场的回报。
> 2. 市场指数投资组合（Passive Portfolio，标记为M）：这部分投资组合直接持有整个市场的指数，如S&P 500，不进行主动的选股，目标是追踪市场的表现。

### 4.5 - Summary of Optimization Procedure

1. Compute the initial position of each security:

$$
w_i^0=\frac {\alpha_i} {\sigma^2(e_i)}
$$

2. Scale those initial positions:

$$
w_i = \frac {w_i^0} {\sum^n_{i=1}w_i^0}
$$

3. Compute the alpha of the active portfolio

$$
\alpha_A = \sum^n_{i=1}w_i\alpha_i
$$

4. Compute the residual variance of A:

$$
\sigma^2(e_A) = \sum^m_{i=1}w_i^2\sigma^2(e_i)
$$

5. Compute the initial position in A:

$$
w_A^0 = \frac {\alpha/\sigma^2(e_A)} {E(R_M)/\sigma^2_M}
$$

6. Compute the beta of A:

$$
\beta_A = \sum_{i=1}^nw_i\beta_i
$$

7. Adjust the initial position in A:

$$
w^*_A = \frac {w^0_A} {1+(1-\beta_A)\times w_A^0}
$$

- When $\beta_A=1$, $w^*_A = w_A^0$

8. Optimal risky portfolio now has weights:

$$
w^*_M = 1-w^*_A \\
w^*_i = w^*_A \times w_i
$$

9. Calculate the risk premium of $P$ (optimal risky portfolio)

$$
E(R_P) = (w^*_M + w^*_A\beta_A) \times E(R_M) +w^*_A \alpha_A
$$

10. Compute the variance of $P$:

$$
\sigma^2_P = (w^*_M + w^*_A\beta_A)^2 \sigma^2_M + [w^*_A\sigma(e_A)]^2
$$

### 4.6 - Optimal risky portfolio

- Information ratio

  - The contribution of the active portfolio depends on the ratio of its alpha to its residual standard deviation (step 5)
  - Calculated as the ratio of alpha to the standard deviation of diversifiable risk
  - The information ratio measures the extra return we can obtain from security analysis

- Sharpe ratio

  - The Sharpe ratio of an optimally constructed risky portfolio will exceed that of the index portfolio (the passive strategy)

  $$
  S^2_P = S_M^2 + [\frac {\alpha_A} {\sigma(e_A)}]^2
  $$

- Efficient frontier

![image-20230613014538646](https://images.wu.engineer/images/2023/06/13/image-20230613014538646.png)

![image-20230613014548170](https://images.wu.engineer/images/2023/06/13/image-20230613014548170.png)

- Full Markowitz model is better in principle, but
  - The full-covariance matrix invokes estimation risk of thousands of terms
  - Cumulative errors may result in a portfolio that is actually inferior
  - The single-index model is practical and decentralizes macro and security analysis

## 5 - CAPM, APT Theory and Factor Models

### 5.1 - CAPM (Capital Asset Pricing Model) 资本资产定价模型
- CAPM is a set of predictions concerning equilibrium expected returns on risky assets
- Based on two sets of assumptions
  - Individual behavior
  - Market structure
- Markowitz established modern portfolio management in 1952
- Sharpe, Lintner and Mossin published CAPM in 1964



- It is the equilibrium model that underlies all modern financial theory
- Derived using principles of diversification with simplified assumptions

Assumptions:

![image-20230613174437440](https://images.wu.engineer/images/2023/06/13/image-20230613174437440.png)

> 资本资产定价模型（Capital Asset Pricing Model，CAPM）是一个经济模型，用于确定一个投资的预期回报，并据此来评估资产的合理价格。CAPM认为投资的预期回报应等于无风险回报率加上风险溢价。
>
> CAPM的基本方程式如下：
>
> E(Ri) = Rf + βi [E(Rm) - Rf]
>
> 其中：
>
> - E(Ri) 是资产i的预期回报
> - Rf 是无风险回报率
> - βi (Beta) 是资产i的系统性风险度量，反映了资产回报与市场整体回报变动的敏感性
> - E(Rm) 是市场整体的预期回报
> - [E(Rm) - Rf] 是市场风险溢价，反映了市场投资相比无风险投资的预期额外回报
>
> 这个模型的主要假设包括：投资者是理性的、市场是有效的、所有投资者都以单期持有期和相同的预期收益率进行投资决策、不存在无风险套利机会，没有税，没有交易手续费等

#### Resulting equilibrium conditions 由此产生的平衡条件

- All investors will hold the same portfolio for risky assets - market portfolio
- Market portfolio contains all securities and the proportion of each security is its market value as a percentage of total market value

> CAPM模型下的两个重要平衡条件
>
> 1. "所有投资者将持有相同的风险资产投资组合 - 市场投资组合"：这个假设基于所有投资者都是理性的，并且他们都会通过选择最大化夏普比率的投资组合来优化他们的投资。在这个假设下，所有的投资者，无论他们的风险承受能力如何，都将选择相同的风险资产组合，这就是市场投资组合。
> 2. "市场投资组合包含所有的证券，每个证券在组合中的比例等于其在总市值中的百分比"：这意味着市场投资组合是根据每个证券在市场总值中的比例构建的。例如，如果一家公司的市值占整个市场的2%，那么在市场投资组合中，该公司的股票也将占2%。
>
> 这两个条件是理想化的情况，能帮助理解CAPM模型和市场行为，但在实际的投资环境中可能并不总是成立，因为每个投资者的风险承受能力，投资目标和信息可能会有所不同。
>
> - 市场投资组合是指一个包含了所有风险资产的投资组合，其中每种资产的权重按照其市场价值占总市场价值的比例确定。这个投资组合理论上包含所有可投资的风险资产，包括股票、债券、商品、房地产等等，不论其市场是公开的还是私人的
> - 在现实中，投资者的投资组合通常只包含一小部分的可投资资产，而市场投资组合则包括了所有的可投资资产。因此，投资者的投资组合与市场投资组合在构成和风险收益特性上可能会有显著的差异。

#### The efficient frontier and the CAL (Capital Allocation Line)

![image-20230613175118667](https://images.wu.engineer/images/2023/06/13/image-20230613175118667.png)

![image-20230613175129792](https://images.wu.engineer/images/2023/06/13/image-20230613175129792.png)

> **1. 资本市场线（CML）**
>
> CML 描述的是在完全有效的市场中，风险投资组合与无风险资产之间的投资组合的风险和回报之间的关系。CML 的斜率代表了市场投资组合的夏普比率（Sharpe Ratio）。CML 上的每一点都代表一个可能的投资组合，这个投资组合包括市场组合和无风险资产的某种组合。CML 的截距是无风险利率，CML 的另一端是市场组合，代表全部资金投入到市场组合中。
>
> - 与CML不同，CAL不假设市场完全有效，也不假设所有投资者都选择相同的风险投资组合。CAL 上的每一点都代表一个可能的投资组合，这个投资组合包括某个风险投资组合和无风险资产的某种组合。
> - CML 可以被看作是 CAL 的一个特例。当风险投资组合是市场投资组合时，CAL就变成了CML。
> - 换句话说，CML是在有效市场假设下，所有投资者都选择同一风险投资组合（即市场组合）的情况下的CAL。

#### Market risk premium 市场风险溢价

- The risk premium on the market portfolio is proportional to its risk and the degree of risk aversion 风险厌恶

$$
E(R_M) = \overline A \sigma^2_M
$$

- $E(R_M)$: 市场风险溢价
- $\overline A$: 所有投资者的平均风险厌恶
- $\sigma^2_M$: 风险

#### Return and risk for individual securities 单个证券的回报和风险

- An individual security’s risk premium is a function of:
  - Its contribution to the risk of the market portfolio or the risk of investors’ overall portfolios: All investors use the same input list (i.e. they all end up usiong the market as their optimal risky portfolio)
  - The covariance of returns with the assets that make up the market portfolio

> CAPM模型下单个证券的风险溢价（risk premium）的决定因素：
>
> 1. 该证券对市场组合风险或投资者整体投资组合风险的贡献：如果一个证券的收益与市场整体收益高度相关，那么这个证券就可能对市场组合的风险产生更大的影响。换句话说，如果这个证券的价格变动很大，并且与市场的变动有很强的关联性，那么它就有可能提高市场组合的风险。因此，投资者会要求更高的风险溢价作为持有这种风险较高的证券的补偿。
>    - 即该证券和市场的关联度，关联度越高，则越有可能提高市场组合的风险。
> 2. 该证券的回报与构成市场投资组合的其他资产的回报之间的协方差（covariance）：这是一种衡量两个随机变量（这里是两个证券的回报）同时变动的趋势的统计指标。如果一个证券的回报与市场投资组合的其他证券的回报高度相关，那么这个证券可能就会对市场投资组合的风险产生更大的影响，投资者会要求更高的风险溢价。如果一个证券的回报与市场的回报几乎没有关系，那么这个证券对市场投资组合的风险影响就会较小，投资者可能会接受较低的风险溢价。
>    - 即该证券和其他证券（资产）的回报之间的关联度。如果关联度越高，则越有可能提高市场组合的风险。
>
> 在CAPM模型中，风险溢价是通过Beta系数来衡量的，Beta系数反映了证券的回报与市场的回报之间的相关性。Beta系数越高，证券的风险溢价就越高，因为这意味着这个证券对市场投资组合的风险的影响越大。

> 回顾：Beta系数反映了证券的回报与市场的回报之间的相关性。

**Example:**

- Covariance of GE (通用电气) return with the market portfolio:

$$
\sum_{i=1}^nw_i Cov(R_i,R_GE) = Cov(\sum_{i=1}^n w_iR_i, R_{GE})
$$

- The reward-to-risk ratio for GE would be:

$$
\frac {\text{GE's contribution to risk premium}} {\text{GE's contribution to variance}} = \frac {E(R_{GE})}{Cov(R_{GE},R_M)}
$$

- The reward-to-risk ratio for investment in market portfolio:

$$
\frac {\text{Market risk premium}} {\text{Market variance}} = \frac {E(R_M)} {\sigma^2(R_M)}
$$

- These two ratio should be equal

$$
\frac {E(R_{GE})}{Cov(R_{GE},R_M)} = \frac {E(R_M)} {\sigma^2(R_M)}
$$

- Risk premium for GE

$$
E(R_{GE}) = E(r_{GE}) - r_f \\
E(R_{GE}) = \frac {Cov(R_{GE}, R_M)} {\sigma^2(R_M)}E(R_M)
$$

- Restating, we obtain:

$$
E(r_{GE}) = r_f + \beta_{GE}\lfloor E(r_M) -r_f \rfloor
$$

- Where $\beta_i$ is the covariance of the return of asset i with the return of the market (M) divided by the variance of the return of the market over a certain period of time

$$
\beta_{GE} = \frac {Cov(R_{GE}, R_M)} {\sigma^2(R_M)}
$$

- Risk premium is the product of a ‘benchmark risk premium’ and the relative risk of the particular asset as measured by its beta

> 小写的r代表无风险回报率，大写R代表风险溢价

#### Expected return-beta relationship

- CAPM holds for the overall portfolio because:

$$
\begin {aligned}
E(r_P) &= \sum_k w_k E(r_k) \text{ and} \\
\beta_{P} &=\sum_k w_k\beta_k
\end{aligned}
$$

- This also holds for the market portfolio

$$
E(r_M) = r_f + \beta_M [E(r_M) - r_f]
$$

> "Expected return-beta relationship" 是资本资产定价模型 (Capital Asset Pricing Model, CAPM) 的核心，该模型描绘了一个资产的预期收益与其系统性风险（也称为 beta）之间的关系。
>
> 公式基本上是说，一个资产的预期收益率应该等于无风险利率加上该资产的 beta 乘以市场风险溢价。换言之，资产的预期收益率与其 beta 是正相关的：beta 越高，资产的预期收益率也应该越高，以补偿投资者承担更高的风险。这就是所谓的 "expected return-beta relationship"。

#### The security market line

![image-20230613185211323](https://images.wu.engineer/images/2023/06/13/image-20230613185211323.png)

![image-20230613185353902](C:/Users/TedWu/AppData/Roaming/Typora/typora-user-images/image-20230613185353902.png)

### 5.2 - Single-index model and realized returns

- To move from expected to realized returns, use the index model in excess return from:

$$
R_i = \alpha_i+\beta_iR_M+e_i
$$

- The index model beta coefficient is the same as the beta of the CAPM expected return-beta relationship

### 5.3 - Single factor model

- Returns on a security come from two sources:
  - Common macro-economic factor
  - Firm specific events
- Possible common macro-economic factors:
  - GDP growth
  - Interest rates

$$
R_i = E(R_i) + \beta_iF + e_i
$$

- $R_i$: Excess return on security
- $\beta_i$: Factor sensitivity or factor loading or factor beta
- $F$: Surprise in macro-economic factor (F could be positive or negative but has expected value of zero)
- $e_i$: Firm specific events (zero expected value)

### 5.4 - Extension of the CAPM

1. Identical input lists
   - In the absense of private informaion, investors should assume $\alpha$ values are zero
2. Zero-beta model
   - Helps to explain positive $\alpha$ on low beta stocks and negative $\alpha$ on high beta stocks
3. Labor income and other nontraded assets
   - Many assets are not tradeable
4. Multiperiod model and hedge portfolios
   - Investors should be more concerned with the stream of consumption that wealth can buy for them
5. Consumption-based CAPM (CCAPM)
   - Investors allocates wealth between consumption tody and investment for the future
6. Liquidity
   - Financial costs inhibit trades
   - Liquidity of an asset is the ease and speed with which it can be sold at fair market value
   - Illiquidity can be measured in part by the discount from fair market value a seller must accept if the asset is to be sold quickly

> - alpha 是投资（如股票或投资组合）与其基准（通常是市场平均或特定的市场指数）相比的超额收益。

>1. **Identical input lists**：如果没有私有信息（即，所有投资者都拥有市场上所有公开的信息），所有投资者都应该假设各个资产的 alpha 值（预期超额收益）为零。这是基于市场效率理论，认为所有公开信息已经被市场充分吸收并反映在资产价格中。
>2. **Zero-beta model**：这个模型用于解释低 beta 股票的 alpha 值为何可能为正，高 beta 股票的 alpha 值为何可能为负。这可能是由于投资者对 beta 超过 1 的股票预期过高，导致其价格高于实际价值，反之亦然。
>3. **Labor income and other nontraded assets**：许多资产（如劳动收入、房产等）是不可交易的，但它们对投资者的财富和消费决策产生影响。这是 CAPM 没有考虑的一点。
>4. **Multiperiod model and hedge portfolios**：投资者更关心的是他们的财富能为他们购买的消费流，而不仅仅是单期的资产收益。因此，需要考虑多期模型和对冲投资组合来规划和保护未来的消费能力。
>5. **Consumption-based CAPM (CCAPM)**：投资者在当前消费和未来投资之间分配财富。这个模型考虑了投资者的消费和储蓄决策，以及其对投资决策的影响。
>6. **Liquidity**：交易成本可能会阻止交易的进行。资产的流动性是指其能被以公平市场价值快速出售的程度。如果资产不能快速出售，或者需要接受低于公平市场价值的折扣才能快速出售，那么这就反映了该资产的流动性不佳。

### 5.5 - The Relationship Between Illiquidity and average returns

![image-20230613194612747](https://images.wu.engineer/images/2023/06/13/image-20230613194612747.png)

不流动性和平均回报的关系

> 不流动性（Illiquidity）和平均收益率之间的关系是金融经济学的一个重要主题。这个关系主要源于以下逻辑：如果一个资产不容易买卖（也就是不流动性较高），那么投资者可能会要求更高的收益作为对承担这种不便的补偿。
>
> 更具体地说，不流动性可能会引起以下两种问题，这两种问题都可能影响到资产的收益率：
>
> 1. 交易成本：当资产的流动性较差时，买卖这种资产可能会产生更高的交易成本。这些成本可能包括更大的买卖价差、更高的佣金费用、或者更高的市场冲击成本等。
> 2. 交易延迟：当资产的流动性较差时，可能需要花费更多的时间才能找到交易对手，这种交易延迟可能会导致投资者失去一些投资机会。
>
> 因此，理论上，如果一个资产的流动性较差，那么投资者可能会要求这种资产提供更高的预期收益，作为对承担这些额外成本和风险的补偿。这也就是说，不流动性和平均收益率之间可能存在正向关系。

#### **Liquidity risk**

When a type of asset has low liquidity, which means it is hard to sell. In this case, the investor usually will hold more risk than the asset that has high liquidity, so investors are expect to have more return from this type of asset.

流动性风险是指投资者在需要将资产转换为现金时，可能因为市场的流动性条件而不能在合理的时间内以合理的价格进行交易的风险。换句话说，如果一个资产难以快速卖出而不影响其市场价格，那么这个资产就存在流动性风险。

流动性风险可以在两个层面上影响投资者：

1. 资产层面：如果一个资产的市场流动性较差（例如，非上市股票、房地产或某些衍生产品），那么投资者可能需要花费更多的时间和成本来买卖这个资产，或者可能需要以大幅折价的价格来卖出这个资产。

2. 市场层面：在某些情况下，整个市场的流动性也可能会暂时降低，这通常在市场压力较大时发生，例如在金融危机期间。在这种情况下，即使是本来流动性较好的资产，投资者也可能难以在合理的时间内以合理的价格进行交易。

由于流动性风险可能会影响到投资者的投资决策和回报，因此在进行投资时，投资者需要考虑到这个风险，并采取相应的管理策略，例如保持一部分流动性较好的资产，或者采取对冲策略等。

- When liquidity in one stock decreases, it commonly tends to decrease in other stocks at the same time.
- Investors demand compensation for liquidity risk, demonstrated by firms with greater liquidity risk having higher average returns.
	- Liquidity betas
	- Liquidity Beta 是一个金融术语，主要用于衡量一个资产的收益率与市场整体流动性变化的敏感性。简单来说，它反映了资产收益率对流动性风险的敞口。Liquidity Beta 是资本资产定价模型 (CAPM) 和Fama-French三因子模型等资产定价模型的扩展。
		在具体计算上，Liquidity Beta 是通过回归分析来得到的，通常是将资产的超额收益率（即资产的收益率减去无风险利率）作为因变量，将市场的超额收益率和市场的流动性变化作为自变量进行回归分析，其中市场的流动性变化对应的系数就是Liquidity Beta。
		- 如果 Liquidity Beta 为正，那么当市场流动性提高（例如，买卖更容易，买卖差价缩小）时，资产的预期收益率可能会下降；反之，当市场流动性下降时，资产的预期收益率可能会上升。
	  - 如果 Liquidity Beta 为负，那么当市场流动性提高时，资产的预期收益率可能会上升；反之，当市场流动性下降时，资产的预期收益率可能会下降。
		这个概念主要用于对资产的流动性风险进行定量分析，以帮助投资者在投资决策中更好地管理流动性风险。
		
> 具有较高流动性风险的公司（或资产）通常会有较高的平均回报率，这是因为流动性风险本身就是一种风险，投资者在决定投资时会要求得到较高的回报来补偿这种风险。
>
> 流动性风险通常指的是一个资产无法在需要时快速以合理的价格出售的风险。在有流动性问题的公司或资产中投资，意味着如果投资者需要将他们的投资快速转换为现金，他们可能会发现难以找到买家，或者必须以低于市场价值的价格出售。这会对投资者的收益产生负面影响。
>
> 为了补偿这种风险，投资者会要求较高的回报。这就是为什么具有较高流动性风险的公司的平均回报率较高。这种现象也被称为流动性溢价，即投资者对承担流动性风险的补偿。
>
> 然而，也应注意，这并不意味着所有具有高流动性风险的公司或资产都能提供高回报。这仅仅是投资者在做出投资决策时一种期望

### 5.6 - Multifactor models

> 多因子模型（Multifactor Models）是一种用于资产定价和投资决策的金融模型，它认为资产的预期收益率不仅仅由市场风险（即CAPM中的市场Beta）决定，还受到多种其他因素的影响。
>
> 这些因素可能包括：公司规模、账面市值比（价值因子）、过去收益率（动量因子）、流动性、盈利能力、投资风险等。每一个因子都有自己的风险溢价，即投资者愿意为承担该因素的风险而获取的额外收益。
>
> 在实际应用中，多因子模型可以帮助投资者更准确地评估资产的风险和预期收益，从而做出更优的投资决策。例如，Fama-French三因子模型和五因子模型就是著名的多因子模型，它们将公司规模和账面市值比（Fama-French三因子模型），以及盈利能力和投资风险（Fama-French五因子模型）作为额外的因素来解释资产的预期收益率。
>
> 值得注意的是，虽然多因子模型在理论和实践中都有广泛的应用，但它们的解释能力并不完全，仍然存在一些不能被这些因子解释的收益率差异。此外，多因子模型的设定也可能会受到数据挖掘和过度拟合的影响，因此在应用多因子模型时，需要谨慎对待这些问题。
>
> $$R_i = E(R_i) + \beta_{iGDP}GDP+\beta_{iIR}IR+e_i$$

#### Overview

- Arbitage 套利 is the exploitation of security mispricing in such a way that risk-free profits can be earned
  - Most basic principle of capital market theory is that well functioning security markets rule out arbitage opportunities
- Generalization of the security market line of the CAPM to gain richer insight into the risk-return relationship
  - Arbitage pricing theory (APT)

> - 套利是指通过利用证券定价错误而赚取无风险利润的过程。在理想的情况下，如果资本市场运行良好，那么市场应该能够消除套利机会。这是因为如果存在套利机会，投资者会立即利用这种差价进行交易，从而将价格推回到合理的水平，消除了套利机会。
> - 资本资产定价模型（CAPM）中的证券市场线（SML）描述了证券的预期回报与其系统性风险（用贝塔系数衡量）之间的关系。在SML中，预期回报是风险无关的部分（无风险利率）和风险相关的部分（贝塔系数乘以市场风险溢价）之和。
>
> 套利定价理论（APT）是对CAPM的一种扩展和一般化，它提供了一种更深入的方法来理解风险和回报之间的关系。
>
> 与CAPM不同，APT不假设所有投资者都有相同的预期并且只考虑一个市场风险因子（即市场组合的贝塔系数）。相反，APT允许存在多个风险因子，并且各个证券对这些风险因子的敏感性可能会不同。这使得APT能够捕捉到CAPM可能忽视的风险因素，从而提供了对风险和回报之间关系的更丰富的洞察。
>
> 但是，APT的一个挑战是，它并没有提供明确的指导来确定哪些风险因子是最重要的，或者如何去衡量这些风险因子。这些问题通常需要依赖于经验和实证研究。

#### **Models**

- Extra market sources of risk may arise from several sources
  - Uncertainty about interest rates or inflation
  - Use more than one factor: market return, GDP, expected inflation, interest rates
- Multifactor models posit that returns respond to several systematic risk factors, as well as firm-specific influences
  - Useful in risk management applications
  - Estimate a beta or factor loading for each factor using multiple regression

> 除了市场回报率以外，还有其他一些系统性风险因子可能影响到证券的预期回报。这些额外的风险因子可能来源于多个不同的领域，例如利率或通货膨胀的不确定性，GDP，预期通胀，利率等。
>
> 多因子模型则是基于这个思想，它假设证券的回报会受到多个系统性风险因子的影响，以及特定公司的影响。这些模型在风险管理应用中非常有用，因为它们可以帮助我们更好地理解和量化影响证券回报的各种风险来源。对于每一个风险因子，我们可以通过多元回归分析来估计它的贝塔系数或因子载荷，这个系数度量了证券回报对该风险因子变化的敏感性。如果贝塔系数较大，那么证券的回报就更容易受到该风险因子的影响。

#### Equations

$$
R_i = E(R_i) + \beta_{iGDP}GDP+\beta_{iIR}IR+e_i
$$

- $R_i$: Excess return for security i
- $E(R_i)$: Expected excess return for security i
- $\beta_{iGDP}$: Factor sensitivity for GDP
- $\beta_{iIR}$: Factor sensitivity for Interest Rate (IR)
- $e_i$: Firm specific events

In this example, the return on a security is the sum of:

1. Its expceted returm
2. The sensitivity to GDP times GDP risk premium
3. The sensitivity to Interest Rate risk times the interest rate risk premium

If the macro factors are expected to be 0 then $R_i=E(R_i)$

#### Arbitrage pricing theory (APT)

- Predicts a SML linking expected returns to risk, but the path is takes to the SML is quite different
- APT relies on three ket propositions
  1. Security returns can be describesd by a factor model
  2. There are sufficient securities to diversify away idiosyncratic risk
  3. Well-functioning security markets do not allow for the persisitence of arbitrage opportunities
- Arbitrage occurs if there is a zero investment portfolio with a sure profit: e.g., shares of a stock sell for different prices on two different exchanges
  - No investment -> investors create large positions to obtain large profits
  - All investors will want an infinite position in the risk-free arbitrage portfolio
  - In efficient markets, profitable arbitrage opportunities will quickly disappear

> APT 也是一种多因子模型，他通过考虑多种风险因子来预测资产的预期回报
>
> APT的基本思想是：在没有套利机会的市场上，资产的预期回报应该与其面临的系统性风险（通过一种或多种风险因子来衡量）成正比。具体来说，APT依赖于以下三个关键前提：
>
> 1. 安全回报可以通过一个因子模型来描述：这意味着资产的回报不仅仅受到市场的影响，还受到一系列其他风险因子的影响。
> 2. 有足够的证券可以分散特定风险：这意味着投资者可以通过投资于大量不同的证券，来降低他们所面临的非系统性风险（即特定风险）。
> 3. 良好运作的证券市场不允许存在持久的套利机会：这意味着如果存在可以不投入任何本金就能获得稳定收益的投资机会，那么投资者将会利用这种机会，直到这种套利机会消失为止。
>
> 这个理论的一个关键特性是，它并不依赖于任何特定的风险因子或者市场均衡模型。因此，APT提供了一个更为灵活和通用的框架，来理解资产的风险和回报之间的关系。

#### Law of one price 一价定律

> "一价定律"（Law of One Price）是一种经济理论，其主要观点是在没有交易成本（如运输费用、关税等）和壁垒（如关税、配额等）的自由市场中，同质商品的价格应当是一样的。这意味着如果两个地点提供相同的商品，那么这两个地点的商品价格应该是相同的。
>
> 一价定律的一个重要前提是市场效率，即市场能够迅速反应信息，并在价格中完全反映出这些信息。如果市场信息不对称或者市场不完全有效，那么一价定律可能不适用。
>
> 例如，假设两个国家，国家A和国家B都生产黄金，但国家A的黄金价格比国家B低。根据一价定律，交易员可以从国家A购买黄金并在国家B销售，从中获得套利利润，直到两国的价格相等为止。这种行为也被称为套利，套利者的行动会推动价格达到一致。
>
> 在金融市场上，一价定律也适用于无风险套利，即如果存在一种策略可以无风险地赚取利润，那么市场参与者将利用这种机会，直到利润机会消失为止。

Bid-Ask Spread is the difference between the bid price and ask price.

- Bid price: 买入价格. This is the **highest price** that the buyer willing to purchase. If you want to sell an item, and the bid price is your final price.
- Ask price: 卖出价格. This is the **lowest price** that the seller willing to sell. If you want to buy an item, and the ask price is your final price.

#### Well-Diversified Portfolios

> “良好分散的投资组合”（Well-Diversified Portfolios）是指投资组合的资产分散到多个不同的投资种类中，包括不同类型的股票、债券、现金等，甚至可能包括房地产、商品等。分散投资是为了降低特定资产的价格波动对投资组合整体表现的影响，从而降低风险。
>
> 举个例子，如果一个投资者所有的资产都投资在一个公司的股票上，那么他的投资风险会非常高，因为一旦这家公司遇到问题，他可能会损失大部分甚至全部的投资。但是，如果他的投资分散到多家公司的股票上，那么即使其中一家公司出现问题，其他公司的股票可能仍然保持稳定或增长，从而降低了他的整体投资风险。
>
> 良好的投资组合分散不仅包括在不同公司的股票之间进行分散，还包括在不同行业、不同地区、不同资产类别（例如股票、债券、现金等）之间进行分散。这样可以进一步降低由于特定行业或地区风险导致的损失。22



## 6 - Equity Valuation

- Fundamental analysts use information concering the current and prospective profitability of a company to assess its fair market value
- Alternative measures of a company’s value
- Dividend discount model (DDM)
- P/E Ratio
- Free cash flow models

> Equity Valuation Model 是用于确定公司股票的公允价值的一种模型。股权估值模型的应用可以帮助投资者决定是否应该购买、持有或出售一个公司的股票。以下是一些常见的股权估值模型：
>
> 1. **股息贴现模型（Dividend Discount Model, DDM）**：该模型将一个公司未来所有的股息现金流贴现到现在的价值，以此来估计股票的价值。股息贴现模型假设股票的价值主要来自于公司支付的股息。
> 2. **自由现金流贴现模型（Discounted Cash Flow Model, DCF）**：DCF模型将公司未来的自由现金流（即公司经营活动产生的现金流，扣除必要的资本支出后剩余的现金流）贴现到现在的价值，以此来估计公司的价值。DCF模型不仅考虑了股息，还考虑了公司的再投资和债务偿还。
> 3. **价格收益比模型（Price/Earnings, P/E）**：这种模型通过将公司的每股收益（EPS）与同行业的其他公司的价格收益比（P/E比）进行比较，以此来估计公司股票的价值。P/E比是投资者愿意为每单位收益支付的金额。
> 4. **净资产价值模型（Net Asset Value, NAV）**：NAV模型用公司的总资产减去其总负债，然后除以公司的股份数，以此来估计公司每股股票的价值。这种模型通常用于估值房地产投资信托（REITs）和其他资产重型公司。

### 6.1 - Valutaions

- Purpose of fundamental analysis is to identify stocks that are mispriced relative to some measure of “true” value that can be derived from observable financial data
- Valuation ratios are commonly used to assess the valuaion of one firm compared to others in the same industry

**Limitations of Book Value**

- Shareholders are sometimes called “residual claimants”
- Book values are based on historical cost, while market values measure the current values of assets and liabilities
- Market values generally will not match historical values

**Liquidation value 清算价值**

- Net amount that could be realized by selling the assets of a firm after paying the debt is liquidation value

**Tobin’s q**

- Tobin’s q is the ratio of market value of the firm to replacement cost

> 清算价值是指，如果一家公司出售其所有资产并偿还所有债务后所剩余的净额。这通常被看作是公司价值的一种保守估计，因为它假设公司会停止运营，并出售其所有资产。清算价值通常被视为股票价格的“底线”（或最低值）。这是因为，如果一家公司的市场价值（即其股票价格乘以其发行的股票数量）低于其清算价值，那么理论上，投资者可以买下公司，然后出售其资产并偿还其债务，以获得利润。
>
> 替代成本（replacement cost）是指，以当前市场价格购买公司所有资产所需要的成本。
>
> 托宾的 q 值（Tobin's q）是一家公司的市场价值和替代成本的比率。这是一个衡量公司价值是否合理的指标。如果 q 值大于 1，那么公司的市场价值超过了其资产的替代成本，可能说明公司的股票被高估。如果 q 值小于 1，那么公司的市场价值低于其资产的替代成本，可能说明公司的股票被低估。

**Intrinsic Value vs. Market Price**

- The return on a stock is composed of cash dividends and capital gains or losses

$$
\text{Expected HPR} = E(r) = \frac {E(D_1)+[E(P_1)-P_0]} {P_0}
$$

- The expected HPR may be more or less than the required rate of return
  - Variation based on the stock’s risk
- The instrinsic value ($V_0$) is the ‘true’ value, according to a model
  - If intrinsic value > market value, the stock is considered undervalue and a good investment

> 股票收益、预期的持有期回报率（Expected Holding Period Return，简称 HPR），以及股票的内在价值（Intrinsic Value）与市场价格的关系。
>
> 1. **股票收益**：股票的收益主要由现金分红和资本利得或损失两部分组成。资本利得或损失是指股票的卖出价格与买入价格之间的差价。
> 2. **预期的持有期回报率**：这是投资者预期在某期间内，持有某项投资能获得的回报率。公式中，$E(D_1)$ 是预期的分红，$E(P_1)$ 是预期的股票卖出价格，$P_0$ 是股票的当前购买价格。预期的 HPR 可能高于或低于所需的回报率，这取决于股票的风险程度。
> 3. **内在价值 vs 市场价值**：内在价值是基于某个模型计算出的股票的“真实”价值。如果内在价值高于市场价值，那么这支股票就被认为被低估了，是一个好的投资机会。反之，如果内在价值低于市场价值，那么股票被认为被高估，投资者应该考虑出售。这是价值投资的基本逻辑。

**Required Return**

- CAPM gives the required return k:
  $$
  k = r_f+\beta[E(r_M)-r_f]
  $$

- If the stock is priced correctly, expected return will equal to the required return

- k is the required rate of return

> “Required return” 是投资者期望从投资中获取的最低回报率。
>
> 在公式中：
>
> - k 是期望的投资回报率，也就是"required return"。
> - rf 是无风险回报率。通常来说，无风险回报率是指国债或其他政府担保的投资的预期回报率。
> - β (Beta) 是投资的系统性风险度量，描述了投资与整个市场的相关性。如果β值为1，说明这项投资的价格波动与市场完全一致；如果β值大于1，说明这项投资的价格波动超过市场；反之，如果β值小于1，则说明这项投资的价格波动小于市场。
> - E(rM) 是市场的预期回报率。
>
> 在理想的市场中，如果股票的价格正确，那么预期的回报率将等于所需的回报率。简单地说，所需的回报率（required return）是投资者为承担一定的风险所期望得到的最低回报率。如果实际的回报率低于所需的回报率，那么投资者可能会选择卖出这个投资。

### 6.2 - Dividend Discount Models (DDM)

$$
V_0 = \frac {D_1} {1+k} + \frac {D_2} {(1+k)^2} + \frac {D_3} {(1+k)^3} + ...
$$

- $V_0$: current value
- $D_t$: dividend at time t
- k: required rate of return
- DDM says $V_0=$ the present value of all expected future dividends into prepetuity

**Constant growth DDM**
$$
V_0 = \frac {D_0(1+G)} {k-g}=\frac {D_1} {k-g}
$$


>股息折现模型（Dividend Discount Model, DDM）是一个用来估计股票公平价值的方法。这种模型的核心思想是，股票的价值等于所有未来股息现值的总和。根据时间价值的原理，未来收益的现值通常比未来收益的面值要小。
>
>基本的股息折现模型公式为：
>
>$P = \frac {D_1} {k-g}$
>
>其中：
>
>- P 是股票的当前价格
>- D1 是下一期预期的股息
>- k 是股东所需的回报率或折现率
>- g 是股息的预期增长率
>
>这个模型的一个关键假设是，股息会以一个恒定的比率无限期地增长。然而在实际应用中，这个假设往往过于简化。因此，股息折现模型有许多变体，比如两阶段股息折现模型，这种模型假设股息的增长率在初期和长期是不同的。
>
>总的来说，股息折现模型是一个基于公司股息政策和股东回报要求来评估股票价值的工具。

![image-20230626183453935](https://images.wu.engineer/images/2023/06/26/image-20230626183453935.png)

- The constant growth rate DDM implies that a stock’s value will be greater:
  1. The larger its expected dividend per share
  2. The lower the market capitalization rate, k
  3. The higher the expected growth rate of dividends
- The stock price is expected to grow at the same rate as dividends

### 6.3 - Discounted Cash Flow (DCF)

$$
E(r) = \text{Dividend yield + Capital gains yield} = \frac {D_1} {P_0}+ \frac {P_1-P_0} {P_0}=\frac {D_1} {P_0} + g
$$



## 7 - Black Litterman



## 8 - Ridge and Lasso Regression (Quick Gothrough)



## 9 - Algorithm Trading



## 10 - Natural Language Processing (Quick Gothrough)



## 11 - Neural Network and Deep Learning (Quick Gothrough)



## 12 - Microstructure and Algorithm Trading







