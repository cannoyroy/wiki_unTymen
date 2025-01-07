# Introduce to Alphas

## 1. What is an Alpha?

The aim of Alpha:

- Determine how to distribute **capital** among a group of **financial instruments**.

To ensure downsides protection:

- Develop **equity long-short market neutral alphas**
- Expected to produce substantially better risk-adjusted returns

Taking a "Long Position" in a stock:

- Buying the stock
- If the stock **increase** in value, you will **profit**

Taking a "Short Position" in a stock:

- **Borrowing** a stock (usually from a **broker**), selling it, then hoping it declines in value
- Then, **buy it back at a lower price** and return borrowed shares

Equity Long-short Market Neutral Strategy:

- Used commonly by hedge funds
- Equal dollar amount of **long positions** and **short positions**
- This strategy can work even if **long position declines** in value. Because **profit from shorting** can be higher than **losses from long positions**
- **GOAL**: minimize **exposure to market** in general, and **profit from a change** in the spread between two stocks

### HOW TO

Begin by defining what instruments you want to trade.

The **universe** can be a group of US stocks defined on the basis of their liquidity.

An Alpha is a vector of the predicted value of the stocks in the universe. Each value can change each day and has two properties.

1. Sign: positive sign = long, or buy, negative sign = short, or sell
2. Magnitude: it determines **capital distribution** among stocks in the portfolio

Steps to Alpha Creation:

1. Generate an idea
2. Implement the idea
   - expression
   - python code
3. Apply operations on raw alpha vector
4. Analyze statistics

## 2. Making an Alpha: Simulation Settings

- First, decide the region and the universe you want to trade.

  "universe": choose how many of the most liquid stocks to trade.

- Next, decide the timing of the date you want to use for your alpha——refer to it as Delay.

  - Delay-1 = Yesterday's Prices
  - Delay-0 = Today's Prices

- Set some Decay. 

  Decay provides a weighted sum of the Alpha values for a specified number of days in the past, it helps remove any major fluctuations or outliers in the Alpha values on any given day.

  Decay performs a **linear decay** function over the past n days by combining today's value with previous days' decayed value.

- Using the Neutralization. **Neutralization** is an operation used to make a strategy market/industry/sub-industry neutral.

- Max stock weight. It guards against high exposure on any individual stock. The recommended setting is **between 0.05 and 0.1 (5-10%)**.

- Simulation Duration. Recommend a window of a least five years for your simulation.

- Lookback days. The number of lookback days must be set greater than or equal to the days your alpha looks back in the past.

## 3. Making an Alpha: Simulating an Alpha

- Begin with formulating an idea for Alpha simulation. It can range from simple to complex. 
- Choose the operators and datasets required to implement the idea. 
- Set up appropriate simulation settings for the idea. 
- Enter an Alpha expression, combining data, operators, and constants, for Alpha idea implementation.
- The platform evaluates the input code for each instrument to construct a fictitious portfolio, allocating investments in each stock for a one-day period in proportion to the values of the expression.
- If specified, neutralization calculates the final value, where a negative variable denotes short positions and a positive variable indicates long positions.
- The platform calculates and displays the simulated PnL**（Profit and Loss）** based on daily positions.

Results come in two forms.

First, it provides you an aggregate  performance parameters like **the Sharpe ratio, the returns, the turnover and the drawdown.**

You will also get a detailed analysis of the aggregate performance parameters, including graphical results representing the capital distribution, the coverage, the Sharpe ratio and the PnL generated from different capitalization stocks grouped together or different stocks within industries, all sectors grouped together.

## 4. Alpha expression to PnL Chart

……

## 名词查询

- **Universe（市场）**：在这里，市场指的是投资者可以选择交易的资产类别的集合。这个集合可以包括股票、债券、衍生品等不同类型的金融工具。确定交易市场意味着划定了投资的范围和目标资产类别。

- **Liquid Stocks（流动性强的股票）**：流动性是指资产能够快速且无显著价格影响地买入或卖出的能力。流动性强的股票意味着这些股票在市场上有较高的交易量，买卖订单可以迅速成交，且价格波动较小。

  **Most Liquid（最流动性强的）**：指的是在所有可交易股票中，流动性排名靠前的股票。这些股票因为其高流动性，通常更受交易者和投资者的青睐，因为它们更容易进出市场，减少交易成本和市场冲击。

- **市场敞口（Market Exposure）**：指投资组合的价值受市场整体变动影响的程度。如果一个投资组合与市场指数（如标普500指数）高度相关，那么它就有较高的市场敞口。

- **最小化市场敞口（Minimize Market Exposure）**：这通常涉及到对冲策略，比如使用衍生品（如期货、期权）来抵消市场风险，或者构建一个与市场指数不同步的投资组合，以减少市场下跌时的损失。

- **对冲基金（Hedge Funds）**：这种策略在对冲基金中尤其常见，它们使用复杂的金融工具和策略来减少市场风险，寻求在各种市场条件下都能获得正回报。

- **风险管理（Risk Management）**：最小化市场敞口是风险管理的一部分，目的是保护投资组合免受不利市场条件的影响。

- **市场中性（Market Neutral）**：最小化市场敞口的目标之一是实现市场中性，即投资组合的表现不受市场整体涨跌的影响，而是依赖于选股或市场时机选择等其他因素。

- **Sharpe Ratio（夏普比率）**：夏普比率是一种衡量投资组合绩效的指标，由诺贝尔经济学奖获得者威廉·夏普（William Sharpe）于1966年提出。它通过计算投资组合的预期报酬率与无风险利率之差，再除以投资组合的标准差（风险）来得出。夏普比率的核心思想是在承担相同单位风险的情况下，投资组合能够获得多少超额报酬。如果夏普比率为正值，说明投资组合的收益率超过了无风险利率，并且每承担一单位风险可以获得相应的超额收益；如果夏普比率为负值，则表示投资组合的收益率低于无风险利率，或者投资组合的风险过大。

  [The Sharpe Ratio](https://www.youtube.com/watch?v=fWnyg0UeQkg)

- **Returns（回报）**：在金融领域，回报通常指的是投资所产生的收益，可以是资本增值也可以是投资收益，如股息或利息。它衡量的是投资在一定时期内的盈利表现。

- **Turnover（换手率）**：换手率在金融领域有两个基本含义，一是指企业在特定时间内的销售额或收入总额，用来评估企业的盈利能力和财务状况；二是指股票的交易量，即在一定时间内市场中股票转手买卖的频率，反映了市场的流动性。

- **Drawdown（最大回撤）**：最大回撤是指投资组合从历史最高点下跌到最低点的最大程度，用来衡量投资风险，特别是资金的潜在损失风险。它是评估投资表现的一个重要指标，因为它显示了在最坏情况下可能遭受的损失。

- **Capitalization Stocks（市值股票）**：指的是根据公司市值大小分类的股票，如小市值、中市值和大市值股票。不同市值的股票可能有不同的风险和回报特征。

- 

  
