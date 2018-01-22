# 9-Market-Sectors-Equal-Weight
A simple Quantopian algorithm that keeps you equally invested in the 9 major market sectors and switches to bonds during market downtrends.

# Terminology
SPY - S&P 500 index
SHY - 1-3 Year treasure bonds
TLT - 20 Year treasury bonds

# How it works

## Normal market conditions
This algorithm keeps you equally invested in the 9 market sectors most of the time. The weighting of these 9 sectors are rebalanced 90 minutes after open on the first trading day of each month. 

## Exiting the market
If the algorithm detects a downtrend or recession, it exits the 9 market sectors and enters bonds. The below logic governs whether t

If 100 day SPY regression slope is lower than SHY and TLT 

AND 100 day and 200 day moving average RSI for SPY is NOT > 50

AND either one of below is true
- 100 day and 200 day moving average RSI for SPY is < 50
- Current SPY price is below 1.01 times the 200 day moving average
- 100 day moving average RSI for SPY is below TLT

The algorithm exits your positions, and enters into either TLT or SHY, depending which has a higher 100 day regression slope.
