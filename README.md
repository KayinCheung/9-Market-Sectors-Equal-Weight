## 9 Market Sectors Equal Weight
A simple algorithm that keeps you equally invested in the 9 major market sectors and switches to bonds during market downtrends.

## Backtest results of algo
Backtest period - 1 Jan 2004 to 19 Jan 2018

![algo result](https://user-images.githubusercontent.com/24837709/35205429-1c4fb44a-ff70-11e7-8e9e-06d97a1011b8.png)

Signifcantly reduces drawdown during financial crisis while improving returns.

Outside of monthly rebalances, the algo only liquidated its positions 8 times in 13 years. It's similar to buy and hold but uses simple indicators or downtrends to exit the market automatically and re-enter the market after the recession.



## Terminology
SPY - S&P 500 index

SHY - 1-3 Year treasure bonds

TLT - 20 Year treasury bonds

### 9 Market sectors consist of 

XLY - Consumer Discrectionary SPDR Fund   
XLF -  Financial SPDR Fund  
XLK - Technology SPDR Fund  
XLE - Energy SPDR Fund  
XLV - Health Care SPRD Fund  
XLI - Industrial SPDR Fund  
XLP - Consumer Staples SPDR Fund   
XLB - Materials SPDR Fund  
XLU - Utilities SPRD Fund

All market sectors are rebalanced monthly to 11.11% of portfolio weight.


# How it works

## Normal market conditions
This algorithm keeps you equally invested in the 9 market sectors most of the time. The weighting of these 9 sectors are rebalanced 90 minutes after open on the first trading day of each month. 

## Exiting the market
If the algorithm detects a downtrend or recession, it exits the 9 market sectors and enters bonds. The below logic governs whether 9 sectors or bonds are held

If 100 day SPY regression slope is lower than SHY and TLT 

AND 100 day and 200 day moving average RSI for SPY is NOT > 50

AND either one of below is true
- 100 day and 200 day moving average RSI for SPY is < 50
- Current SPY price is below 1.01 times the 200 day moving average
- 100 day moving average RSI for SPY is below TLT

The algorithm exits your positions, and enters into either TLT or SHY, depending which has a higher 100 day regression slope.


## How to use it
This algorithm can be copy pasted in Quantopian, which allows you to link an algo to your broker account in Interactive Brokers or Robinhood. Alternavitely you can also backtest the algorithm at the beginning of each month and follow its trades to manually enter/exit positions.


### Backtesting parameters

Slippage cost - $0.01/share

Transaction cost - $0.0075/share
